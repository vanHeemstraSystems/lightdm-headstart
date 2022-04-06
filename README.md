lightdm-headstart
# LightDM - Headstart

Based on "How to Install a GUI on Ubuntu" at https://www.servermania.com/kb/articles/ubuntu-server-gui/

Based on "Fixing "System has not been booted with systemd as init system" Error" at https://linuxhandbook.com/system-has-not-been-booted-with-systemd/

1. First you need to check if *systemd* package is installed - ```sudo dpkg -l | grep systemd```.
2. If not then install it by hands ```sudo apt-get install systemd```. But if it does it might be damaged, so you may try to reinstall it ```sudo apt-get install --reinstall systemd```.
3. If the package is installed, even after reinstallation it does not work, list the full path of the files inside this package ```sudo dpkg -L systemd```. Maybe binary files are located in a directory that is not included into *$PATH* variable.

See also "Failed to get D-Bus connection error when trying to start lightdm (desktop)" at https://www.youtube.com/watch?v=L992Ra_uga4

If you see ```can't start systemd - Failed to get D-Bus connection```

Fix it with:

```
$ /etc/init.d/dbus start
```

If you see ```DEBUG: process XXXXX terminated with signal 6```, install SLIM as follows: https://ubuntuhandbook.org/index.php/2013/08/install-use-slim-login-manager-in-ubuntu/

That has no dependencies to systemd and works fine with fast boots. Slim returns to login if starting X fails, lightdm does not.
