
# File mods

You can change permissions of a file or a directory in Linux using *chmod* command:

    $ chmod MODE FILE

You can define MODE in numeric format or in a [symbolic format](#symbolic). 

Using symbolic format you can modify existing permissions, not just reset them.

<a name='numeric'></a>

## Numeric modes

    Value in  Corresponding
    Mode      Mode Bit
    
              The file's owner:
     400      Read
     200      Write
     100      Execute/search
    
              Other users in the file's group:
      40      Read
      20      Write
      10      Execute/search
    
              Other users not in the file's group:
       4      Read
       2      Write
       1      Execute/search

The resulting MODE value is a sum of it's bits. For example: 4+2 = 6 and a six means read and write permissions combined.  

Common values:

- 777 — read + write + execute permissions for all users
- 666 — read + write permissions for all users
- 700 — rwx permissions for owner and no permissions for the rest of all users

<a name='symbolic'></a>

## Symbolic mode

### Format:

    users operation permissions

### Where:

- users — one or more of the following acronyms:
    - u — owner  
    - g — owners group
    - o — other users
    - a — all of above
- operation:
    * \+ — add permissions
    * \- — remove permissions
    * = — set the permissions defined next and remove all other permissions
- permissions:
    - r — read
    - w — write
    - x — execute

### Examples

- a=rwx — all permissions for all users
- a=rw — read and write permissions for all users
- u=rw — read and write permissions for owner and no permissions for the rest of users

## Read more
[File permissions](https://www.gnu.org/software/coreutils/manual/html_node/File-permissions.html#File-permissions)
[Numeric modes](https://www.gnu.org/software/coreutils/manual/html_node/Numeric-Modes.html#Numeric-Modes)
[Symbolic modes](https://www.gnu.org/software/coreutils/manual/html_node/Symbolic-Modes.html#Symbolic-Modes)
[Setting permissions](https://www.gnu.org/software/coreutils/manual/html_node/Setting-Permissions.html#Setting-Permissions)