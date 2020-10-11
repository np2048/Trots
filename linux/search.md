
# Linux file search utilities

## Command line

### By name

Search files by name:

    $ find [PATH] [FILENAME]

Default path is current directory.

You can use * in FILENAME as wildcard symbol:
    
    $ find *config*

will return all a list of all files containing *config* anywhere in the name.

### By contents

You can search file contents using the **grep** utility:
    
    $ grep [OPTIONS] PATTERN [FILES]

>Example:

    $ grep -r 'File contents'

will search for string 'File contents' in any files of the current directory

>Example:

    $ grep -r 'File contents' /home

will search for string 'File contents' in any files of the /home directory

## GUI utilities for searching files

- By name and contents: [catfish](https://git.xfce.org/apps/catfish/about/)
- By name: [gnome-search-tool](https://gitlab.gnome.org/Archive/gnome-search-tool)

