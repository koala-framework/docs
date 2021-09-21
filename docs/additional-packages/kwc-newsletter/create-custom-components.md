#CREATE CUSTOM COMPONENT

It's best practice to place your component in

`Newsletter/Detail/Mail/Paragraphs/YOURCOMPONENT/`

in your project.

Like in any other component you will need a `Component.php` and `Component.tpl`. But additionally you will need a `Mail.html.tpl` and a` Mail.txt.tpl`. 
Those two are needed to define how to render the component for an email-client like thunderbird. 
The html-template is used if the client uses html and the txt-template is used as a fallback in case html isn't supported.

If you wonder where the Component.tpl is needed and used, it's used in backend to show the content for the user creating the newsletter layout. 
So it should match the Mail-templates.

Anything else is just like in any other component. So you can define your own Form, Model, Controller etc.