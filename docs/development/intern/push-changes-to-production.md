#HOW TO PUSH CHANGES TO PRODUCTION SERVER

##WEB HAS NO PRODUCTION BRANCH

If web is not yet "online online" you can push changes into master and export that directly to production:

`vps export --server=production (exp)`

##WEB HAS PRODUCTION BRANCH

There are 3 ways to push changes online. Choose wisely.

WARNING: **changes to production server will clear caches**


##1. update to production server (multiple commits)
 
 (master branch)
 
    git add ....
    git commit
    git push
    
.

    vps export --server=test (ext) 
    
    
###verify changes on test server, if ok:

`vps go-online`


##2. Small update to production server (single, small commit)

(master branch)

    git add ....
    git commit
    git push
    
.

    vps export --server=test (ext)
    
##3. Update to production server without testing on test server (single, small commit)   

    git checkout production (gc production)
    git add ....
    git commit
    git push
    
.


    vps export --server=production (exp)
    
###change is now online, backport to master

    git checkout master (gc master)
    git cherry-pick production #picks only the last commit, production^ for second last (gcp production)
    git push