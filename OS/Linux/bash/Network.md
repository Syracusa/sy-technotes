# Close program that hold some network port
```
sudo netstat -ap | grep :8764

> tcp        3      0 0.0.0.0:8764            0.0.0.0:*
> LISTEN      198637/python3

sudo pkill -9 python3
```