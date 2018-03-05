# How to install PostgresSQL in ubuntu

### Installation
```
$    sudo apt-get update
$    sudo apt-get install postgresql postgresql-contrib
```
It will install postgres and -contrib package which has some additional utilities

### Switch to postgres user 
```
$ sudo -i -u postgres
```

### Access PostgresSQL prompt
```
$ psql
```

### Access PostgresSQL prompt without switching user
```
$ psql -u posgres
```

### Exit from PostgresSQL prompt
```
\q
```

### Reference 
* [Postgres installation - digital occean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04)
