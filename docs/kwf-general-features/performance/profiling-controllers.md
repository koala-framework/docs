#PROFILING CONTROLLERS

####Short tutorial how to use xdebug to profile a controller:

1. The first step is to identify slow controllers e.g. via firebug.
2. Get the concrete url including parameters  (in firebug there's a right-click option: "Copy Location 
    with Parameters") and append &XDEBUG_PROFILE.
3. Request the url to generate a trace-file which can be used to check for bottleneck. 
    (check [http://xdebug.org/docs/profiler](https://xdebug.org/docs/profiler) for more information)
4. You can find the file at `/tmp` named `cachegrind.out.NUMBER.` Open this file with software like kcachegrind and look for the problem.
5. Do performance boosting
6. Repeat steps 3 till 5 until you are satisfied with the speed of your code