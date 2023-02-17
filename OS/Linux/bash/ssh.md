# SSH Connection 
## Troubleshooting

### Check network connection
```
ping {IP}
```
### Check if ssh service working
```
sudo service ssh status
```

### Check ssh port
```
cat /etc/ssh/sshd_config
sudo lsof -i:22
```
### Try self-connecting
```
ssh localhost
```
### Check log
```
cat /var/log/auth.log
```
## Start sshd on startup
```
systemctl start sshd
```
## Login without password
### Create Public Key(Client side)
TBD
### Register public key(Server side)
```
nano ~/.ssh/authorized_keys
sudo service ssh restart
```
