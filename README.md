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

## Display Managers

For Ubuntu 16.10+ the default is GDM, for 16.04 and earlier the default is LightDM.

See https://askubuntu.com/questions/641642/gui-does-not-start

See also "How to start GUI from command line?" at https://askubuntu.com/questions/168736/how-to-start-gui-from-command-line

## Windows Subsystem for Linux

Start by clicking Start and entering "turn windows". The Turn Windows Features on or off item should be displayed. Then scroll down to Windows Subsystem for Linux.

Restart Windows.

Open the Windows Store, search for Linux, and install Ubuntu.

Once complete, click Launch from within the Windows Store or open it from the Start menu.

On the first run, you'll be prompted to input a username and password to create a user account.

Run these commands

sudo apt update

sudo apt upgrade

While this upgrade is running, head to Sourceforge to download and install the VcXsrv Windows X Server utility (https://sourceforge.net/projects/vcxsrv/files/latest/download).

Install the Linux desktop. Many Linux desktop environments (https://www.makeuseof.com/tag/best-linux-desktop-environments/) are available but to keep things simple we'll install LXDE:

sudo apt install lxde

Following installation of LXDE, input these commands:

export DISPLAY=:0

export LIBGL_ALWAYS_INDIRECT=1

Open the Xlaunch tool, and choose One large window, and Display number: 0

Click Next on the following pages until the end.

Start the LXDE desktop environment

startlxde

Steps to start Ubuntu / LXDE every time.

Open Ubuntu

Enter these commands:

export DISPLAY=:0

export LIBGL_ALWAYS_INDIRECT=1

Open the Xlaunch tool, and choose One large window, and Display number: 0

Click Next on the following pages until the end.

Start the LXDE desktop environment

startlxde

Note that it is not possible to damage Windows 10 using the Linux environment. Any commands you input will damage only the Windows Subsystem for Linux and the chosen operating system. Windows 10 will remain safe and secure.

*Sources*:

- How to Get the Linux Bash Shell on Windows 10 (https://www.makeuseof.com/tag/linux-bash-shell-on-windows-10/)

- How to Run a Linux Desktop Using the Windows Subsystem for Linux (https://www.makeuseof.com/tag/linux-desktop-windows-subsystem/)

- 5 Linux Distros You Can Install in Windows Subsystem for Linux (https://www.makeuseof.com/linux-distros-for-windows-subsystem-for-linux/)
