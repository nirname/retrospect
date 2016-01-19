# Memcached

## Installation

    sudo apt-get install libevent-dev

### Ubuntu

    sudo apt-get install memcached
    /etc/init.d/memcached status

### From source

    wget http://memcached.org/latest
    tar -zxvf latest
    cd memcached-1.x.x
    ./configure && make && make test && sudo make install
