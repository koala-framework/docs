#QUICK START

When implementing your own Acl you usually create a class named `app/Acl.php` containing a `Acl` class. 
Then set this class as `aclClass` setting in config.ini.

##Inherit existing Kwf Acl

Depending on your requirements you can inherit the required Acl class:

* Kwf_Acl (when not using components)
* Kwf_Acl_Component (when using CMS and components)

##Create custom resources

In the constructor of your Acl class add a new resource like this:

    $this->addResource(new Kwf_Acl_Resource_MenuUrl('controllermodule_controllername',
                    array('text'=>trl('Text'), 'icon'=>'user.png'),
                    '/controllermodule/controllername'));
        $this->addResource(new Zend_Acl_Resource('controllermodule_othercontroller'), 'controllermodule_controllername');
        
`othercontroller` is added with a given parent, with means users that can access the parent can also access `othercontroller`.

##And then allow this new resource for a role:

    $this->allow('admin', 'controllermodule_controllername');
    
##Create dropdown menu items

for categorizing the menu you can easily create a dropdown using the Acl:

    $this->addResource(new Kwf_Acl_Resource_MenuDropdown('foo_categoryname',
                    array('text'=>trl('Category'), 'icon'=>'user.png')));
        $this->addResource(new Kwf_Acl_Resource_MenuUrl('foo_bar',
                    array('text'=>trl('Text'), 'icon'=>'user.png'),
                    '/foo/bar'), 'foo_categoryname');