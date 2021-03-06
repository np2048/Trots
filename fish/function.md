
# Functions in Fish shell

In *Fish shell* you can define not only [aliases](alias.md) but also functions. You may treat a function as an advanced form of an alias.

Let's say you want to define an alias for [git GUI client](../git/gui.md) and you want to be able to start it from the terminal and run in the background:
    
    $ ~/opt/GitAhead/GitAhead &

If you just define an alias for that in will return an error because *Fish* won't know where to put the arguments for this command, so it will put them just at the end and it will lead to an error. To avoid the error you can define a function instead of an alias. 

Edit your [config.fish](config.md) and add the function:

    function gitahead
        command ~/opt/GitAhead/GitAhead $argv &
    end

Restart *Fish* and you'll be able to run the program in background with a single command:

    $ gitahead

## Read more

[Functions in Fish shell documentation](https://fishshell.com/docs/current/index.html#functions)