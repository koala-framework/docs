#CHERRY PICK KWF CHANGE

    git checkout master
    composer update
    git add composer*; git commit -m "composer update"; git push
    git checkout production
     
    ../library/kwfscripts/vivid/vendor-cherry-pick.php koala-framework/koala-framework $COMMITID
     
    or for an repository, for example dealersearch:
    ../library/kwfscripts/vivid/vendor-cherry-pick.php vivid-planet/kwc-dealer-search $COMMITID
