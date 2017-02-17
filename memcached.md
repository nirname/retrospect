# Memcached

## Installation

```bash
sudo apt-get install libevent-dev
```

### Ubuntu

```bash
sudo apt-get install memcached
/etc/init.d/memcached status
```

### From source

```bash
wget http://memcached.org/latest
tar -zxvf latest
cd memcached-1.x.x
./configure && make && make test && sudo make install
```