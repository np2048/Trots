
# How to install flutter on an Arch-based Linux

1. Install flutter package from the AUR:

        $ pamac build flutter
    
    >You have to enable AUR packages in your *pamac* settings

1. Set owner of the flutter working directory:

        $ sudo chown -R USER /opt/flutter
    
    Where:
    
    - **USER** — your current user name

1. Run flutter doctor:

        $ flutter doctor

1. Accept android licences:

        $ flutter doctor --android-licenses

1. Fix the rest of *flutter doctor* issues.

    You can run flutter doctor again to get actual list of requirements to fulfill.