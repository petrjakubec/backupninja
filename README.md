first, you need to install and configure mariadb
```
# yum install -y mariadb-server || apt-get install -y mariadb-server
# service mariadb start ||  sudo service mysqld start
# mysql_secure_installation #just hit enter because by default there is no password - I've set password: password

```

after that you can log into db by password
```
# mysql -u root -p
```


# backupninja

configuration of backupninja can be easily done through tool **ninjahelper**

20.mysql is a example of configuretion which will create uncompressed sqldump from all databases (if you have more dbs, it would be better specify separate job for each one by using ninjahelper).

/etc/backup.d/20.mysql

you can run the job instantly:
```
# backupninja --now --debug
```


logs can be found in:
```/var/log/backupninja.log``` 

sqldump will be created in 
```/var/backups/mysql```

# backupninja setup 
is in the /etc/backup.d/20-files.dup
