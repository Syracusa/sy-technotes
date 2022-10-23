# HOWTO : Make embedded device driver develop environment
 - This post explain how to make embedded device driver develop environment.
 - I'll show you how to make basic device driver of Beaglebone black.
## Table of contents
1. Get kernel for your device.
 - First, you should get kernel that used in your device. 
 ```
 git clone https://github.com/beagleboard/linux
 cd linux
 git checkout 4.19.94-ti-r42 # Checkout to your device's kernel version
 ```

2. Install cross-compiler. 
 - Embedded device like beaglebone black, is mostly not use same architecture of your PC. The binary is required to compiled by their architecture specific compiler.
```
sudo apt-get update
sudo apt-get install gcc-arm-linux-gnueabihf
```
 - After install compiler, make sure that you can execute that compiler.
```
 arm-linux-gnueabi-gcc --version
```

3. Write driver code.
 - Very simple device driver code that do nothing.
```
/* __your_driver_name.c */
#include <linux/init.h>
#include <linux/module.h>

MODULE_LICENSE("GPL");

static void __your_driver_name_exit(void)
{
    printk(KERN_NOTICE "Driver exit.\n");
}

static int __your_driver_name_init(void)
{
    printk(KERN_NOTICE "Driver init.\n");
    return 0;
}

module_init(__your_driver_name_init);
module_exit(__your_driver_name_exit);
```
4. Write makefile.
 - Makefile
```

KERNELDIR ?= {Your directory to kernel}
PWD := $(shell pwd)

default:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) modules

clean:
	rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c *.mod \
		.tmp_versions modules.order Module.symvers .cache.mk \
		dio *.tmp *.log

endif
```
 - Now we can build the driver.
 - Note that you should not just type make. You should tell them which cross-compiler to use.
```
 - make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi-
```
 - If everything works fine, then __your_driver_name.ko file will be generated at your working directory.

5. Test driver.
 - Move your ko file to device.
 - In this post, I will use scp to move file as my deivce is connected with LAN.
 ```
 - scp __your_driver_name.ko root@192.168.1.105:~/
 ```

 - See if your driver can be insmod/rmmod.
 ```
 - insmod __your_driver_name.ko
 - rmmod __your_driver_name
 - dmesg
 ```