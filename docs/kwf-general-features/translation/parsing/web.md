#PARSING

All trl(...) strings need to be collected into a single po file used as a base to translate into different languages.

Translated po files need to be present in /trl folder during build to be used.

##Parse your content

Add [https://github.com/koala-framework/kwf-trl](https://github.com/koala-framework/kwf-trl) to your project composer.json and run "composer update"

It does add a script to parse your code. In your web folder just call

`vendor/bin/trl parseWeb`

This creates a po file containing every text masked with trl(...) in all of your web branches.

Use this po file as base for your translations.
