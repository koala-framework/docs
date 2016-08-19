#GIT ADVANCED

###Checkout production branch (the first time)

    # for web    
    git checkout -b production origin/production
     
    # for kwf
    git checkout -b production/webname origin/production/webname
    
    
###apply commit to other repository

   
    
    git format-patch HEAD~1 #creates patch file for last 1 commit
       mv 0001-* ../otherrepo #move patch file to where you want to apply patch
       cd ../otherrepo
       git am --3way 0001-*
        
       # if patch causes conflict apply manually and fix conflict
       git apply --verbose --reject $PATCHNAME
        
       # cleanup
       rm 0001-*
        
       # push changes
       git push    



###Create Public Branch

    git branch foo
    git checkout foo
    git branch --set-upstream origin origin/foo
    git push
    
    
#Show only not cherry-picked commits

    git log --cherry-pick --left-only master...production