#CLI CONTROLLERS

Cli controllers are used to encapsulate procedures and access them via command line (CLI-Controller = Command Line Interface Controller). It's also possible to enable this procedures for a cronjob.

##Create an cli-controller

Create a new php file in `/controllers/Cli.` Call it like you want but end it with `'Controller.php'`. It has at least to extend `'Kwf_Controller_Action'` and implement a 'public function `indexAction()`' as main entry point.

It's also important to finish your algorithm with an `'exit;'` statement.

    <?php
    class Cli_MyCustomControllerController extends Kwf_Controller_Action
    {
        public function indexAction()
        {
            //Your logic
     
            exit;
        }
    }

##Call an cli-controller

Navigate to your project folder with your shell or terminal and enter:

    #Cli Controller: controllers/Cli/MyCustomControllerController.php
    php bootstrap.php my-custom-controller
    
To start this script with definied parameter just do it like this:

    php bootstrap.php my-custom-controller --debug
    php bootstrap.php my-custom-controller --count=10