#UNIT TESTS

Koala Framework is backed by many unit tests. PhpUnit is used as test framework.

####To execute all tests run in koala-framwork repository:

`php bootstrap.php test`

You can use the usual phpunit options like --filter --group --exclude-group.

For example to run a specific test call

`php bootstrap.php test --filter=Foo_Test::testMyFunction //Foo_Test is the class-name of your testclass, testMyFunction the function-name of the test-case`

##Config

To run all tests you need the following config:

####**tests/config.local.ini:**

    [production]
    server.domain = kwf.local
    server.baseUrl = ""
    server.testBrowser.Firefox.host = myownhost
    server.testBrowser.Firefox.port = 4444
    server.testBrowser.Firefox.browser = *firefox
    server.testBrowser.Firefox.name = Firefox
    server.autoStopTest = false
     
    googleMapsApiKeys.kwflocal = XYZ
    debug.querylog = true
    debug.eventlog = true
    debug.benchmark = true
    debug.benchmarklog = true
     
    libraryPath = /var/www/library