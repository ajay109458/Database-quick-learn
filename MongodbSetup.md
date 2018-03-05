### How to install MongoDB in ubuntu

### Import key 
Import key for official MongoDB repository so that ubuntu can validate authencity of software by verifying GPG key. 
```
$  sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
```

### Update package list in repository
```
$ sudo apt-get update
```

### Install MongoDB
```
$  sudo apt-get install -y mongodb-org
```

### Start MongoDB
```
$  sudo systemctl start mongod
```

### Check status of mongodb if service has started
```
$  sudo systemctl status mongod
```

### Enable MongoDb as soon as system starts
```
$ sudo systemctl status mongod
```

Reference
[MongoDB installation - Digital occean](https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-16-04)
