#NODEJS + NPM

Koala Framework uses various [nodejs](https://nodejs.org/en/) based tools during build. It is **not required on the production server**.

npm and node must be installed and in your path.

###Windows

On Windows you can use the NodeJS [Windows installer](https://nodejs.org/download/) wich also installs npm.

###Bower

If bower is not installed globally composer install will automatically install it local to your project. On Windows this can cause issues with too long filenames, so we recommend installing bower globally:

`npm install -g bower`