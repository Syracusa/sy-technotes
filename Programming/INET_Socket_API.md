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
# sys/socket.h
## socket()
 + int socket(int domain, int type, int protocol)
 + domain : AF_INET
 + type : SOCK_DGRAM(for udp), SOCK_STREAM(for tcp), SOCK_RAW(for monitoring traffic)
 + protocol : 0 will automatically select protocol for you(You can use explicit value like IPPROTO_UDP or IPPROTO_TCP or IPPROTO_ICMP or something )
## bind()
 + 


## setsockopt()
 + int setsockopt()