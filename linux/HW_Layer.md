# Role of device driver

```
---------------------------------
|     Application(User area)    |
---------------------------------
               |
           System Call
               |
---------------------------------
|   Device Driver(Kernel area)  |
---------------------------------
        |               |
 MEMORY MAPPED IO   INTERRUPT
        |               |
---------------------------------
|            FPGA(HW)           |
---------------------------------

```