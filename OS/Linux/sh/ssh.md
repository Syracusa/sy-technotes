# SSH Connection 
## Troubleshooting
### Check network connection
```sh
ping {IP}
```

### Check if ssh service working
```sh
sudo service ssh status
```

### Check ssh port
```sh
cat /etc/ssh/sshd_config
sudo lsof -i:22
```

### Try self-connecting
```sh
ssh localhost
```

### Check log
```sh
cat /var/log/auth.log
```

## Start sshd on startup
```sh
systemctl start sshd
```

## Login without password
### Create Keypair(Client side)
```sh
ssh-keygen 
```

### Register public key(Server side)
```sh
nano ~/.ssh/authorized_keys
sudo service ssh restart
```
