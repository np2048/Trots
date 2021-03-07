
# Swap partition in Linux

How to turn on swap using a swap partition in Linux.

In order to activate swap in Linux you have to create and turn on a swap partition or a swap file.

Also you have to [adjust the swappiness parameter](swappiness.md).

## Get the list of the swap partitions active at the moment

    $ swapon -s

## Get the swap partition UUID

You can use a GUI tool GParted to get the list of all patitions, create, delete, move, resize and so on.

To get the UUID of a partition right click on it and choose *Information* in the dropdown menu.

## Assign a partition as a swap partition

Run a command:

    $ swapon -U UUID

Where:

* UUID — is the actual UUID of yours swap partition

Example:

    $ sudo swapon -U a1b23cde-45f6-7890-ab12-3c4d567890e1

This will activate swap only for the current session till next reboot. To make the changes permanent you have to add a line to your /etc/fstab file.

## Add swap partition to fstab

Edit /etc/fstab file as root:

    $ sudo vim /etc/fstab

Add a line at the end using the actual UUID of the swap partition in your system:

    UUID=a1b23cde-45f6-7890-ab12-3c4d567890e1    none    swap    sw    0    0

That's it.



