#CREATE NEW WEB

    cd ~/www/template
    gpr
    php ../library/kwfscripts/vivid/create-from-template.php --name="Pretty Web Name" #optional: --id="webid"
    cd ../webid
    
    
##Changes for POI Web

###**boostrap.php**

1. include SetupPoi.php
2. SetupPoi::setUp();

###**app/Acl.php**

* extend Vkwf_Acl_Component_IsiWebPoi


###**config.ini**

1. delete webcode (if content-web, but discuss if this is really a good idea)
2. delete library
3. change uploads-path


    [production]
    server.user = www
    server.host = cms-web.szg.porsche.co.at
    server.dir = /www/docs/div/example.com
    server.domain = www.example.com
    server.previewDomain = preview.example.com
     
    [test : production]
    server.host = marwebap01t.szg.porsche.co.at
    server.domain = test.example.com
     
    [qa : test]
    server.domain = qa.example.com
    server.host = anja1.szg.porsche.co.at
    vkwfConfigSection = test
    
    
##Create empty repository

    cd ~/www
    php library/kwfscripts/vivid/create-empty-repository.php --name="Pretty Web Name"
    cd ../webid
    