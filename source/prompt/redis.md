# Redis

**Installation**

    wget http://download.redis.io/redis-stable.tar.gz
    tar xvzf redis-stable.tar.gz
    cd redis-stable
    make
    make install

**Start**

* `redis-server` is the Redis Server itself.
* `redis-sentinel` is the Redis Sentinel executable (monitoring and failover).
* `redis-cli` is the command line interface utility to talk with Redis.
* `redis-benchmark` is used to check Redis performances.
* `redis-check-aof` and redis-check-dump are useful in the rare event of corrupted data files.
