#LOCALIZE WEB

##Translate and provide po files

There are several options helping you to translate po files for a web. For example

* Upload your po-file to [lingohub](https://lingohub.com/)
* use [Qt4 Linguist](http://doc.qt.io/qt-4.8/linguist-manual.html)
* or [Poedit](https://poedit.net/)

If using lingohub you got the option to work with kwf-lingohub to get your translation into your web, 
else you need to do it manually.

##WORKING WITH LINGOHUB

If using lingohub you first need to upload your parsed po files to lingohub. 
(it's planned to do this automatically after parsing)

It's recommended to add [kwf-lingohub](https://github.com/koala-framework/kwf-lingohub) as requirement to your composer.json:

    {
        "require": {
            "koala-framework/kwf-lingohub": "dev-master"
        }
    }
    
    
 You also need to set your account and project name in composer.json to enable kwf-lingohub to automaticall download needed 
 resources on composer install and composer update.   
 
    {
        "extra": {
            "kwf-lingohub": {
                "account": "myaccount",
                "project": "myproject"
            }
        }
    }
    
    
and your api-token in a config folder of your home directory. You find it in your lingohub account-settings on the right side.   

    ~/.config/koala-framework/kwf-lingohub/config
     
    {
        "apiToken": "YOUR-TOKEN"
    }
    
    
##MANUALLY PROVIDING TRANSLATION

If you are providing translation on your own (like with qt4 linguist or any other translation tool) you
need to save your translation in trl folder

`trl/language-code.po` (e.g. trl/de.po for german)

and build your project to enable it.