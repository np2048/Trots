
# git log

Git log shows the commit history.

    $ git log

Usually it is used to get the id of a commit needed for other commands.

<a name="oneline"></a>

## one line

To make **git log** output the log in a neat and compact form:
    
    $ git log --oneline

<a name="reflog"></a>

## reflog

You can use **git log** to output the history including cancelled commits during [git reset](reset.md) command:

    $ git log --reflog

>It's more convenient to use [git reflog](reflog.md) command for this purpose.

