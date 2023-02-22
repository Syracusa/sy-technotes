# TFTP
+ ref : https://linuxhint.com/install_tftp_server_ubuntu/
## Install tftp Server
```
sudo apt update
sudo apt install tftpd-hpa

sudo systemctl status tftpd-hpa
```
## Configure TFTP Server
+ Open config file
```
sudo nano /etc/default/tftpd-hpa
```

+ Modify config
```
# /etc/default/tftpd-hpa

TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/home/kjkim/tftpdir"
TFTP_ADDRESS=":69"
TFTP_OPTIONS="--secure"
```

+ Restart service
```
sudo systemctl restart tftpd-hpa
sudo systemctl status tftpd-hpa
```