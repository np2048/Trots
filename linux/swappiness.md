
# swappiness

How to adjust swappiness parameter in Linux.

Set swappiness = 10 in linux edit a config file:

    $ sudo vim /etc/sysctl.conf

Add or update the line:

    vm.swappiness=10

New settings will apply after reboot. To apply it immediately run the following command:

    $ sudo sysctl vm.swappiness=10



