
# config.fish

The **config.fish** file is intended to store user [aliases](alias.md) and other commands for *Fish shell*. Every time the shell starts it reads and executes commands from this file.

The file is placed at **~/.config/fish** directory. So it's full path is:

    ~/.config/fish/config.fish


## Dynamically reload config without logout

You can reload the configuration file to apply the changes without the need of logout and relogin to *fish*:

    $ source ~/.config/fish/config.fish