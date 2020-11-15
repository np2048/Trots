# Termux terminal emulator for Android

[Termux](https://termux.com/) allows you to use lots of Linux command line tools and utilities on an Android device.

## Install a package

    $ pkg install PACKAGE_NAME

<a name="storage"></a>

## Add access to the device file system

By default *Termux* is using only his own files as a sandbox and it doesn't have any access to the actual files of the host device. But you can grant permissions to the *Termux* to obtain that access. To request file permissions run this command inside *Termux*:

    $ termux-setup-storage

<a name='ssh'></a>

## OpenSSH

You can install *OpenSSH* in *Termux* to be able to connect to your device via SSH.

### Install the server

    $ pkg upgrade
    $ pkg install openssh

<a name='ssh-gen'></a>

### Generate a key-pair on the client

SSH is a secure way to transfer data between separate devices on an insecure network. It is achieved using [asymmetric encryption](https://en.wikipedia.org/wiki/Public-key_cryptography). *Termux* doesn't allow to authorize via SSH using just a password as it is not a secure solution. So, you have to use a **key-file** in order to connect.

Generate a key-pair on a **client** machine (where your ssh **client** is installed):
    
    $ ssh-keygen

At this step you will be asked to enter the user name and a password that will be used for authorization.

It will generate a pair of key-files in your *~/.shh* directory: a **public** one (*id_rsa.pub* if you've choosen RSA encryption algorithm which is used by default) and a private key (*id_rsa*). 

### Transfer the public key-file from client to the SSH server

You have to copy your **public** key to the Android device using any file transfer medium. As it is a public key it doesn't have to be encrypted or protected in any other way. To transfer the file you can use email, a messanger, a USB flash drive and so on.

>Don't transfer your private key anywhere: id_rsa. If you want to setup another SSH client to be able to connect to your Android device you can generate another key pair independently and install new public key on the SSH server just like the first one.

### Add the public key to authorized_keys of the SSH server

Once you have generated the encryption key pair and transferred the public key to the Android device you have to install the key into *OpenSSH*. This is done by adding the contents of the key-file to the *~/.ssh/authorized_keys* file. Those files are in plain text so you can do it using a text editor. Or a Linux command which is more convenient.

Make sure that you've [enabled the storage access](#storage) in *Termux*.

Let's say you copied the key-file to the **Downloads** directory on your Android device. So it must be available in *Termux* at the path:

    ~/storage/downloads/

Make sure that it is so:

    $ cat ~/storage/downloads/id_rsa.pub

Add the contents of the key-file to *authorized_keys*:

    $ cat ~/storage/downloads/id_rsa.pub >> ~/.ssh/authorized_keys

### Start the server

Once it is configured you have to start the server in *Termux* to be able to connect:

    $ sshd

It will enable SSH on port **8022** by default. SSH will be enabled while *Termux* and *sshd* are running.

### Get the device ip address

You have to determine the IP address of your device where the server is running in order to be able to connect to it. You can get the IP in **Termux** using the [ip address](../linux/ip.md) command.

You have to get the IP address of the device in your **local** network. It usually looks like *192.168.1.22* or so.

### Connect to the server

To connect to the *OpenSSH* server running on an Android device from a Linux terminal:

    $ ssh USER@IP -p 8022

where:

- **USER** — user name defined at the [key-pair generation step](#ssh-gen).
- **IP** — the IP address of the Android device in your local network.
- **8022** — the port number which *OpenSSH* is listening on your device (8022 is the default value).

If the connection is OK you will be asked for your password that was set during the [key-pair generation step](#ssh-gen).





