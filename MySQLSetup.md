# How to install mysql on ubuntu

### Install mysql
```
$ sudo apt-get update
$ sudo apt-get install mysql-server
```

### Configuring mysql
```
$ mysql_secure_installation
```

### Testing mysql
```
$ systemctl status mysql.service
```

### Connect to mysql
* -p : prompt for the password
* -u : represents user
```
$ mysqladmin -p -u root version
```
