
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

## SSH into a VirtualBox machine

To be able to connect into a VirtualBox machine you have to create a port forwarding rule it the settings of the VM instance:

1. Open the VM **Settings - Network**
1. Make sure that an Adapter is enabled
1. Open the **Advanced - Port Forwarding** dialog
1. Add a rule:

    - *Name*: **Rule 1**
    - *Protocol*: **TCP**
    - *Host IP*: **127.0.0.1**
    - *Host Port*: **2222**
    - *Guest IP*: **10.0.2.15** — This is the default value. You can get the actual IP in your VM by calling [ip address](ip.md) command.
    - *Guest Port*: **22**

1. Make sure that *sshd* daemon is [installed and running](#install) in the VM
1. Connect to the VM:

    $ ssh -p 2222 USERNAME@127.0.0.1

    where:

    - **USERNAME** — is your actual user name in the VM

1. Authenticate using your user's password defined in the VM


## Read more

[How to Install, Configure and Enable SSH Service in Linux](https://www.ubuntupit.com/how-to-install-configure-and-enable-ssh-service-in-linux/)

[Easy way to SSH into VirtualBox machine](https://dev.to/developertharun/easy-way-to-ssh-into-virtualbox-machine-any-os-just-x-steps-5d9i)

