# Unix domain socket
+ https://www.toptip.ca/2013/02/overflow-in-datagram-type-sockets.html
```
cat /proc/sys/net/unix/max_dgram_qlen
sysctl -w net.unix.max_dgram_qlen=128   
```

# SystemV Message Queue
+ https://manpages.ubuntu.com/manpages/trusty/man2/msgrcv.2.html
cat /proc/sys/kernel/msgmnb
sysctl -w kernel.msgmnb=131072 
