#INSTALL ON VIRTUAL MACHINE

###Requirements:

* [Vagrant](https://www.vagrantup.com/downloads.html)
* VirtualBox (or any other provider vagrant supports)

####To create a virtual machine for running kwf-cms-demo execute the following:

    #clone kwf-vagrant
    git clone git://github.com/koala-framework/kwf-vagrant.git
    cd kwf-vagrant
     
    #clone kwf-cms-demo (replace with your repository) into app subfolder
    git clone git://github.com/vivid-planet/kwf-cms-demo.git app
     
    vagrant up
    
    
By default this will create a new initial database.

Optionally you can import an existing database dump into the new virtual machine, to do so create the following:

`app.sql`: mysqldump of database to import

`uploads`: uploads directory to import

You now have a fully running instance of the app running in the virtual machine, access it thru the browser:

`http://localhost:8080/`

To execute cli scripts connect to the virtual machine using vagrant ssh.