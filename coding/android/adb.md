
# Android Debug Bridge

## adb list connected devices

When you connect a device to USB it should be detected automatically and appear in adb connected devices list:

    $ adb devices

If you see a warning: [no permissions](#permissions) near to the device ID in the list, [solve this issue as described below](#permissions).

If you connect a device but it's not in the list make sure that you have enabled debug mode and adb on the device.


## adb transfer file to connected device

Save a local file to device's MicroSD card:

    $ adb push FILENAME /sdcard1/

Save a local file to device's internal SD card:

    $ adb push FILENAME /sdcard/

## adb shell

You can execute shell commands on the device as root if you connect via adb:

    $ adb shell

To terminate the shell session type:

    # exit

To execute a single shell command:

    $ adb shell ls /

Where: 
  
- **ls /** is the command to be executed

<a name="permissions"></a>

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