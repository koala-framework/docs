#PARSING

Add [https://github.com/koala-framework/kwf-trl](https://github.com/koala-framework/kwf-trl) to your project composer.json and run "composer update"

To parse koala-framework in kwf-folder simply call

`vendor/bin/trl parseKwf`

#####But this should only be needed if you improved or added code to our koala-framework repository.

This iterates over different branches collecting trlKwf-masked texts into en.po file.

Normally you don't need to do that because as soon as your code is merged to our repository we'll do that 
for you and upload it to our lingohub.com project.
