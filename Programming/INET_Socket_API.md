# INET Socket API

# UDP
## Server Side
 + socket() -> bind() -> recvfrom()/sendto()
## Client Side
 + socket() -> recvfrom()/sendto()

# TCP 
## Server Side
 + socket() -> bind() -> listen() -> accept() -> read()/write()
## Client Side
 + socket() -> connect() -> read()/write()

# API
## sys/socket.h

### socket()
#### Definition
 + int socket(int domain, int type, int protocol)
#### Parameter
##### int domain
 - AF_INET
##### int type
 - SOCK_DGRAM(for udp)
 - SOCK_STREAM(for tcp)
 - SOCK_RAW(for monitoring traffic)
##### int protocol
 + 0 (will automatically select protocol for you)
 + IPPROTO_UDP
 + IPPROTO_TCP
 + IPPROTO_ICMP
##### Return : int
 + Socket file descriptor 
 + -1 if failed

### bind()
 + 


### setsockopt()
 + int setsockopt()