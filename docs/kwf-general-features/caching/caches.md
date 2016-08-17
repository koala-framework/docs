#CACHES

Koala Framework uses a bunch of different caches

##Optcode Cache

It is highly recommended to use a optcode cache (aka Php accelerator) to generally improve performance of php scripts.

####Examples:

* apc (up to Php 5.5)
* Zend OPcache (default in php core from 5.5)


##Kwf_Cache_Simple

This cache is used in Koala Framework as a simple to use cache.

The used backend is automatically found in the following preference:

* memcache (if server.memcache.host is set)
* apc (or apcu) (if php extension is installed)
* file (cache/simple) (fallback, very slow)

####Usage Example

    $cacheId = 'unique-prefix-123';
    $data = Kwf_Cache_Simple::fetch($cacheId);
    if ($data === false) {
       $data = someExpensiveMethod();
        Kwf_Cache_Simple::add($cacheId, $data);
    }
     
     
    //delete cache in eg. Events:
    Kwf_Cache_Simple::delete($cacheId);
    
##Kwf_Cache_SimpleStatic

Similar as `Kwf_Cache_Simple` but for cache values that don't change during runtime of application 
(only when updating the code).

The used backend is automatically found in the following preference:

* apc (or apcu)
* file (cache/simple) (very slow)

####Usage Example

    $cacheId = 'unique-prefix-123';
    $data = Kwf_Cache_SimpleStatic::fetch($cacheId);
    if ($data === false) {
       $data = someExpensiveMethod();
        Kwf_Cache_SimpleStatic::add($cacheId, $data);
    }
    
    
##Kwf_Component_Cache_Memory

Used when rendering components. This cache is not cleared when calling clear-cache.

The used backend is automatically found in the following preference:

* memcache
* apc (or apcu)
* file (cache/view)


##Kwf_Assets_Cache

Two level cache with Kwf_Cache_SimpleStatic plus file (cache/assets)

##Kwf_Media_MemoryCache

Two level cache with `Kwf_Cache_Simple` plus file (cache/mediameta)