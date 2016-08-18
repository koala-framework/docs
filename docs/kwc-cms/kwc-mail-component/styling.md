#STYLING

Styling of Html Mails can't be done using modern techniques if you want to support a wide range of mail clients. 
Especially Lotus Notes doesn't understand a lot of Css.

We recommend to style Html mails using good old tables.

Components can have additional templates `Mail.html.tpl` and `Mail.txt.tpl` that will be used when rendering them for mails.

`Component.css` won't be used at all.

Additional styles can be added (as replacement for Css styling) by implementing `getHtmlStyles()` method (see below).

##getHtmlStyles()

Overwriting this method in `Kwc_Newsletter_Detail_Mail_Component` allows you to set styles for tags and/or css classes in mails. 
This is used instead of the `Component.css` and has following advantages:

* The styles are applied automatically in a backwards compatible way to support a wide range of mail clients
* It keeps you mail templates tidy

####Set styles for a tag in general:

    array(
        'tag' => 'h1',
        'styles' => array(
            'font-family' => 'Arial',
            'font-size' => '14px',
            'font-weight' => 'bold',
            'color' => '#333333'
        )
    )
    
    
####Set Styles for a table cells with class headline:

    array(
        'tag' => 'td',
        'class' => 'headline',
        'styles' => array(
            'font-family' => 'Arial, Helvetica, sans-serif',
            'line-height' => '16px',
            'color' => '#333333',
            'font-size' => '14px',
            'font-weight' => 'bold'
        )
    )
    
    
####Replace a tag becaue the client doesn't support a specific tag:

    array(
        'tag' => 'strong',
        'replaceTag' => 'b',
        'styles' => array(
            'color' => '#333333',
            'font-family' => 'Arial',
            'font-size' => '12px'
        )
    )
    
    
####Instead of using background-images in css which isn't support by mail clients use appendTags:


    array(
        'tag' => 'li',
        'styles' => array(
            'list-style-type' => 'none',
        ),
        'appendTags' => array(
            'img' => array(
                'src' => '/assets/web/images/aufzaehlung_pfeil.gif',
                'style' => 'padding-right: 5px'
        ))
    )