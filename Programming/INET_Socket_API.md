INET Socket API
========
***

UDP API call flow
--------
+ Server Side
 socket() -> bind() -> recvfrom() / sendto()
+ Client Side
 socket() -> recvfrom() / sendto()

TCP API call flow
-------- 
+ Server Side
 socket() -> bind() -> listen() -> accept() -> read()/write()
+ Client Side
 socket() -> connect() -> read()/write()
***
API Detail
--------
***
### sys/socket.h
***
#### socket()
  int socket(int domain, int type, int protocol)
##### Parameter
1. int domain
 + AF_INET
2. int type
 + SOCK_DGRAM(for udp)  
 + SOCK_STREAM(for tcp)  
 + SOCK_RAW(for monitoring traffic)  
3. int protocol
 + 0 (will automatically select protocol for you)
 + IPPROTO_UDP
 + IPPROTO_TCP
 + IPPROTO_ICMP
##### Return 
 + Socket file descriptor 
 + -1 if failed

#### bind()
 + 

#### sendto()
 + ssize_t sendto(int fd, void \*buf, size_t n, int flags, const sockaddr\* addr, socklen_t addr_len)
##### Parameter
1. int fd
2. void \*buf
3. size_t n
4. int flags
5. const sockaddr \*addr
6. socklen_t addr_len

#### setsockopt()
 + int setsockopt()
##### Parameter

##### Return

***
### arpa/inet.h
***