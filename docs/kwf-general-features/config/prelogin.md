#PRELOGIN

The so called PreLogin is an [HTTP basic authentication](https://en.wikipedia.org/wiki/Basic_access_authentication) required for every request if activated. 
It can be used to protect work in progress websites, or test servers.

Activate preLogin by adding

`preLogin = true`

to your `config.ini.` Per default the username and password are test:test _(vkwf: vivid:planet)_. 

Define a different pair by adding

`preLoginUser = USERNAME`

`preLoginPassword = PASSWORD`

It's also possible to send the authorization via X-Kwf-Authorization if the default Authorization-Header is for example needed for OAuth.

##Exceptions to your PreLogin

It's also possible to define exceptions for your pre-login like for your own ip or a path of your website.

###Examples:

`preLoginIgnoreIp.local = 192.168.0.*`

`preLoginIgnore.api = /api/foo`

child paths are also ignored
