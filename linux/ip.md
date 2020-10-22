
# How to determine your own IP address in Linux

## Short version

    $ ip -br address

**-br** option stands for **brief**

More readable result (with colors):
    
    $ ip -br -c address

**-c** option stands for **color**

## Detailed info

Execute in the terminal:

    $ ip address

It will return the list of all network interfaces:

    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc 
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
           valid_lft forever preferred_lft forever
        inet6 ::1/128 scope host 
           valid_lft forever preferred_lft forever
    2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc 
        link/ether 12:3c:57:b3:5h:5a brd ff:ff:ff:ff:ff:ff
    3: wlp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
        link/ether 11:22:33:44:55:66 brd ff:ff:ff:ff:ff:ff
        inet 192.168.1.2/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp4s0
           valid_lft 75743sec preferred_lft 75743sec
        inet6 fe80::44ea:defa:4422:b333/65 scope link noprefixroute 
           valid_lft forever preferred_lft forever

In this example the IP address will be

    192.168.1.2

The *24* that follows it is the subnet mask:

inet **192.168.1.2**/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp4s0

## Read more

[How to Find IP Address in Linux Command Line](https://linuxhandbook.com/find-ip-address/)