#RULES FOR CUSTOMIZING COMPONENTS

A few common practice rules should be followed when creating components:

##Side effects

A component must not have any side effects to any other part of the website.

* CSS: all styles must be scoped within .cssClass (no global styles)
* JS: all code must be wrapped in onElementRady('.cssClass'
* PHP: nothing global must be set during rendering

Show/Hide: a component must not show/hide itself, this must be done where the component is created.

##Translation

All user visible strings must be wrapped into trl() calls.

* getSettings: trlStatic
* getTemplateVars: $this->getData->trl()
* Component.tpl/twig: $data->trl()
* Form/FrontendForm: trlStatic

##Naming

Naming should be consistent:

When you have a FooBar_Component:

* generator key should be 'fooBar'
* container div class/id should be 'fooBar'