
# Mount a partition in Linux

If you are to mount a partition for the first time then you may need to [create a mount point](#mountpoint) first. When it's done you can actually mount the filesystem:

    $ sudo mount /dev/sda5 /mnt/sda5

Where:

**sda5** is an actual partition. 

**/mnt/sda5** is the mount point.

<a name="mountpoint"></a>

## Create a mount point

Mount point is just a directory that is used to mount devices which contain valid filesystems. So, if you want to create a mount point at */mnt* just run a mkdir command:

    $ cd /mnt
    $ sudo mkdir sda5

## Read more

[Create and mount filesystems in Linux](https://www.linuxsysadmins.com/create-and-mount-filesystems-in-linux/)