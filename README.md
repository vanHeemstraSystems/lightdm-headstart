lightdm-headstart
# LightDM - Headstart

Based on "How to Install a GUI on Ubuntu" at https://www.servermania.com/kb/articles/ubuntu-server-gui/

Based on "Fixing "System has not been booted with systemd as init system" Error" at https://linuxhandbook.com/system-has-not-been-booted-with-systemd/

1. First you need to check if *systemd* package is installed - ```sudo dpkg -l | grep systemd.```
2. If not then install it by hands ```sudo apt-get install systemd.``` But if it does it might be damaged, so you may try to reinstall it ```sudo apt-get install --reinstall systemd.```
3. If the package is installed, even after reinstallation it does not work, list the full path of the files inside this package ```sudo dpkg -L systemd.``` Maybe binary files are located in a directory that is not included into *$PATH* variable.
