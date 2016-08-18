#EVENT-COMPONENT

This component is used to display a list of events depending on the actual date.

##How to enable and customize

At first you need the `kwf/Kwc/Events/Directory/Component.php.`
This class is the super-class of your own customized.

If you want to have several independent event lists, and all events collected on one page just add this class to your `config.ini` like this:

     kwc.childComponents.Kwc_Root_Category_Component.YOUR_SITE_TYPE_ID = CLASSNAME 
     
or if you want only one list add it to your `/Root/Component.php` via Generator:

(Please insert code-example)

####Independent of your choice of how to provide the event list(s) you have now many things to provide and customize:

##View

This component can be customized like every other component. Please just make sure you change all references of depending components. 
(This can mean to extend other classes with new php-classes or via yml-files)

##Top / TopChoose

This is used to show only a defined amount of events. Starting from today.

###Top

You have to define by code which eventlist to use.

###TopChoose

Using this component you have the possibility to select which eventlist to use in backend configuring this component.