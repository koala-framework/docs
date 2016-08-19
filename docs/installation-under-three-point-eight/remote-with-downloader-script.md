#INSTALL ON REMOTE WEBSERVER USING DOWNLOADER SCRIPT

If your webserver doesn't allow using git you can use our downloader script.

###Requirements:

* Php
* Apache (configured with virtual host pointing to empty document root)
* MySQL Server (running)

####To download the application plus koala framework you can use our kwf-downloader script:

[https://raw.github.com/vivid-planet/kwf-downloader/master/downloader.php](https://raw.githubusercontent.com/vivid-planet/kwf-downloader/master/downloader.php)

Upload this file into the document root and open in the browser.

The script will download and extract the required files. If the webserver can't connect to github to download the files you can manually upload them using eg. ftp (the kwf-downloader script tells you what to do)

After downloading kwf-downloader automatically starts setup.


##Update

To update the application it has to be re-downloaded, open the following url in browser to start that:

http://www.example.com/kwf/maintenance/update-downloader

After downloading updates will be executed automatically.