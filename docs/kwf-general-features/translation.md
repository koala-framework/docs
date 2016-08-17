#TRANSLATION

Internationalisation in Koala Framework is done by masking strings that need to be translated. 
There are a bunch of global functions used for masking strings:

* standard: `trl('Lorem Ipsum'); trl('Lorem {0} Ipsum', 'xy');`
* with context: `trlc('context', 'Lorem Ipsum'); trlc('context', 'Lorem {0} Ipsum', 'xy');`
* plural: `trlp('Lorem Ipsum', '{0} Lorem Ipsums', 2);`
* plural with context: `trlcp('context''Lorem Ipsum', '{0} Lorem Ipsums', 2);`


##Source

Standard `trl()` calls must be used for strings used in the application. 
Strings used inside Koala Framework itself or other supplementary packages must add the postfix Kwf to all 
function names (eg. trlKwf())

##application / web code language

The language of the strings used in the code does not have to be english, it is configrable per application. 
See `webCodeLanguage` setting in `config.ini.`

Strings used in Koala Framework or other supplementary packages must always be written in english.

##Target Languages

####For Backend / ExtJS based Application

The target language is defined by the currently logged in user. Add a language column to the `kwf_user` table to make 
it configurable per user.
Add the available (and translated) languages to `config.ini`:

    languages.en = English
    languages.de = German

####For Frontend in a Component based Web (Kwc)

Each page has a language configured, you can get it using `$data->getLanguage()`. 
All possible languages are returned by individual Components.

If you need further customization the following flags are important: 

* `hasLanguage`
* `hasAvailableLanguages`

##Static strings

Normally the `trl()` function returns the translated string. But to do that it needs to know the target language - 
which it not always knows at that time. This is commonly an issue in `Kwf_Forms` or component settings.

The solution is the Static postfix (eg. trlStatic()) which doesn't translate immediately but only marks the string as 
to-be-translated. Once the target language is known, `Kwf_Trl::trlStaticExecute()` has to be called on those strings 
to get the correct translation.

As `trlStatic()` returns a string it is even possible to concat with other strings or translations: 
`trlStatic('Foo').' - '.trlStatic('Bar')`

##Usage in component template

To mask a text in a template for translation call` $this->data->trl('Lorem Ipsum');.`

##Usage in JavaScript

To mask a text in a javascript file simply use `trl('Lorem Ipsum');`

Every target language will have it's own javascript file with the trl strings replaced.

##Usage in Component Frontend

To use translation in javascript files the `Kwc_Box_Assets_Component` has to be used:
Create a generator in your `Root_Master_Component`.

    $ret['generators']['assetsBox'] = array(
        'class' => 'Kwf_Component_Generator_Box_Static',
        'component' => 'Kwc_Box_Assets_Component',
        'inherit' => true
    );

