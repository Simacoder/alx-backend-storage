# 0x02. Redis basic

# Resources
Read or watch:

- [Redis commands](https://intranet.alxswe.com/rltoken/lQ8ANhVfxDTxDr2UDSyQRA)
- [Redis python client](https://intranet.alxswe.com/rltoken/imfgFhAZPlg7YMZ_tHvFZw)
- [How to Use Redis With Python](https://intranet.alxswe.com/rltoken/7SluvFvgckwVgsvrfOf1CQ)
- [Redis Crash Course Tutorial](https://intranet.alxswe.com/rltoken/hJVo3XwMMFFoApyX8zPXvA)

# Learning Objectives
- Learn how to use redis for basic operations
- Learn how to use redis as a simple cache

# Install Redis on Ubuntu 18.04
$ sudo apt-get -y install redis-server
$ pip3 install redis
$ sed -i "s/bind .*/bind 127.0.0.1/g" /etc/redis/redis.conf
# Use Redis in a container
Redis server is stopped by default - when you are starting a container, you should start it with: service redis-server start

# Tasks
# 0. Writing strings to Redis
- Create a Cache class. In the __init__ method, store an instance of the Redis client as a private variable named _redis (using redis.Redis()) and flush the instance using flushdb.
# 1. Reading from Redis and recovering original type
- Redis only allows to store string, bytes and numbers (and lists thereof). Whatever you store as single elements, it will be returned as a byte string. Hence if you store "a" as a UTF-8 string, it will be returned as b"a" when retrieved from the server.
# 2. Incrementing values
- Familiarize yourself with the INCR command and its python equivalent.

- In this task, we will implement a system to count how many times methods of the Cache class are called.

- Above Cache define a count_calls decorator that takes a single method Callable argument and returns a Callable.

- As a key, use the qualified name of method using the __qualname__ dunder method.

- Create and return function that increments the count for that key every time the method is called and returns the value returned by the original method.

- Remember that the first argument of the wrapped function will be self which is the instance itself, which lets you access the Redis instance.

# 3. Storing lists
- Familiarize yourself with redis commands RPUSH, LPUSH, LRANGE, etc.

- In this task, we will define a call_history decorator to store the history of inputs and outputs for a particular function.

- Everytime the original function will be called, we will add its input parameters to one list in redis, and store its output into another list.
# 4. Retrieving lists
- In this tasks, we will implement a replay function to display the history of calls of a particular function.

- Use keys generated in previous tasks to generate the following output:

# AUTHOR
- [Simanga Mchunu](https://twitter.com/Simacoder)
