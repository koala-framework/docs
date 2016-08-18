#MULTI-DOMAINS

Koala Frameworks supports more domains out of the box.

* Use "Kwc_Root_DomainRoot_Component instead of "Kwc_Root_Component"
* Add settings for every domain to config.ini, e.g.:
    kwc.domains.at.name = Austria
    kwc.domains.at.domain = www.xy.at

Every Domain acts as a subroot. It has it's own home-page, is seperated in the site tree and complete independent to the other domains.

#LANGUAGES

The same technique can also be used for languages.

#OWN SUBROOTS

It's also possible to create own subroots. This can be helpful when you want to have similar data in different branches of the sitetree.
To create a subroot just add the following flag to the settings of the component which should act as an subroot:

`$ret['flags']['subroot'] = 'nameOfSubroot';`