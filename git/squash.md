
# git squash

Let's say you have made lots of commits during the development process and now you want to push your new feature to the master branch. You may want to combine the last commits into one to keep clear and readable the commits history.

You can do it using [get reset --soft](reset.md#soft) command:
    
    $ git reset --soft COMMIT_ID
    $ git commit -m 'New squashed commit'

After you run this commands all the commits between COMMIT_ID and the last commit in the active branch will turn into a single commit.

>You can get desired COMMIT_ID value using **git log** command.