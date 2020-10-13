
# Mount a partition in Linux

If you are to mount a partition for the first time then you may need to [create a mount point](#mountpoint) first. When it's done you can actually mount the filesystem:

    $ sudo mount /dev/sda5 /mnt/sda5

Where:

**sda5** is an actual partition. 

**/mnt/sda5** is the mount point.

<a name="mountpoint"></a>

## Create a mount point

Mount point is just a directory that is used to mount devices which contain valid filesystems. So, if you want to create a mount point at */mnt* just run a *mkdir* command:

    $ cd /mnt
    $ sudo mkdir sda5

It you want to allow other users to read and write to the mounted filesystem you should add some permissions.

Add read permissions for everyone:
    
    $ sudo chmod a+r sda5/

Add write permissions for everyone:
    
    $ sudo chmod a+w sda5/

## Read more

[Create and mount filesystems in Linux](https://www.linuxsysadmins.com/create-and-mount-filesystems-in-linux/)