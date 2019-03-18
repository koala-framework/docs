# Templates

To change a component's HTML output, you can create a `Component.twig` file in the component's folder.  
The file will be used after the next build of the project.

For detailed information on how to use the twig template-engine, you can read the <a href="https://twig.symfony.com/" target="_blank">official twig-documentation</a>.

## Example: Component.twig
In the `Component.twig` you have access to a variable `rootElementClass`.  
This is a class-name unique to your component.

```twig
<div class="{{ rootElementClass }}">
    <h1>Example content</h1>
</div>
```

## Styling the template
To style the html of your component, you can add a `Component.scss` file.  
You can then add your styles to the css-selector `.kwcClass`, this will reference the `rootElementClass` set in your `Component.twig`. 
 
```scss
.kwcClass {
    // Styles for the html-element with the class "rootElementClass".
}
```

## Defining variables for your template

You can access anything returned by the `getTemplateVars()` function of your `Component.php` like follows: 

```php
public function getTemplateVars(Kwf_Component_Renderer_Abstract $renderer)
{
    $ret = parent::getTemplateVars($renderer);
    $ret['myText'] = "Some text";
    return $ret;
}
```

```twig
<div class="{{ rootElementClass }}">
    {{ myText }}
</div>
```

You can also access anything in the `placeholder` array returned in the `getSettings()` function of your `Component.php` like follows:
```php
public static function getSettings($param = null)
{
    $ret = parent::getSettings($param);
    $ret['placeholder']['myText'] = "Some text";
    return $ret;
}
```

```twig
<div class="{{ rootElementClass }}">
    {{ placeholder.myText }}
</div>
```
