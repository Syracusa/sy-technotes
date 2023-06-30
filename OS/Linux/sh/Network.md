# Tcpdump cheatsheet
+ UDP
  + sudo tcpdump -i eth0 src 192.168.4.40


# Set static ip(Ubuntu)
+ ref : https://www.tecmint.com/set-add-static-ip-address-in-linux/
```
vi /etc/network/interfaces
```

```
auto eth0
iface eth0 inet static 
  address 192.168.0.100
  netmask 255.255.255.0
  gateway 192.168.0.1
  dns-nameservers 4.4.4.4
  dns-nameservers 8.8.8.8
```


# Close program that hold some network port
+ Prerequisite =>  $ sudo apt install net-tools
```

sudo netstat -ap | grep :8764

> tcp        3      0 0.0.0.0:8764            0.0.0.0:*
> LISTEN      198637/python3

sudo pkill -9 python3
```

# Check Firewall