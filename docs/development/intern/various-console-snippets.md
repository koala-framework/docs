#VARIOUS CONSOLE-SNIPPETS

`$ ../library/kwfscripts/update-code`

Does a gpr, makes a backup for your database, updates your update-scripts

###Git grep over multiple Repositories/Directories

`for i in *; do( cd $i; echo $i; git grep -i "_grouping" HEAD ); done`

###scp; Update roco driverscab zip-file

    scp filename vpcms@vpcms.vivid-planet.com:vivid-planet.com/test/ota/roco/cabs scp datei.en 
    
    vpcms@vpcms.vivid-planet.com:test.preview1.vpcms.vivid-planet.com
    
    