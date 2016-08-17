#MEMCACHE

Koala Framework can make use of a running memcache deamon. If configured it will be used automatically for all caches 
that can be cleared while the application is running.
Main advantage over apc user cache (which is used instead by default) is that deleting cache entries in memcache doesn't 
cause fragmentation as it does in apc. Another advantage is that we can use a single memcache instance from multiple 
webservers - when load balancing.

To enable memcache configure it in config:

    server.memcache.host = localhost
    
    
##Requirements

* Running memcache daemon
* php memcache extension