#DOMAIN CONFIGUARTION

The domain the website runs on you already configured during setup: server.domain

Now what Koala does it redirects all incoming requests with a different domain (`Host:` field in HTTP Header to be precise) 
to this server.domain. After all we don't want multiple domains with the same content ending up in the google index.


##No Redirect Pattern

To disable that redirect for some domains set server.noRedirectPattern with a regular expression - if that matches no redirect will be performed.

`server.noRedirectPattern = "^relaunch\.koala-framework\.org$"`

This can be use when building a relanuch and and old website still points to the old server. Or when moving servers and a subdomain points the new server for testing.

Make sure to remove the pattern when it isn't needed anymore, else sooner or later google will pick it up.

####For multiple domains a clever regexp with | (=or) can help:

`"^relaunch\.koala-framework\.org|foo\.koala-framework\.org$"`

##Preliminary Domain (Since 4.1)

When the Domain doesn't yet point to the webserver and you have a temporary, preliminary domain (usually some subdomain) you can set
 `server.preliminaryDomain`.
 
####This will disable the redirect to `server.domain` (like noRedirectPattern) but also:

* enable Pre Login for that preliminary domain (to make sure google doesn't index it)
    (set server.preliminaryDomainPreLogin = false to disable)
* use that domain when generating preview urls in the CMS

##Multi-Domain configurations

When using Kwc_Root_DomainRoot_Component to create a multi domain site we obviously can't redirect all domains to server.domain. 
No redirect will be performed for any domain listed under kwc.domains:

`kwc.domains.foo.domain = www.example.com`

`kwc.domains.bar.domain = www.bar.com`

Now if a request comes in with a domain not listed here Koala again redirects to one of them - but which one? 
Use the pattern config to match them with a regular expression. Here some examples:

`kwc.domains.bar.pattern = "bar\.com$" ;match all subdomains`
`kwc.domains.bar.pattern = "^www.bar\.(com|org)$" ;match .com and .org`
`kwc.domains.bar.pattern = "^www.bar\.[a-z]+$" ;match any tld`

The first listed domain (foo in the example) doesn't need a pattern as it will be the default if none of the patterns match.

Similar to server.noRedirectPattern the redirect also can be disabled for kwc.domains. But keep in mind that pattern **must match first:**

`kwc.domains.foo.noRedirectPattern = ^relaunch\.example\.com$`

And, as for server.preliminaryDomain that is also possible:

`kwc.domains.foo.preliminaryDomain = relaunch.example.com`

With prelogin by default that can be disabled using

`kwc.domains.foo.preliminaryDomainPreLogin = false`