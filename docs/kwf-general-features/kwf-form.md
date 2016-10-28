#KWF_FORM


Using `Kwf_Form` you can describe a form including it's fields, labels etc.

It can be used in two ways:

* as ExtJS based form (AutoForm), rendered and submitted using only JavaScript
* as Kwc Component based form (`Kwc_Form_Component`), rendered using HTML only, submitted using JavaScript with HTML only fallback

####Advantages:

* single API for AutoForms and Component forms
* same form where user enters data in Frontend can be used to edit the data in backend
* easy to switch from AutoForm to Frontend form

####Features:

* Clientside (JavaScript) validation
    * for AutoForm using purely ExtJS
* Serverside validation
    * using Zend_Validate
* write/read from Kwf_Model
* AutoForm: attach to AutoGrid using bindings
* easy to extend by writing custom fields


##Usage

    class MyForm extends Kwf_Form
    {
        protected _initFields()
        {
            $this->add(new Kwf_Form_Field_TextField('name', 'Name'));
            $this->add(new Kwf_Form_Field_NumberField('age', 'Age'))
                ->setAllowNegative(false);
                ->setAllowDecimals(false);
        }
    }
    
####Alternative:
   
    $form = new Kwf_Form();
    $form->add(new Kwf_Form_Field_TextField('name', 'Name'));
    $form->add(new Kwf_Form_Field_NumberField('age', 'Age'))
        ->setAllowNegative(false);
        ->setAllowDecimals(false);
        
        
##Default Width for Fields in Container

It is possible to set a default width for every field in a container. 
You only have to call setDefaultFieldWidth on a container.

####For example:

    $form = new Kwf_Form();
    $form->setDefaultFieldWidth(300);
    $form->add(new Kwf_Form_Field_TextField('name', 'Name'));


##Error Message

Form Error Messages can be shown below the formField or with a bubble.
Edit your config.ini to get one of the two styles.

    kwc.form.errorStyle = belowField
    //OR
    kwc.form.errorStyle = iconBubble


##Field Properties

The supported properties are based on ExtJS Form config. Look up the relevant Field in the Koala api documentation 
to get supported properties: [http://www.koala-framework.org/docs/](http://www.koala-framework.org/docs/) (Form Package)

Additionally for ExtJS forms any property unknown to Koala is used as field config, refer to the ExtJS documentation 
for all possible properties: [http://dev.sencha.com/deploy/ext-2.3.0/docs/?class=Ext.form.NumberField](http://dev.sencha.com/deploy/ext-2.3.0/docs/?class=Ext.form.NumberField) However keep 
in mind that those won't work for Component forms, and any server side validation / formatting won't happen
