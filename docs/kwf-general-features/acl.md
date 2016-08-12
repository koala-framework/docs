#ACL

Koala Framework uses the Zend Framework access control list (ACL) and adds a few useful additions. 
To understand this documentation you should read the [Zend Framework documentation](https://framework.zend.com/manual/1.12/en/zend.acl.html) first.

#####In Koala Framework the ACL is used for two things:

* Control the access of controllers (for security)
* Generate a menu that will show only allowed menu items
* Furthermore one important concept in Koala Framework is that a resource is a controller.
  
* The most common used resources are:
  
* Kwf_Acl_Resource_MenuUrl (menu item plus a controller. Also has it links to (usually the controller - but that is not required))
* Kwf_Acl_Resource_MenuDropdown (displays a dropdown menu, doesn't represent a controller)
* Zend_Acl_Resource (for controllers that are not visible in the menu)
* Koala Framework also defines a few default roles:
  
* guest (used for not logged in users)
* admin (has all resources (including debug related) allowed)
* cli (used on the command line)
* superuser (has all resources allowed)