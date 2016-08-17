#PROCESS CONTROL AND BACKGROUND PROCESSES

Using that feature you can run long-running background processes, 
where process-control will make sure the processes keep running.

##Add the following job to crontab:

    * * * * * php /path/to/web/bootstrap.php process-control
    
    
This cronjob will make sure the processes are running and starts them if required.

##And define the desired processes in config.ini: 

    processControl.foo.cmd = foo ; will start "php bootstrap.php foo"
    processControl.foo.count = 2 ; optional, starts two processes
    processControl.foo.timeLimit = 3600 ; optional, kill process if cpu time is higher than that
    processControl.foo.shutdownFunction = Foo::shutDown ; optional, for clean shutdown (instead of kill)
    
##Process Output:

As the started processes are executed in background you don't get the output.

To view the output manually check the `log/*.log` and `log/*.err` files or use

`php bootstrap.php process-control logcat`

to clear log files use:

`php bootstrap.php process-control logclear`

To get the output sent by e-mail set the following `config.ini `options:

    debug.mailProcessControlOutput = true ;enabled by default on production, disabled on test
    developers.koarl.sendProcessControlOutput = true
    developers.koarl.email = koarl@koala-framework.org
    
    
##Manual control

You can control process control using the following commands:

    php bootstrap.php process-control status
    php bootstrap.php process-control restart
    php bootstrap.php process-control stop
     
     
##Example

typical example of a background job:

    <?php
    class Cli_FooController extends Kwf_Controller_Action
    {
        public function indexAction()
        {
            while(true) { //restart foo action in endless loop
                $cmd = "php bootstrap.php foo foo";
                if ($this->_getParam('debug')) $cmd .= " --debug";
                if ($this->_getParam('verbose')) $cmd .= " --verbose";
                passthru($cmd);
            }
        }
     
        public function fooAction()
        {
            while(true) {
                //do your stuff
     
                sleep(10); //sleep to avoid high cpu usage
            }
        }
    }
     