
# Pass : The standart Unix password manager

[Pass](https://www.passwordstore.org/) is a simple, neat and transparent password manager for Linux.

Before you start using *pass* you have to [initialize a gpg keychain](gpg.md#init). It is also recommended to [create a dedicated subkey](gpg.md#subkey) and use it only with *pass*.

<a name='init'></a>

## Initialization
    
    $ pass init KEY_ID

You can get the KEY_ID as described in [gpg trot](gpg/list.md)

## Dedicated keys for certain subdirectories

You can assign a separate key to a directory inside of your *.password_store*:

    $ pass init -p SUBDIRECTORY KEY_ID

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

## Backup and sync passwords using GitHub

    $ pass git init

This will create a common git repository inside the password storage directory. You can execute any git commands inside of this directory:

    $ cd ~/.password-store

In order to be able to upload files to the GitHub you have to [create a remote repository](../git/create.md#gh) and define remote origin for the current branch:

    $ git remote add https://github.com/USERNAME/REPOSITORY

Once it's done you can execute common *git push* and *git pull* commands to upload and download new information about the passwords to and from the repository.

Upload all new data to *GitHub*:

    $ git add .
    $ git commit -m 'Some password changes'
    $ git push

Check for changes on the remote repository and apply them to local files:

    $ git pull

## Init from a github repository

    $ cd ~
    $ git clone https://github.com/USERNAME/REPOSITORY/ .password-store

## Manually decrypt a password file

You can manually decrypt a password file from the storage using [gpg](gpg/decrypt.md):
    
    $ gpg -d ~/.password_store/[SUBDIRECTORY/]FILENAME

## Read more

[Man page with lots of examples](https://git.zx2c4.com/password-store/about/)

[Quickstart guide on Pass official website](https://www.passwordstore.org/)

[Pass in Arch wiki](https://wiki.archlinux.org/index.php/Pass)

