#GIT BASICS

###Initial global Config

    git config --global user.name "John Doe"
    git config --global user.email johndoe@example.com
    git config --global color.ui true
    git config --global url.ssh://git.vivid-planet.com/.insteadof=git://git.vivid-planet.com/
    
    
####To use a different user name for connecting to git.vivid-planet.com:

    git config --global url.ssh://johndoe@git.vivid-planet.com/.insteadof=ssh://git.vivid-planet.com/
    
    
####or add the following to `~/.ssh/config`:

    Host git.vivid-planet.com
        User johndoe

###Get changes from git server

    git pull --rebase (gpr)
    vps update

###Commit changes to git server

    git status (st)
    git diff (gd)
    git add filenames
    git commit
    git push