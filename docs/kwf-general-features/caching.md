#CACHING

To have optimal performance Koala Framework has a few caches.

When changing something that gets cached the relevant cache needs to be cleared. 
For example when changing a config file, a JavaScript file or a template.

To clear the complete cache execute:

`php bootstrap.php clear-cache`

As this is inconvenient during development there is also a script that watches all files that get cached 
and clear that relevant cache automatically. To start that execute:

`php bootstrap.php clear-cache-watcher`

(only works on linux with inotify, inotifywait application is required, also [memcache](caching/memcache.md) is required)

