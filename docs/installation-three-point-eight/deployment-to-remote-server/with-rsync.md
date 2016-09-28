#DEPLOYMENT USING RSYNC

If your production server is accessible using ssh and you can use rsync you can use kwf-deploy scripts to deploy your app.

More coming soon.

    composer require koala-framework/kwf-deploy

.



    [production]
    server.host = mywebhost.com
    server.dir = /var/www/example.com
    server.user = myuser ; ssh user
    server.port = 123  ; ssh port, if not default 22

.



    ./vendor/bin/deploy rsync