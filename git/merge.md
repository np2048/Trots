
# How to merge two Git branches

Let's say you have two branches in your repo:

1. main 
1. master

To merge **master** -> **main** you have to switch to the first branch and then merge the second one:
    
    $ git checkout main
    $ git merge master

At this point an error may occur:
    
    fatal: refusing to merge unrelated histories

If it happens goto [Merge unrelated histories](merge_histories.md)
