
# How to use the TAR utility in Linux command line

*TAR* allows you to glue multiple files and directories into a single file. It may be convenient for future encryption or a transmission.

*TAR* works much faster then *ZIP* because it doesn't do complex processing of the data.

## Options 

You can execute *TAR* operations by calling it in a short syntax or in a long descriptive form. The most usefull options are listed below.

**-f**, --file=FILENAME — name of a TAR archive file. It is used both for input and output files.
**-c**, --create — create *TAR* archive
**-t**, --list — show the list of files inside of an archive
**-x**, --extract — extract files from an archive

## Create new .tar archive

Long form syntax:

    $ tar --create --file=ARCHIVE.tar INPUT_FILE_OR_DIRECTORY

Short syntax:

    $ tar -cf ARCHIVE.tar INPUT_FILE_OR_DIRECTORY

## Extract files from a tar archive

Long form syntax:

    $ tar --extract --file=ARCHIVE.tar

Short syntax:

    $ tar -xf ARCHIVE.tar

## Get file list into an archive

Long form syntax:

    $ tar --list --file=ARCHIVE.tar

Short syntax:

    $ tar -tf pass.tar

## Read more

    $ tar --help
