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


--------

```
socket() -> int fd
char* ip -> inet_pton() -> struct in_addr_t
int port -> htons() -> in_port_t

in_addr_t -> sockaddr_in
in_port_t -> sockaddr_in

struct sockaddr_in -> sendto()
int fd -> sendto()
```

***
API Detail
--------
***
### sys/socket.h
***
#### struct sockaddr_in
 + in_port_t sin_port; 
Port number in network byte order
 + struct in_addr sin_addr;

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