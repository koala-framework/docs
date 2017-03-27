#CODING STANDARDS

##General

* General Editor Settings: utf8, 4 space indent,
* max 80 char per line
* everything in english
* Directory paths always without slash at the end (http + filesystem)
* Variable names, css class names, Ids: always englisch
* Variable names, css class names, Ids: camelCase
* Template-Files: CamelCase.tpl
* fuel types: diesel, gasoline, cng, electric, hybrid

##Php:

* [Zend Framework conding standards](https://framework.zend.com/manual/1.12/en/coding-standard.html)
* Cotroller Name: CustomersController (=grid), CustomerController (=form)
* No short-open-tags.

##Database:

* Modelname and Tablename: Plural
* Tablename: starting with app_
* Standard db fields: visible, pos, archive, name
* storage engine innoDb (incl relations)
* Relationtables: app_foos_to_bars
* firstname, lastname (without _ in between!)
* gender ENUM('female', 'male') - if required 'company'

##Translation

* Anrede: trlKwfc('gender', 'Title')
* Titel: trlKwf('Title') (academic Titel)

##Frontend:

* css-colors central defined in ini-file
* div id="mainMenu" id or class - depending if unique
* Design-Images as assets /assets/web/images/
* Filename Images: camelCase.jpg
* li class="current" in menu
* class="" is accepted

##Backbone

    backbone/views/Idea/Collection.scss
    backbone/views/Idea/Collection.underscore.tpl
    backbone/views/Idea/Item.js
    backbone/views/Idea/Item.scss
    backbone/views/Idea/Item.underscore.tpl
    backbone/views/Idea/Item/Header.js
    backbone/views/Idea/Item/Header.scss
    backbone/views/Idea/Item/Header.underscore.tpl
    backbone/views/Idea/Layout.js

##Symfony
###Services
* app.model.folder_camel-case
* app.handler.folder_camel-case
* ...
