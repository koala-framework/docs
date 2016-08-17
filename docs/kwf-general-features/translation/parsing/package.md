#PARSING

Translations in packages have to be masked only with functions starting with trl...Kwf...().

Translations contained in `kwf-po-file` `(vendor/koala-framework/koala-framework/trl/en.po)` should not be part of your 
packages po file. The script only adds translation to your po file if it's not part of kwf-po-file.

1. clone kwf-trl package
2. go into a webfolder in which you use the package and call 

    `../kwf-trl/bin/trl parsePackage packagename` 

to parse all branches of your package and write en.po file to trl-folder of your package.

This file is the base for further localisation.

Change packagename to the name of the package you want to parse. 
The correct name can be found in the composer.json file from the package.