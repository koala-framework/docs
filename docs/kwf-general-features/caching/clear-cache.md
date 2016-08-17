#CLEAR CACHE

There are several types of cache:

1. OptCode
2. Apc
3. ViewCache
4. ...plus others

#####To delete the optcode cache write:
`php bootstrap.php clear-cache --type=optcode`

#####Apc cache is cleared with:
`php bootstrap.php clear-cache --type=apc`

#####Kwc view cache can be deleted with params:
`php bootstrap.php clear-view-cache`

1. `--all`
* deletes the view-cache of every component
2. `--id=`
* deletes the view-cache of the specified component-id
3. `--dbId=`
* this is used to delete by defined dbId
4. `--expandedId=`
* This is searching for a concrete component at a defined location. The expanded id is build up with parent-ids + component-id (eg. root-main_first-page-textImage
5. `--class=`
* Thisway you can define a class to delete the caches from


##Which cache to delete

Sometimes it's harmful to delete all caches on production server as it would cause a downtime of the website.
You can delete only required cache types by using the `--type` parameter for the clear-cache call.

Changes only on uncached code: `--type=optcode`

(<3.8): Changes only on assets (like css or js): `--type=assets`

Changes in config.ini: `--type=config,apc`

(<3.8): Changes on trl: `--type=trl,apc` (don't forget corresponding view-cache)

Changes in config on server.domain value: `--type=config, setup, apc`