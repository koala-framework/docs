# Template helpers
Koala provides a set of helper classes for html based on `Zend_View` helpers.  
You can find the full list under `/Kwf/View/Helper/` or you can search for them in our [docs](http://www.koala-framework.org/docs/).

## Extend another twig file

Extend a component's `Component.twig` file:
```twig
{% extends renderer.getComponentTemplate("MyComponent") %}
```

Extend any twig file:
```twig
{% extends "path/to/my/template.twig" %}
```

## Render an image-tag

```twig
{{ renderer.image("/assets/web/images/myImg.png", "Alt text")) }}
```

**Render an image-tag with html-attributes and inline styles:**  
*This should only be used if styling with css is not possible, for instance in HTML-Emails.*

```twig
{{ renderer.image('/assets/web/images/myImg.png', "Alt text", {'width': 100, 'height': 40, 'border': 0, 'style': 'vertical-align: middle; text-decoration: none;'}) }}
```

## Render a link to a component's page

```twig
{{ renderer.componentLink(targetComponent, "Link text")) }}
```

**Render a link to a component's page with inline styles:**  
*This should only be used if styling with css is not possible, for instance in HTML-Emails.*

```twig
{{ renderer.componentLink(targetComponent, "Link Text", {'style': 'text-decoration: none;'}) }}
```

## Mail Link
This encodes an email address, so it cannot be found too easily by crawlers looking for spam targets.

```twig
{{ "koal@koala-framework.org"|mailLink }}
```

This will be converted to the following HTML.   
As soon as JS is loaded it will be decoded and will function like any other mailto-link.

```html
<a href="mailto:koal(kwfat)koala-framework(kwfdot)org">
    <span class="kwfEncodedMail">koal(kwfat)koala-framework(kwfdot)org</span>
</a>
```
