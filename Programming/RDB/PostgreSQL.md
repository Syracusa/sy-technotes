# Troubleshooting
## Connection error
+ Problem
```
createdb: error: connection to server on socket "/var/run/postgresql/.s.PGSQL.5432" failed: No such file or directory
        Is the server running locally and accepting connections on that socket?
```
+ Solution
```
user$ pg_lsclusters
Ver Cluster Port Status Owner    Data directory              Log file
15  main    5432 down   postgres /var/lib/postgresql/15/main /var/log/postgresql/postgresql-15-main.log
user$ sudo pg_ctlcluster 15 main start
user$ sudo service postgresql restart

```

+ ref : https://stackoverflow.com/questions/31645550/postgresql-why-psql-cant-connect-to-server


## No role
```
createdb: error: connection to server on socket "/tmp/.s.PGSQL.5432" failed: FATAL:  role "joe" does not exist
```
```
user$ sudo -u postgres createuser joe
```

##  
```
sudo su - postgres
```