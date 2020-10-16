
# Tor Browser for Linux

## Installation

The easiest way of using the Tor Browser in Linux is to install the [Tor Browser Launcher](https://github.com/micahflee/torbrowser-launcher).

Tor Browser Launcher is included in official Arch repositories, so you can install it with pacman or pamac:

    $ pamac install torbrowser-launcher

If something goes wrong and Tor Browser doesn't start after the installation you can use the **flatpak** as recommended in the official [Tor Browser Launcher](https://github.com/micahflee/torbrowser-launcher#installing) repository:

    $ pamac install flatpak
    $ flatpak install flathub com.github.micahflee.torbrowser-launcher -y

When installation is completed run the *Tor Browser Launcher*:
    
    $ flatpak run com.github.micahflee.torbrowser-launcher

>For convenience you can save this command into a script, for example *~/opt/tor.sh* and start *Tor Browser* by just running that script.

## Default downloads directory location

If you installed **Tor Browser Launcher** from the official Arch repository it will save downloaded files at the following path:

    /home/user/.local/share/torbrowser/tbb/x86_64/tor-browser_en-US/Browser/Downloads/

where:

**x86_64** — your system type id 

**tor-browser_en-US** — your *Tor Browser* version

