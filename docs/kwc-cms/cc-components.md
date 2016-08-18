#COPYCONTENT / CC COMPONENTS

When you browsed the Koala sources you will have probably recognized the cc components.

This components are used to show a copy of a component on a different place in your component tree.

###You can use it like this:

* Create a component which should copy another component
* Analyse the component you want to copy
* Configure your copy component


##Create a copy component

Create a new class extending '`Kwc_Chained_CopyTarget_Component`'. It should look like this:


    <?php
       class Lessons_Category_Detail_Component extends Kwc_Chained_CopyTarget_Component
       {
           public static function getSettings()
           {
               $ret = parent::getSettings(false);
               return $ret;
           }
       }
       

##Analyse the component you want to copy

Open the component and follow the base classes (and the containing folder) till you find the first Cc folder with containing `Component.php`
For example if you want to copy a component extending CompositeComponent you will have to make one parent-step to CompositeComponent 
and head into the Cc folder and note the class name of the `Component.php`

##Configure your copy component

Now you should have the base Cc Component name and the class name of the component you want to copy.

In case your component name is "`Lessons_Detail_Component`" and it extends "`Kwc_Abstract_Composite_Component`" you will have to insert following line 
to your "getSettings()"-function:

`$ret['generators']['target']['component'] = 'Kwc_Abstract_Composite_Cc_Component.Lessons_Detail_Component';`

The first part of the asigned string is the first Cc component in inheritance (the class name you noted) and after the dot the component you want to copy.

####The last step is to define which data should be shown. You have to implement getTargetComponent function. It could look like this:

    public function getTargetComponent()
        {
            $lessonId = $this->getData()->row->lesson_id;
            return Kwf_Component_Data_Root::getInstance()->getComponentByDbId('lesson-'.$lessonId);
        }
    
    
