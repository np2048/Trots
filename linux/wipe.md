
# How to securely delete files on Linux

## Don’t Do This With SSD’s

These techniques are for HDD only.  

It won't work with SSD and will just cause some wear. Try to find an utility for data wiping by the manufacturer of your storage device.


## Directory

    $ wipe -rf /PATH/TO/CATALOG

>Maybe you'll have to install the **wipe** utility first.

## Single file

    $ shred -uz somefile.txt

### Syntax:

    $ shred [OPTIONS] FILENAME

### Important options:

**-u**

Actually delete the file. Without this argument it will just rewrite the file with fake data.

**-n NUMBER** 

Define the number of file rewriting with 0 and 1 data. This parameter significantly affects the speed of the operation. Default value is 3.

**-z, --zero**

Add a final overwrite with zeros to hide shredding.

**-v, --verbose**

Show progress.

### Example of typical usage:
    
    $ shred -uvz somefile.txt

    $ shred -uvz -n 2 somefile.txt

## Multiple files
    
You can use * wildcard charachter in the filename with *shred*.

This will delete all *.txt* files in the current directory:
    
    $ shred -uz *.txt

All files in a directory (not recursively):
    
    $ shred -uz tmp/*

## Read more

[How to Securely Delete Files on Linux](https://www.howtogeek.com/425232/how-to-securely-delete-files-on-linux/)



