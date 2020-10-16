# How to add a directory into the $PATH variable in Fish shell

[Fish shell](https://fishshell.com) allows you to permanently update your path variable just by executing a  single command in the terminal:

    $ set -U fish_user_paths /THE/PATH/YOU/NEED/ $fish_user_paths

Where:
- /THE/PATH/YOU/NEED/ — is the path that you need to add to the PATH variable

Full guide dedicated to this topic on the official *Fish shell* site:
[https://fishshell.com/docs/current/tutorial.html#path](https://fishshell.com/docs/current/tutorial.html#path)