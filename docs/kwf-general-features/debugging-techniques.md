#DEBUGGING TECHNIQUES

Koala Framework provides a few useful debugging tools.

##Disable Error Log

When developing locally you should always disable the error log - which will result in errors getting printed directly. 
Set `debug.error.log = false` in `config.local.ini`

Further it is recommended to `enable display_errors` in `php.ini` for local development and test servers.

##Debug Output

* `p("abc")` (p stands for print): echo given expression
* `d("abc")` (d stands for die): echo given expression and die after that
* `bt()` (bt stands for backtrace): echo backtrace
* `Kwf_Debug::disable()` / `Kwf_Debug::enable()`: disable any debug output until it's enabled again. (can be called multiple times)

##Querylog

Useful to profile or debug sql queries.

To enable set `debug.querylog = true` in `config.local.ini`. All sql queries will be logged into a file querylog in the 
application root. Some useful statistics are included.

##Eventlog

Useful to debug events (mainly used for clearing view cache).

Similar to querylog, can be activated using `debug.eventlog = true` in `config.local.ini`.

##Benchmark

Shows a box containing various benchmarks for every frontend page in the top right corner. Numbers like elapsed time, 
used memory, loaded classes, created component objects are included.

To enable set `debug.benchmark = true` in `config.local.ini`

###Enable in Production

It is also possible to enable the benchmark output by adding a KWF_BENCHMARK get parameter to the Url. 
This however only works for a whitelist of remote ip addresses which can be defined in `config.ini` using `debug.benchmarkActivatorIp`.

##Php Extensions

We also reccomend using [xdebug](https://xdebug.org/) php extension for development servers.
