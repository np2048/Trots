
# git rebase

Let's say you have a branch 'new' in your repo. You've created that branch to develop a new feature. But after that the *master* branch was updated. In this case you can change the origin commit of your new branch to the newest master commit to get the updates of the master into your working directory in the new branch:

    $ git checkout 'new'
    $ git rebase COMMIT_ID

You can get COMMIT_ID using **git log** command:
    
    $ git checkout 'master'
    $ git log

>Don't use **rebase** on public branches. Instead of this use cherry-pick to pick commits into your branch from another branch.