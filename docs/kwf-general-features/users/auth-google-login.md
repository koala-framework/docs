#GOOGLE OAUTH LOGIN

Using the Auth Methods you can easily enable SSO login by using the kwf-google-auth package which provides an auth method for that.

First you have to create a new project in the [Google API Console](https://console.developers.google.com/dcredirect?pli=1) and create a new OAuth crendential. (`APIs & auth » Credentials » OAuth » Create new Client ID`)

In "Authorized JavaScript origins" enter the domain where your project runs.

In "Authorized redirect URIs" enter the domain plus the following path: 

`https://www.example.com/kwf/user/login/redirect-callback`

(Note that the only local domain allowed by google is localhost)

####The install the required package:

    composer require koala-framework/kwf-google-auth
    
####Add the required config.ini settings:

    user.model = Users
    user.auth.memberGoogle.clientId = xxxx
    user.auth.memberGoogle.clientSecret = xxxx
    
####And create the following classes in models/ folder:   
 
     class Users extends Kwf_User_Model
     {
         protected $_proxyModel = 'UserEditModel';
     }
      
     class UserEditModel extends Kwf_User_EditModel
     {
         public function getAuthMethods()
         {
             $ret = parent::getAuthMethods();
             $ret['google'] = new Kwf_GoogleAuth_Auth(
                 array(
                     'clientId' => Kwf_Config::getValue('user.auth.memberGoogle.clientId'),
                     'clientSecret' => Kwf_Config::getValue('user.auth.memberGoogle.clientSecret'),
                 ),
                 $this
             );
             return $ret;
         }
     }
     
This will show an Login with Goolge+ Button in the Login Page.

##Disable Password login

If you want to use google login only you can disable the password: 


    class UserEditModel extends Kwf_User_EditModel
    {
        public function getAuthMethods()
        {
            $ret = array(); //don't call parent, so we don't have default auth methods
            $ret['google'] = new Kwf_GoogleAuth_Auth(
                array(
                    'clientId' => Kwf_Config::getValue('user.auth.memberGoogle.clientId'),
                    'clientSecret' => Kwf_Config::getValue('user.auth.memberGoogle.clientSecret'),
                ),
                $this
            );
            return $ret;
        }
    }
     