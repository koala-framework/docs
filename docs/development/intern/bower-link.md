#CREATE SYMLINK FOR BOWER FOLDERS

This makes it easier if you make changes und you want to commit these to git.

Here is an example with densajs:

    git clone git@github.com:koala-framework/densajs.git;
    cd densajs;
    bower link;
    cd $webPath;
    bower link densajs;


Replace `$webPath` with the path to your web.