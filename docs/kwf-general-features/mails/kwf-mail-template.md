#KWF_MAIL_TEMPLATE

`Kwf_Mail_Template` allows sending mails similar to `Kwf_Mail` but adds support for templates.

First you have to create a new Kwf_Mail_Template object with the 'new' operator. You will have to set the `$template` parameter. This can either be a path (but no absolute) to your template in /views/mails or even a component- or a data-object. In the second case the template has to be placed in the component-folder.

Now you only have to set the receiver (and cc and bcc if you need) and call send.

There are several options you can configure. Just look at the Koala-Doc or directly in source code.

##Code Example

###view / mails / MyTemplate.html.tpl

    <p>Dear <?=$this->fullname?>,</p>
    <p>This is a message from Koala Framework.</p>
    
    
###view / mails MyTemplate.txt.tpl

    Dear <?=$this->fullname?>,
     
    This is a message from Koala Framework.
    
##Php code

    $mailTemplate = new Kwf_Mail_Template('MyTemplate');
    $mailTemplate->fullname = 'FooBar' //assign var that can be used in views
    $mailTemplate->addTo('recipient@example.com');
    $mailTemplate->setFrom('sender@example.com', 'Example Name'); //optional, to override config default
    $mailTemplate->setSubject('Example');
    $mailTemplate->send();