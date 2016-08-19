#VARIOUS SNIPPETS

###Zendesk Login Normal

http://rssinclude.zendesk.com/access/normal/

###Formulare:

* [Mehrspaltiges Formular](../../kwf-general-features/kwf-form/container-columns.md)


###Sort by Position

* Create a SMALLINT Field in database called 'pos' (+ update script)
* Make a Model.php and [set the filter](../../kwf-general-features/models/filters.md)
* in Grid: `protected $_position = 'pos';`



###Add a component to the paragraphs

`kwc.childComponents.Kwc_Paragraphs_Component.componentName = ComponentClass`

###Add a component as Pagetype

`kwc.childComponents.Kwc_Root_Category_Component.componentName = ComponentClass`

###ltanierende CSS Klasse in Partial.tpl

`< ?=$this->dynamic('Alternate')? >`

###Hover Bubble

Es wird nur ein DIV mit der Klasse "kwfSwitchHoverFade" benötigt. In diesem DIV muss sich dann ein DIV mit der Klasse "switchLink", der als link für Hover dient. Weiters benötigt man ein DIV mit der Klasse "switchContent", inder der Inhalt für die Bubble ist. Zudem wird dieser Eintrag in der dependencies.ini:

    Frontend.dep[] = Components
    
    Frontend.dep[] = KwfSwitchHoverFade

Referenz: `Verkäuferinfo -> Components -> Articles -> Detail -> Component.tpl`

##db query backtrace (zum debuggen)

in der Datei: Kwf/Db/Profiler.php die Zeile $this->_logger->debug(btString()); auskommentieren


###Empty Link

prevents the link of the href="#" behaviour

###Move the Component to the horizontally menu as Button (componentName required)

`$ret['menuConfig'] = 'Kwf_Component_Abstract_MenuConfig_SameClass';`

###Brake ordering process in Shop on last step

Set "`return;`" before "`$order->save();`" in `Shop/Cart/Checkout/Payment/Abstract/Component`

