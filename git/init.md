
# git init

When you already have some files in a directory and you want to create a new repository including them without any moving of the files:

    $ git init 
    $ git add .
    $ git commit -m 'Start'

**Login to GitHub or other service and create a repository.**
https://github.com/new

Or use the [gh command line tool](create.md#gh).

Attach new remote repository to local:
    
    $ git remote add https://github.com/USERNAME/REPOSITORY
    $ git pull
    $ git push --set-upstream origin master

If everything is OK you'll be in the **master** branch now. To merge the **master** branch with the **main** branch goto: [Merge](merge.md). 