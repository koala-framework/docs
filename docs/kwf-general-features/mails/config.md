#CONFIG SETTINGS

##Standard sender-name and sender-email for a complete web:

`email.from.address = koala@koala-framework.org`
`email.from.name = Mr. Koala`

This setting will be used as default for every mail sent from koala.

##Send _all_ mails to fixed address:

`sendAllMailsTo = koala@koala-framework.org`

This can be used on test server to avoid "real" mails getting sent.

##Custom SMTP Transport:

    email.smtp.host
    email.smtp.auth
    email.smtp.username
    email.smtp.password

Using those settings will use a different transport than the default one.

