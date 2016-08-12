#CONTROLLERS QUICK START

To get a working controller follow the steps described here.

It is assumed that you use a preconfigured [kwf-app-demo](https://github.com/vivid-planet/kwf-app-demo) or 
[kwf-cms-demo](https://github.com/vivid-planet/kwf-cms-demo) that comes with a `.htaccess` and `bootstrap.php`.


##Add module

Modules are used to categorize controllers into directories. Create a directory in controllers/Foo and register it in `bootstrap.php`:

    $front->addControllerDirectory('controllers/Foo', 'foo');
    
(this step is optional, you can create controllers without module which will end up in module named `default`)

##Create controller class

Create a new class in `controllers/Foo/BarController.php` named `Foo_BarController` that inherits `Kwf_Controller_Action`.

    class Foo_BarController extends Kwf_Controller_Action
    {
        public function indexAction()
        {
            die('foo bar');
        }
    }
    
    
##Create Acl Resource

    $this->addResource(new Kwf_Acl_Resource_MenuUrl('foo_bar', 
    array('text'=>trl('Foo Bar'), 'icon'=>'user.png'), '/admin/foo/bar'));
    
(when using `Kwf_Controller_Front` as frontControllerClass the `/admin` from the url has to be removed)

##Allow resource for a role

    $this->allow('admin', 'foo_bar');
    
[See Acl for more details](../acl).