#NAVIGATION WITH SUBROOTS

When navigating through the sitetree the parameter "subroot" can be added to stay in the branch of the given subroot. 
E.g. you want to search for the News Component. Normally this component only exists once, so you can use the following statement:

`Kwf_Component_Data_Root::getInstance()->getComponentByClass('News_Component');`

When having subroot it's likely that every domain has a News Component. So the above statement would result in an error because 
it cannot return a unique component. To retrieve the News Component of the subroot where you're currently in, use:

`Kwf_Component_Data_Root::getInstance()->getComponentByClass('News_Component', array('subroot' => $component));`

When you're inspecting the code of the Koala Framework you will see that in many cases this parameter is used automatically.