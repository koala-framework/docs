#HTTPS SUPPORT

Koala Frameworks supports automatic redirects to https.

##Enable

###config.ini :
`server.https = true`

##only for specific domains

This is required if not all domains have a certificate. If not configured it is assumed that all domains have a certificate.

###config.ini:
`server.httpsDomains[] = www.example.com`

`server.httpsDomains[] = *.foo.com`

##Https for all requests (only < 3.10)
to force https for all requests (not just for the points above) add the following.

###bootstrap.php
`//after Kwf_Setup::setUp()`

`Kwf_Util_Https::ensureHttps();`