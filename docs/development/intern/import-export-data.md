#IMPORT / EXPORT DATA (DATABASE + UPLOADS)

##Copy Data from production to test server

`vps copy-to-test`

###On Poi Server:

connect to test server

`../library/kwfscripts/copy-data-from.php`

##Import Data from production to local

`vps import (imp)`

###from other source:

`vps import --server=test (imp --server=test)`

###Or:

`vps import --server=niko (imp --server=niko)`

##Copy data from local to online

**(please, don't!)**

###local:

`../library/kwfscripts/copy-data-to-git.php --skip-encrypt`

###online:

`../library/kwfscripts/copy-data-from-git.php --skip-encrypt`

##Config settings:

    server.import.where.foo = "year=(SELECT max(YEAR) FROM bar)" ; ignore only items matching this WHERE
    server.import.keepTables[] = foo ; don't touch this table
    server.import.ignoreTables[] = foo ; import only structure of this table