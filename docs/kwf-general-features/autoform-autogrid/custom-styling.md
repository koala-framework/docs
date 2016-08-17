     
#STYLING

Basic custom styling for any Ext.Panel including AutoForm or AutoGrid or even an form field can be done by adding 
a class attribute to it's element.

###Examples:

    new Ext.Panel({
        cls: 'example-foo'
    });
     
    new Kwf.Auto.FormPanel({
        cls: 'example-foo'
    });
.
    
    $form->add(new Kwf_Form_Field_TextField('foo'))
        ->setCls('example-foo');