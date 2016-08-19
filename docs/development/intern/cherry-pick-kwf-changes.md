#CHERRY PICK KWF CHANGE

    cd web
    composer update on master branch
    git checkout production
    composer install
     
    ../library/kwfscripts/vivid/vendor-cherry-pick.php koala-framework/koala-framework $COMMITID
     
    or for an repository, for example dealersearch:
    ../library/kwfscripts/vivid/vendor-cherry-pick.php vivid-planet/kwc-dealer-search $COMMITID
 