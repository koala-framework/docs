#SIMPLE DEBUGAPPROACH FOR SASS

####In bootstrap.php:

    $d = new Kwf_Assets_Dependency_File_Scss('web/themes/Theme/Master.scss');
    echo ($d->getContentsPacked('de')->getFileContents());
    exit;

####and then comment out most scss in Master.scss and only  let one simple selector in use to start debugging:

To view sass variables use: 

    debug: $val; 

where `$val` can be every variable.