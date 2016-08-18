#KWC_MAIL_EDITABLE_COMPONENT

This component is usefull if you want to edit the mail in backend. It's required to place the `Kwc_Mail_Editable_Component` somewhere in your 
component-structure.

You will find a button in your top-toolbar called "Mail Texts". There you can edit every `Kwc_Mail_Editable_Component` existing in your web.

To send the mail you will simply have to get the component and call `createMail()` with a recipient (an object implementing `Kwc_Mail_Recipient_Interface`) 
and call send on the returned object. 
The `Kwc_Mail_Editable_Component` will have to handle dynamic data if existing. You get the recipient as parameter in your getTemplateVars.