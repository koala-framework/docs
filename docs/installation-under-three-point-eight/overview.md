#INSTALLATION (< 3.8)

There are multiple ways how to install koala framework, depending on your server infrastructure.

If you need help contact us on our [mailing list](http://www.koala-framework.org/community/mailing_list).

This instructions are only valid for Koala Framework Version up to 3.7.

##Development on local machine

Developing a koala website/application should not be done on production servers for obvious reasons. Instead you should run a local copy of the application where you develop. Recommended method for getting the changes deployed is using git - to either a public github repository or your own git server.

For local development you can either:

* [use php built-in webserver](local-php-builtin-webserver.md) (easy to set up, not best performance)
* [use apache webserver](local-apache.md) (difficult to set up, good performance)
* [use our virtual machine](virtual-machine.md) (recommended for windows)

as for development the webserver performance isn't critical we recommend the first method.

##Installation on remote Webserver

Which installation method you choose for the remote webserver depends on what you can do on the server.

In any case you need an apache configured with an document root, see [ubuntu example configuration.](ubuntu-example-configuration.md)

###Then choose one of the following:

* [Shell Access, git installed](remote-with-git.md) (recommended)
* [use downloader script](remote-with-downloader-script.md) (browser based installation)

##Maintenance

After installing you can use the [maintenance scripts](maintenance.md).