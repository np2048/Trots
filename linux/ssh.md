
# SSH

Secure Shell (SSH) allows to securely connect to other machines over an unsecure network.

To enable SSH you have to install an SSH server. Some popular SSH servers:

- [OpenSSH](https://wiki.archlinux.org/index.php/OpenSSH) — Premier connectivity tool for remote login with the SSH protocol
- [Dropbear](https://en.wikipedia.org/wiki/Dropbear_(software)) — Lightweight SSH server. The command-line ssh client is named *dbclient*
- [lsh](https://en.wikipedia.org/wiki/Lsh) — GNU SSH implementation
- [TinySSH](https://tinyssh.org/) — a minimalistic SSH server which implements only a subset of SSHv2 features.


<a name='install'></a>

## Installation on Linux

OpenSSH installation on an Arch-based Linux.

    $ sudo pacman -S openssh

Check the state of the OpenSSH Daemon:

    $ sudo systemctl status sshd 

Start the OpenSSH Daemon:

    $ sudo systemctl start sshd 

Additional commands that may be usefull:

    $ sudo systemctl stop sshd 
    $ sudo systemctl enable sshd 
    $ sudo systemctl disable sshd
    $ sudo systemctl restart sshd

### Configuration

To configure the SSH service script on Arch Linux, you need to open the configuration file from the */etc/ssh/* directory.

    $ man sshd_config / config files 
    $ sudo nano /etc/ssh/sshd_config

## Connect to a server via SSH

    $ ssh USER@IP -p PORT

where:

- **USER** — login
- **IP** — ip address of the remote host
- **PORT** — port number of the SSH server on the remote host (default: 22)

When you connect to a server for the first time SSH will ask you to accept it's footprint:

    The authenticity of host '[192.168.1.1]:8022 ([192.168.1.1]:8022)' can't be established.
    ECDSA key fingerprint is SHA256:A123/1231092381KJDLFJS09342034JDSLF.
    Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
    Warning: Permanently added '[192.168.1.1]:8022' (ECDSA) to the list of known hosts.

If you confirm then the server's footprint will be added to your local *.ssh/known_hosts* list. If the server will be reinstalled in the future on the same ip so it's footprint will be changed and you'll get the following error if you try to connect again from the same client:

    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    @    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
    Someone could be eavesdropping on you right now (man-in-the-middle attack)!
    It is also possible that a host key has just been changed.

If you trust the remote host and you are pretty sure that everything is OK so you can delete the old footprint from your *.ssh/known_hosts* file and connect again to accept new footprint.

## Transfer files

You can transfer files securely via SSH using *scp* command:

    $ scp [-P PORT] FILENAME USER@REMOTE_IP:REMOTE_DIRECTORY

>Note that you can only copy files to a directory where the username you specified has write permissions.

Copy files recursively:
    
    $ scp -r * pragmalin@debianvm:/home/pragmalin

Example:

    $ scp wordpress-5.4.2.tar.gz pragmalin@debianvm:/home/pragmalin

## SSH into a virtual machine

You can login into a virtual machine using SSH and configure it from your local environment:

[VirtualBox](virtual-box.md#ssh)

[virt-manager](virt-manager.md#ssh)

## SSH into an Android device

You can [configure an SSH server on an Android device](../android/ssh.md).

### SFTP

Once you have installed SSH server you can connect to it and transfer files using an FTP client as [Filezilla](https://filezilla-project.org/) in SFTP protocol.

## Read more

[How to Install, Configure and Enable SSH Service in Linux](https://www.ubuntupit.com/how-to-install-configure-and-enable-ssh-service-in-linux/)

[Easy way to SSH into VirtualBox machine](https://dev.to/developertharun/easy-way-to-ssh-into-virtualbox-machine-any-os-just-x-steps-5d9i)

[How to copy files via SSH](https://www.pragmaticlinux.com/2020/07/how-to-copy-files-via-ssh/)