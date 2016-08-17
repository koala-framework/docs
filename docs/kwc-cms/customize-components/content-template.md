#STYLING - TEMPLATE

For changing the Html output of a component create a Component.tpl or a `Component.twig` file in the component folder. 
It will be picked up automatically. Templates from parent component classes can't be used if a component has it's own template.

To allow styling scoped to this component you should always include a div with `class="$this->cssClass"` in `Component.tpl` 
or with `class="{{ cssClass }}"` in `Component.twig` file as outer element.

The templates are rendered using `Zend_View`. You can add variables to the template by implementing `getTemplateVars` in the 
Php class.

###Tpl - Example:

    <div class="<?=$this->cssClass?>
        <h1>foo</h1>
    </div>
    
###Twig - Example:

    <div class="{{ cssClass }}">
            <h1>Some content</h1>
    </div>
    
###Twig - Blocks

With a block we can change parts of a template. It's a better approach than to copy the whole template.

    <div class="{{ cssClass }}">
        {% block replaceableContent %}
            <h1>Some content you can overwrite in a Childcomponent</h1>
        {% endblock %}
    </div>
    
    
###Twig - Overwrite parts of a template:

To change only parts of a parent template by using the blockelements, simple make a Component.twig and extend from 
the template you need and overwrite the blockelement you want to change. It's a better approach than copy the whole 
template and overwrite it.

    {% extends renderer.getComponentTemplate("Kwc_Menu_Mobile_Component") %}
     
    <div class="{{ cssClass }}">
        ...
    </div>
    
    
###Twig - Php Variables:

Variables defined in the `getSettings()` function like `$ret['placeholder']['menuLink'] = trlKwfStatic('Menu');` 
are accessible like that.

    <div class="{{ cssClass }}">
        {{ placeholder.menuLink }}
    </div>
    

###Twig - Php Variables:

Variables defined in the `getTemplateVars()` function like `$ret['title'] = 'title';` are accessible like that.

    <div class="{{ cssClass }}">
        {{ title }}
    </div>