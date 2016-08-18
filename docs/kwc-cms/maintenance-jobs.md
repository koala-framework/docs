#MAINTENANCE JOBS

Koala Framework uses a background process to perform various maintenance jobs. To activate this process you need to add the following line to crontab:

    * * * * * php /var/www/path-to-web/bootstrap.php process-control

clear-cache restarts all process-control processes and the above cron job makes sure processes are still running.

##Jobs

* kwf_pages_meta table update (for sitemap.xml)
* fulltext content update (if used)
* newsletter sending (if used)
* plus any custom jobs


##Create custom job

    class MyComponent_ExampleJob extends Kwf_Util_Maintenance_Job_Abstract
    {
        public function getFrequency()
        {
            return self::FREQUENCY_DAILY; //or: FREQUENCY_MINUTELY, FREQUENCY_SECONDS
        }
     
        public function getPriority()
        {
            return 0; //higher priority is executed after lower priority, default is 0
        }
     
        public function execute($debug)
        {
            // add code the execute here
        }
    }
     
     
    class MyComponent_Component extends Kwc_Abstract implements Kwf_Util_Maintenance_JobProviderInterface
    {
        public static function getMaintenanceJobs()
        {
            return array(
                'MyComponent_ExampleJob'
            );
        }
        
        
##Manually run jobs for development

####run minutely jobs:

`php bootstrap.php maintenance-jobs run --debug`

####run daily jobs:

`php bootstrap.php maintenance-jobs run-daily --debug`

####list all maintenance jobs:

`php bootstrap.php maintenance-jobs show-jobs`

####run a single job:

`php bootstrap.php maintenance-jobs run-job --job=CLASSNAME`