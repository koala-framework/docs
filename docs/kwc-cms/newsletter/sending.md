#SENDING

Sending out newsletter mails is done by a background process that has to be started using maintenance jobs.

####Add cronjob that starts process-control processes:

    * * * * * php /var/www/path-to-web/bootstrap.php process-control
    
###before 3.10: (deprecated)

Sending out newsletter mails is done by a background process that has to be started using process-control.

1. Add newsletter command to processControl config (`config.ini`)


        processControl.newsletter.cmd = newsletter start
    

2. Add cronjob that starts process-control processes



        * * * * * php /var/www/path-to-web/bootstrap.php process-control
    
    
###before 3.5: (deprecated)

Sending out newsletter mails is done by a cron job.


###Set up the cron job to be executed every minute:

        * * * * * php /var/www/path-to-web/bootstrap.php newsletter

If you don't configure the cron job no sending at all will happen.