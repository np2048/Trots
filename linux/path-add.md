
# How to update your PATH variable in Linux

How to add a path to the PATH variable for your Linux user profile.

## Bash

If you are using the [Bash](https://www.gnu.org/software/bash/) shell then edit your *~/.bashrc* file using a text editor:

    $ nano ~/.bashrc

Go to the last line and add a string:

    export PATH=/the/path/you/need/:$PATH

Where:
- /the/path/you/need/ — is the path that you need to add to the PATH variable

In order to apply the changes run the same command in the terminal:

    export PATH=/the/path/you/need/:$PATH

## Fish

[Fish shell](https://fishshell.com) allows you to permanently update your path variable just by executing a  single command in the terminal. Refer to the [fish/path.md](../fish/path.md) trot.



