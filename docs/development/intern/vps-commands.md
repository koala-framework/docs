#VPS COMMANDS

####`vps` (or `kwf`) is an alias for `php bootstrap.php`

* `vps clear-cache-watcher (ccw)` (watch for file changes and rebuild relevant caches)
* `vps clear-cache (cc)` (clear all caches)
* `vps update` (executes all update scripts, call after code update or adding a new component)
* [`vps import --server=production (imp)`](import-export-data.md)
* [`vps export --server=test (ext)`](push-changes-to-production.md)
* [`vps export --server=production (exp)`](push-changes-to-production.md)
* [`vps go-online`](push-changes-to-production.md)


###[Solr](../../kwc-cms/fulltext-search/solr-backend.md)

* `vps fulltext start-solr`

* `vps fulltext rebuild --debug`