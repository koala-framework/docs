#USER MANAGEMENT CONTROLLERS

Kwf also provides default controllers for user management (create/modify/delete users). For basic usage add the following controllers to your Acl:

    $this->add(new Kwf_Acl_Resource_MenuUrl('kwf_user_users',
            array('text'=>trlKwf('Useradministration'), 'icon'=>'user.png'),
            '/kwf/user/users'));
        $this->add(new Zend_Acl_Resource('kwf_user_user'), 'kwf_user_users');
        $this->add(new Zend_Acl_Resource('kwf_user_log'), 'kwf_user_users');
        $this->add(new Zend_Acl_Resource('kwf_user_comments'), 'kwf_user_users');
        
The user roles a user is allowed to manage are defined through Acl roles (`Kwf_Acl_Resource_EditRole`), 
an example how to create an additional role explains this best:      
 
     $this->addRole(new Kwf_Acl_Role('myrole', trl('My Role')));
     $this->add(new Kwf_Acl_Resource_EditRole('edit_role_myrole', 'myrole'), 'edit_role');
     $this->allow('admin', 'edit_role_myrole');
     
     
In addition you can change the behavior of the user management controllers by inheriting them any changing the Acl accordingly (to point to your custom controllers)