#SET DASHBOARD IN BACKEND

At first you have to create your Ext-configuration with JavaScript. For more information look at ExtJS 
Integration=>[Quick Start](quick-start.md).
Don't forget to add your used controller to your `Acl.php.`

###The important step is this:
There is a global JavaScript variable called "Welcome" which contains an Ext-configuration of a panel to show in backend at /admin. (That's normally a box with your web-name and the Kwf Version)
Just asign Welcome your dashboard variable.

For example you did the Quick-Start you have to add this line at the end of your JS file:

`Welcome = Example.Foo;`