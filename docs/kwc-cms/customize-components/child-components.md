#CHILD COMPONENTS

A component can create child components, and you can change the component class of created child components.

To do that you have to modify the generators setting of the component:

    class Example_Component extends Kwc_Abstract_Composite_Component
    {
        public static function getSettings()
        {
            $ret = parent::getSettings();
            $ret['generators']['child']['component']['text'] = 'Kwc_Basic_Text_Component';
            return $ret;
        }
    }
    
    
####There two several ways how generators are defined:

    //generator can have multiple child components
    $ret['generators']['child']['component']['text'] = 'Kwc_Basic_Text_Component';
     
    //generator can have single child component
    $ret['generators']['child']['component'] = 'Kwc_Basic_Text_Component';
    
  
Check the parent component class to see which is the correct way.

## Child Settings
You can change the settings of a child component without creating a separate class for it by using `childSettings`.  
<br>
This should only be done for small changes, if you want to change a large portion of the settings you should create a separate class for it or your code will become confusing.  
<br>
Inside the `$ret['childSettings']` array create an array with the key of "child_" followed by the key of the child component you want to change the settings of.  

```php
$ret['generators']['child']['component']['myText'] = 'MyText_Component';
$ret['childSettings'] = array(
    'child_myText' => array(
        'componentName' => trlStatic('My Text Component')
    )
);
```


### Reset child settings  
By default the `$ret['childSettings']` will be merged with the child's existing settings.  
To fully override these settings set `'_merge'` to `'reset'` in the setting you want to override.  

```php
$ret['generators']['child']['component']['myImage'] = 'MyImage_Component';
$ret['childSettings'] = array(
    'child_myImage' => array(
        'dimensions' => array(
            '_merge' => 'reset',
            'square500' => array('width' => 500, 'aspectRatio' => 1)
        )
    )
);
```

This will remove all the dimensions originally set in the child component and only the 'square500' option will be available.
