
# VirtualBox

<a name='ssh'></a>

## SSH into virtual machine from the host

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

1. Make sure that *sshd* daemon is [installed and running](ssh.md#install) in the VM
1. Connect to the VM:

    $ ssh -p 2222 USERNAME@127.0.0.1

    where:

    - **USERNAME** — is your actual user name in the VM

1. Authenticate using your user's password defined in the VM