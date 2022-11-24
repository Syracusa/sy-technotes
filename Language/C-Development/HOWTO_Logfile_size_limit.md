# Resize logfile with remove old logs

```
#include <sys/mman.h>
#include <unistd.h>
#include <sys/types.h>

#define MAX_LOGFILE_SIZE_KB

/* File* fp : Readable & Writable file pointer. */
void resize_logfile(File* fp)
{
    fseek(fp, 0, SEEK_END);
    long fsize = ftell(fp);

    if (fsize > MAX_LOGFILE_SIZE_KB * 1024) {
        long half = fsize / 2;
        uint8_t *fmap = mmap(NULL, fsize,
                                PROT_READ | PROT_WRITE,
                                MAP_SHARED, fp->_fileno, 0);

        if (fmap != MAP_FAILED){
            fprintf(stderr, "%p %ld\n", fmap, half);
            memcpy(fmap, &fmap[fsize - half], half);
            munmap(fmap, fsize);
            ftruncate(fp->_fileno, half);
            fseek(fp, 0, SEEK_END);
            fprintf(stderr "Resize log file... %ld -> %ld\n", fsize, half);
        } else {
            fprintf(stderr, "Map fail : %s\n", strerror(errno));
        }

    }
}
```