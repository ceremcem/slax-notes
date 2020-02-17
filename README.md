# Slax Notes

1. Change keyboard layout permanently: 

       dpkg-reconfigure keyboard-configuration
    
2. [Disable X by default](https://unix.stackexchange.com/a/264417): 

       systemctl set-default multi-user.target


3. Make modules directly from the apt command: [Forum thread](https://groups.google.com/forum/#!topic/slax-users/5dCZbzfpAjA)

4. Activate modules on the fly, generating iso's with extra modules: https://www.slax.org/customize.php

5. Upgrade the Debian version as usual: `apt-get upgrade && apt-get dist-upgrade`

    > Note: Kernel is not updated, see [#2](https://github.com/ceremcem/slax-notes/issues/2)

6. If `apt-get update` fails with "could not resolve hostname": 

       chmod o+r /etc/resolv.conf
