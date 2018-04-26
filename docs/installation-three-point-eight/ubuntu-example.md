#EXAMPLE SERVER CONFIGURATION

for Ubuntu/Debian

replace kwf-cms-demo with name of your app.

If you need help contact us on our [mailing list](http://www.koala-framework.org/community/mailing_list).

###1. Install required packages

        sudo apt-get install php5-cli apache2 libapache2-mod-php5 \
            mysql-server php5-mysql php5-tidy php-apc php5-imagick \
            git-core php5-json memcached php5-memcache
     
        #Additional packages if you plan to build on this server:
        sudo apt-get install nodejs nodejs-legacy npm

###2. Configure PHP (if php <= 5.5)

/etc/php5/conf.d/apc.ini:

    extension=apc.so
    [apc]
    apc.shm_size = 128M
    apc.enable_cli = on
    apc.cache_by_default = on
    apc.user_ttl = 60
    apc.slam_defense = 0
    apc.write_lock = 1
 
/etc/php5/apache2/php.ini

Search for short_open_tag and set it to

    short_open_tag = On
    
    
    
###3. Create local test domain

add kwf-cms-demo.local to /etc/hosts, example:

    127.0.0.1 localhost kwf-cms-demo.local

###4. Configure Apache: Create Virtual Host

create /etc/apache2/sites-available/kwf-cms-demo.conf with following contents:

    <VirtualHost *:80>
            ServerName kwf-cms-demo.local
            DocumentRoot /var/www/kwf-cms-demo
            <Directory /var/www/kwf-cms-demo/>
                    Options FollowSymLinks
                    AllowOverride All
                    Order allow,deny
                    allow from all
            </Directory>
            ErrorLog ${APACHE_LOG_DIR}/error.log
            LogLevel warn
            CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>

###5. Configure Apache: enable required module and new site

    sudo a2enmod rewrite
    sudo a2ensite kwf-cms-demo

###6. Reload Apache (to enable the new site)

    sudo /etc/init.d/apache2 reload

###7. Install App and Koala

You are now ready to install Koala Framework with your preferred method.
