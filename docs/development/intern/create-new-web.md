#CREATE NEW WEB

    cd ~/www/template
    gpr
    php ../library/kwfscripts/vivid/create-from-template.php --name="Pretty Web Name" #optional: --id="webid"
    cd ../webid

**Make sure to set a unique [preLogin](../../kwf-general-features/config/prelogin.md) in every new project.**


## Changes for POI Web

### Require the correct setup in `bootstrap.php`

1. Require `SetupPoi.php` intead of `Setup.php`
2. Call `Vkwf_SetupPoi::setUp();` instead of `Vkwf_Setup::setUp();`

### Extend from the correct Acl in `app/Acl.php`
```php
<?php
class Acl extends Vkwf_Acl_Component_IsiWebPoi
{
    // ...
}
```


### Update the server-settings in `config.ini`

```ini
[production]
libraryPath = /www/docs/div/library
server.user = www
server.host = macac2c02p.szg.porsche.co.at
server.dir = /www/docs/div/example.com
server.domain = www.example.com
server.https = true

[test : production]
server.host = macac2c01t.szg.porsche.co.at
server.domain = test.example.com

[vivid : production]
server.https = false
```
    
    
# Create empty repository

    cd ~/www
    php library/kwfscripts/vivid/create-empty-repository.php --name="Pretty Web Name"
    cd ../webid
