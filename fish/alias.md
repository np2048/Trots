
# Fish shell aliases

You can use **alias** keyword to define aliases for shell commands in *Fish shell*. 

To test the alias you can define it just in the terminal by executing the command:
    
    alias COMMAND='NEW_COMMAND_STRING'

To make the alias permanent you can add the same line into the [config.fish](config.md) file.

    
>Example:

    $ alias ls='lsd -a --group-dirs first'

If you execute this command in a terminal running *Fish shell* the alias will be set. In result every time you'll run 

    $ ls 

fish will actually execute 
    
    $ lsd -a --group-dirs first
