
# How to mount a Nextcloud to a Linux filesystem

## Install davfs

You have to install **davfs2** package support into your system to be able to mound cloud filesystems:

    $ sudo pacman -S davfs2


## Create a mount point

    $ cd /mnt
    $ sudo mkdir /cloud

More info: [../linux/mount.md#mountpoint](../linux/mount.md#mountpoint)

## Set mount point permissions
    
    $ sudo chown user cloud
    $ chmod 600 cloud

More info: [../linux/chmod.md](../linux/chmod.md)

<a name='url'></a>

## Get WebDAV URL of your cloud

Login into your Nextcloud in a browser tab and click **Settings** in the left-bottom corner of the page.

You'll see WebDAV URL in an edit box.

## Add cloud fs to the fstab

    $ sudo nano /etc/fstab

Add a line at the end of file:

    "WEBDAV_URL /mnt/cloud davfs user,rw,auto 0 0

Where:

- WEBDAV_URL — see the [WebDav step](#url)
- /mnt/cloud — mount point where you want your cloud to be mounted at
- davfs user,rw,auto 0 0 — you can leave this part unchanged, it just works as it is

<a name='access'></a>

## Setup access for your device in the Nextcloud settings

Open your Nextcloud in a browser tab and navigate to **USERNAME** (in the top-right corner of the main page)** - Settings - Security : Devices & sessions**.

Enter your device name and click **Create new app password**.

Copy the password and click **Done**.

## Add cloud access credentials to your secret file

Create the secret file if it doesn't exist:

    $ cp  /etc/davfs2/secrets ~/.davfs2/secrets

Open *~/.davfs2/secrets* file in a text editor and add a line at the end of file:

     WEBDAV_URL EMAIL PASSWORD

Where:

- WEBDAV_URL — see the [WebDav step](#url)
- EMAIL — your e-mail used for a registration in a Nextcloud server
- PASSWORD — see the [Setup access](#access) step

## Mount the file system

That's it. If you've done the previous steps correctly than you'll be able to mount your clod data into the Linux file system:
    
    $ mount /mnt/cloud

## Read more

[Accessing Nextcloud files using WebDAV](https://docs.nextcloud.com/server/15/user_manual/files/access_webdav.html)



