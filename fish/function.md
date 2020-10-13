
# Functions in Fish shell

In Fish shell you can define not only [aliases](alias.md) but also functions. You may treat a function as an advanced form of an alias.

Let's say you want to define an alias to run a program in background:
    
    $ ~/opt/GitAhead/GitAhead &

If you just define an alias for that in will return an error because Fish won't know where to put some arguments for this command, so it will put them just at the end and it will lead to an error. To avoid the error you can define a function instead of an alias. 

Edit your [config.fish](config) and add the function:

    function gitahead
        command ~/opt/GitAhead/GitAhead $argv &
    end

Restart Fish and you'll be able to run the program in background with a single command:

    $ gitahead

## Read more

[Functions in Fish shell documentation](https://fishshell.com/docs/current/index.html#functions)