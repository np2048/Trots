
# Pass : The standart Unix password manager

[Pass](https://www.passwordstore.org/) is a simple, neat and transparent password manager for Linux.

Before you start using *pass* you have to [initialize a gpg keychain](gpg.md#init). It is also recommended to [create a dedicated subkey](gpg.md#subkey) and use it only with *pass*.

<a name='init'></a>

## Initialization
    
    $ pass init KEY_ID

You can get the KEY_ID as described in [gpg trot](gpg.md#list)

## Add a password

You can organize your password files in a common directory structure:

    $ pass insert [SUBDIRECTORY/]FILENAME
    Enter password for test: 
    Retype password for test:

## Add multiline data to store

    $ pass insert -m [SUBDIRECTORY/]FILENAME
    Enter contents of Business/cheese-whiz-factory and press Ctrl+D when finished:

**-m** multiline

## Generate password and store it:

    $ pass generate -c [SUBDIRECTORY/]FILENAME [LENGTH]

**-c** copy new password to the clipboard

## List existing passwords in store

    $ pass

Or
    
    $ pass ls

## Get password

    $ pass [SUBDIRECTORY/]FILENAME

Add **-c** option to copy password to the clipboard instead of showing it in the terminal:
    
    $ pass -c [SUBDIRECTORY/]FILENAME

## Delete password

    $ pass rm [ --recursive, -r ] [ --force, -f ] [SUBDIRECTORY/]FILENAME

## Copy password into another subdirectory in the storage

    $ pass cp [ --force, -f ] OLD_PATH NEW_PATH

## Move password into another subdirectory in the storage

    $ pass cp [ --force, -f ] OLD_PATH NEW_PATH


## Manually decrypt a password file

You can manually decrypt a password file from the storage using [gpg](gpg.md#decrypt):
    
    $ gpg -d ~/.password_store/[SUBDIRECTORY/]FILENAME

## Read more

[Man page with lots of examples](https://git.zx2c4.com/password-store/about/)

[Quickstart guide on Pass official website](https://www.passwordstore.org/)

[Pass in Arch wiki](https://wiki.archlinux.org/index.php/Pass)

