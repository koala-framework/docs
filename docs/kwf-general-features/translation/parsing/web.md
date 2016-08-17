#PARSING

All trl(...) strings need to be collected into a single po file used as a base to translate into different languages.

Translated po files need to be present in /trl folder during build to be used.

##Parse your content

Checkout [https://github.com/koala-framework/kwf-trl](https://github.com/koala-framework/kwf-trl) (e.g. in your www folder)

It does contain a script to parse your code. In your web folder just call

`../kwf-trl/bin/trl parseWeb`

This creates a po file containing every text masked with trl(...) in all of your web branches.

Use this po file as base for your translations.