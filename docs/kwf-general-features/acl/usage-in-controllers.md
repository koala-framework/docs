#ACL CHECK IN CONTROLLERS

All controllers inheriting `Kwf_Controller_Action` by default check the acl if the currently authorized user is allowed to access this controller.

Any other permission check has to be done by yourself by accessing the User Model and the Acl.