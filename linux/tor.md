
# Tor Browser for Linux

The easiest way of using the Tor Browser in Linux is to install the [Tor Browser Launcher](https://github.com/micahflee/torbrowser-launcher).

Tor Browser Launcher is included in official Arch repositories, so you can install it with pacman or pamac:

    $ pamac install torbrowser-launcher

If something goes wrong and Tor Browser doesn't start after the installation you can use the **flatpak** as recommended in the official [Tor Browser Launcher](https://github.com/micahflee/torbrowser-launcher#installing) repository:

    $ pamac install flatpak
    $ flatpak install flathub com.github.micahflee.torbrowser-launcher -y

When installation is completed run the *Tor Browser Launcher*:
    
    $ flatpak run com.github.micahflee.torbrowser-launcher

>For the convenience you cat save this command into a script, for example *~/opt/tor.sh* and start *Tor Browser* by just running that script.

