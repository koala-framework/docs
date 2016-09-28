# INSTALLATION (3.8+)

There are multiple ways how to install koala framework, depending on your server infrastructure.

If you need help contact us on our [mailing list](http://www.koala-framework.org/community/mailing_list).

These instructions are valid for Koala Framework Version 3.8 and greater.

## Development on local machine

Developing any website/application should not be done on production servers for obvious reasons. Instead you should run a local copy of the application where you develop.

For Koala Framework this local is required as it has a build step (Version 3.8+) that needs to get executed locally. The results of the build then must get uploaded to the production server.

For local development you can either:

* [use php built-in webserver](local-development-environment/php-builtin-webserver.md) (easy to set up, not best performance)
* [use apache webserver](local-development-environment/apache.md) (difficult to set up, good performance)
* [use our virtual machine](local-development-environment/virtual-machine.md) (recommended for windows)
as for development the webserver performance isn't critical we recommend the first method.

## Installation on remote Webserver
Which installation method you choose for the remote webserver depends on what you can do on the server.

In any case you need an apache configured with an document root, see ubuntu example configuration.

Then choose one of the following:

* [Shell Access, rsync installed](deployment-to-remote-server/with-rsync.md) (recommended)

## Maintenance

After installing you can use the [maintenance scripts](maintenance.md).
