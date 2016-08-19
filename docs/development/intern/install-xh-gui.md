#XHGUI

XHGui is a Php profiler.

###Installation

    cd ~/www
    git clone git@github.com:perftools/xhgui.git
    cd xhgui
     
    wget https://gist.githubusercontent.com/nsams/e6cb18e4628df2143da5/raw/b5af654939c0c95b33c9412cc0b973da7d13c246/gistfile1.txt
    git apply gistfile1.txt
    rm gistfile1.txt
     
    composer install --ignore-platform-reqs
     
    connect to webserver and:
    $ mongo
    > use xhprof
    > db.results.ensureIndex( { 'meta.SERVER.REQUEST_TIME' : -1 } )
    > db.results.ensureIndex( { 'profile.main().wt' : -1 } )
    > db.results.ensureIndex( { 'profile.main().mu' : -1 } )
    > db.results.ensureIndex( { 'profile.main().cpu' : -1 } )
    > db.results.ensureIndex( { 'meta.url' : 1 } )
    
    
    
###usage:

1. add the following into bootstrap.php(top):

    `require '../xhgui/external/header.php';`

2. http://xhgui.xxx.vivid/