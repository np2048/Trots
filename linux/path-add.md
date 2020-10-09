
# How to update your PATH variable in Linux

How to add a path to the PATH variable for your Linux user profile.

## Bash

If you are using the [Bash](https://www.gnu.org/software/bash/) shell then edit your *~/.bashrc* file.

Go to the last line and add a string:

    export PATH=/the/path/you/need/:$PATH

Where:
- /the/path/you/need/ — is the path that you need to add to the PATH variable

In order to apply the changes run the same command in the terminal:

    export PATH=/home/dave/work:$PATH

## Fish

[Fish shell](https://fishshell.com) allows you to permanently update your path variable just by executing a  single command in the terminal:

    $ set -U fish_user_paths /the/path/you/need/ $fish_user_paths

Where:
- /the/path/you/need/ — is the path that you need to add to the PATH variable

Full guide dedicted to this topic on the official *Fish shell* site:
[https://fishshell.com/docs/current/tutorial.html#path](https://fishshell.com/docs/current/tutorial.html#path)





    