
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

## SSH into a virtual machine

You can login into a virtual machine using SSH and configure it from your local environment:

[VirtualBox](virtual-box.md#ssh)



## Read more

[How to Install, Configure and Enable SSH Service in Linux](https://www.ubuntupit.com/how-to-install-configure-and-enable-ssh-service-in-linux/)

[Easy way to SSH into VirtualBox machine](https://dev.to/developertharun/easy-way-to-ssh-into-virtualbox-machine-any-os-just-x-steps-5d9i)

