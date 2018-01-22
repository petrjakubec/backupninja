# Install mariadb
First, you need to install and configure mariadb
```
# yum install -y mariadb-server || apt-get install -y mariadb-server
# service mariadb start ||  sudo service mysqld start
# mysql_secure_installation #just hit enter because by default there is no password - I've set password: password

```

after that you can log into db by password
```
# mysql -u root -p
> exit
```


# backupninja

Manual configuration of backupninja can be easily done through tool **ninjahelper**.

File /etc/backup.d/20.mysql is a example of configuration which will create uncompressed sqldump from all databases (if you have more dbs, it'd be better specify separate job for each one by using ninjahelper).

/etc/backup.d/20.mysql

For test reasons you can run the job instantly:
```
# backupninja --now --debug
```


logs can be found in:
```/var/log/backupninja.log``` 

sqldump of local db will be created in 
```/var/backups/mysql```

# backupninja setup 
Config is in the /etc/backup.d/20-files.dup

# RUN the Backup
Final command for backup using combination of duplicity & backupninja via FTP should be:
```
duplicity /etc ftp://backup@ftp.gpx.cz/var
or 
duplicity /etc ftp://backup:changeme@ftp.gpx.cz/var
```
