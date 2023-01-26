# Linux Pthread
```
#include <pthread.h>
void *routine(void *arg)
{
    /* Do something */
}

void main()
{
    pthread_t t;
    int res = pthread_create(&t, NULL, routine, NULL/*arg*/);
    if (res < 0) {
        fprintf(stderr, "pthread_create fail!\n");
    }

    int stat;
    pthread_join(t, (void **)&stat );
    fprintf(stderr, "Thread join with status %d\n, stat);
}
```