#USER MODEL

By default users are saved in the database and accessed through a model. 
With `Kwf_Registry::get('userModel')` you can get the user model, which will return an instance of `Kwf_User_Model`.

Using this model you can access the users like a [standard model](../models/basic-usage.md). In addition there are  various methods to access the active user:

* getAuthedUserRole()
*  getAuthedUser()
*  getAuthedUserId()

A common pattern to check for permissions is 
`Kwf_Registry::get('userModel')->getAuthedUserRole()` which returns the user role of the currently authorized user.

To change the user model class use this setting in `user.model` in config.ini, see [config settings](config.md) for more on that.