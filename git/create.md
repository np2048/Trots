
# Git create a repositoy from command line

    git init 
    git add .
    git commit -m 'Start'

**Login to Github or other service and create a repository.**
https://github.com/new

Attach new remote repository to local:
    
    git remote add https://github.com/YOUR_LOGIN/NEW_REPOSITORY
    git pull
    git push --set-upstream origin master

If everything is OK you'll be in the master branch now. To merge the **master** branch with the **main** branch goto: [Merge](merge.md). 
