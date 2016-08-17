#UPDATE TO 3.9+

If you'r updating from any web prior 3.9 to 3.9+ you need to convert your trl.xml files into po files.

This is done automatically during upgrade-script. There should be one po file for every supported language. 
If it's explicitly needed you can call the script directly via

`php upgrade-to-3.9/trl convertTrlXmlToPo --trlXmlPath=trl.xml --outputPath="..." --webcodeLanguage="..." --targetLanguage="..."`

If you'r planning to use [kwf-lingohub](https://github.com/koala-framework/kwf-lingohub) you'll need to add trl folder to your `.gitignore`. 
If `vivid-planet/vkwf` is existing it's done during upgrade-script.

Next step ist to create a [lingohub project](create-lingohub-project.md)