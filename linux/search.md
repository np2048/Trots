
# Linux file search utilities

## Command line

### By name

Search files by name:

    $ find [PATH] -name 'FILENAME'

Default path is current directory.

You can use * in FILENAME as wildcard symbol:
    
    $ find -name '*config*'

will return all a list of all files containing *config* anywhere in the file name.

The *find* utility is able to filter files by a variety of parameters, not only filename. And also it is able to execute some commands to bulk process the files. Refer to --help and *man* to get more detailed info:

    $ find --help
    $ man find

### By contents

You can search file contents using the **grep** utility:
    
    $ grep [OPTIONS] PATTERN [FILES]

>Example:

    $ grep -r 'File contents'

will search for string 'File contents' in all files of the current directory

>Example:

    $ grep -r 'File contents' /home

will search for string 'File contents' in all files of the /home directory

>More about grep: [https://www.techrepublic.com/article/10-ways-to-use-grep-to-search-files-in-linux/](https://www.techrepublic.com/article/10-ways-to-use-grep-to-search-files-in-linux/)

## GUI utilities for searching files

- By name and contents: [catfish](https://git.xfce.org/apps/catfish/about/)
- By name: [gnome-search-tool](https://gitlab.gnome.org/Archive/gnome-search-tool)

## Read more

[Findutlis documentation on GNU.org](https://www.gnu.org/software/findutils/)