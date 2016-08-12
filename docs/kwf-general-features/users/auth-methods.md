#AUTH METHODS

Koala Framework supports flexible configuration of how to authenticate, called auth methods.

To change them you first need a custom user model - inherit the default one and set the [relevant config settings](config.md).

    
    class Users extends Kwf_User_Model
    {
        public function getAuthMethods()
        {
            $ret = parent::getAuthMethods();
            $ret['custom'] = new MyAuth($this);
            return $ret;
        }
    }
    
    
##Interfaces

An Auth class must implement one of the following interfaces:

* ` Kwf_User_Auth_Interface_Redirect:` Authenticate using external server by redirecting to it, for example OAuth, SAML.
* `Kwf_User_Auth_Interface_Password:` Authenticate using given username and password
* `Kwf_User_Auth_Interface_AutoLogin:` Automatic login based on auto login cookie


##Defaults

By default `Kwf_User_Model` has the following configuration:

    public function getAuthMethods()
        {
            return array(
                'password' => new Kwf_User_Auth_PasswordFields(
                    $this
                ),
                'autoLogin' => new Kwf_User_Auth_AutoLoginFields(
                    $this
                )
            );
        }
        
   
##Other Auth Methods

We are currently working on auth methods for Google+ Login and Facebook Login.
     