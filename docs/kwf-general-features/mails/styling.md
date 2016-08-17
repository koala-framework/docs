#SCSS STYLING IN MAIL

You need to add your scss file to a package in your `dependencies.ini`. 
This can be named like anything. In our case it's "Mail". Everything added to this package will be collected together.

`dependencies.ini`

   [dependencies]
   ....
   Mail.files[] = web/views/mails/Mail.scss
    
    
Now you need to tell the build to compile everything in this package and create the file containing all compiled data.

`config.ini:`

    assets.packages[] = Mail
    

You also need to add this code snippet to your `Mail.html.tpl` to include the compiled package into your mail.

    <style>
        <?php 
            echo Kwf_Assets_Package_Default::getInstance('Mail')->getBuildContents('text/css', 'de');
        ?>
    </style>