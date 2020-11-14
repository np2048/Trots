
# Android Debug Bridge

## adb devices no permissions;

    $ lsusb

It will return list of all the devices connected to USB:

    Bus 001 Device 002: ID 05c6:9025 Qualcomm, Inc.
    Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
    ...

**Qualcomm** is one of the most common names of controllers used in android phones. 

**05c6:9025** is the ID that we will need in the next step.

**05c6** First 4 digits is the idVendor. We will need only this part.

    sudo vim /etc/udev/rules.d/51-android.rules 

Add one rule for each unique idVendor:

    SUBSYSTEM=="usb", ATTR{idVendor}=="05c6", MODE="0666", GROUP="plugdev"

Reboot the system to apply the changes. If you don't want to reboot the whole system you may reboot *udev* only.