#PRIVATE FONTS REPOSITORY

**Basic proceed for a font:**

First create a git-repo for the font at "phabricator.vivid-planet.com", name like "myFont-font", and clone it to your local machine. Than put the font-files into the folder "font" and create a font.css and bower.json at root level.

Add the font-repo to the composer.json of your web (see: Usage in Web) and do a composer install.

**bower.js**


   
    {
         "name": "example-fonts",
         "version": "1.0.0",
         "authors": [
         ],
         "description": "Example Fonts",
         "license": "prop",
         "private": true
       }
           
           
**fonts.css**



    @font-face {
        font-family: 'Example';
        src: url('/assets/example-fonts/fonts/example.eot');
        src: url('/assets/example-fonts/fonts/example.eot?#iefix') format('embedded-opentype'),
             url('/assets/example-fonts/fonts/example.woff') format('woff'),
             url('//assets/example-fonts/fonts/example.ttf') format('truetype'),
             url('/assets/example-fonts/fonts/example.svg#Example') format('svg');
        font-weight: normal;
        font-style: normal;
    }
    
     
Now add and commit all files.

**create tag**

    git tag v1.0.0
    git push origin v1.0.0
    
    
    
###Usage in Web

     "extra": {
            "require-bower": {
                "example-fonts": "ssh://git@phabricator.vivid-planet.com/diffusion/EXAMPLEFONTS/example-fonts.git#1.0.0"
            }
        }
        

.



    $ret['assets']['dep'][] = 'FontFaceExample';
    
    
FontFaceExample = "FontFace" expanded with the name of the font you gave in bower without the "-font" extension.
    
    


    
    

