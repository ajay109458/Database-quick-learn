# Redis Setup on Ubuntu

## Download and extract source code

#### Update the package repo
`$  sudo apt-get update`

#### Install dependencies
`$ sudo apt-get install build-essential tcl`

#### Download source to temp directory
```
$ cd /tmp
$ curl -O http://download.redis.io/redis-stable.tar.gz
```

#### Unpack tarball 
```
$ tar xzvf redis-stable.tar.gz
```

#### Move into redis source directory
```
$ cd redis-stable
```

## Build and install Redis

#### Compile Redis binaries
```
$ make
```

#### Run test suite to make sure every thing is built fine
```
$ make test
```

#### Install binaries to system 
```
$ sudo make install
```

[Install Redis](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-redis-on-ubuntu-16-04)



