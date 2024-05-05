# Setting Up a New Cabinet

## Table of Contents
- [Summary](#summary)
- [Hardware](#hardware)
- TODO: Add more headings to TOC

## Summary

The Devcade project should theoretically run on just about any linux distro if set up properly. Our distro of choice has been the latest Debian.

In the past, we have taken advantage of Debian's preseed functionality to install the OS, and set up our launcher, [devcade-onboard](https://github.com/computersciencehouse/devcade-onboard). This (now outdated) preseed file is located in the devcade-onboard git repo and also hosted at https://devcade.csh.rit.edu/preseed and is based off of the file given as an example in the [Debian Wiki](https://wiki.debian.org/DebianInstaller/Preseed). While it is outdated now, it may be used again in the future to partially or completely automate these steps.

The setup is reletively simple to perform manually as well. It mostly consists of the following:
- Install an OS
- Install necessary packages and runtimes
- Cloning some Git repos
- And doing a bit of configuration

## Hardware

Devcade and it's games ought to run on nearly any x86 hardware released in the last 10 years, but we recommend the following as a starting point:

**CPU:** Intel Core i5 (5th gen or better)

**RAM:** 8GB

**GPU:** N/A

This should act as a modest starting point and depending on the games you run on your cabinet or those that users are making for your cabinet, you can always upgrade these later as needed.

---

Install Debian 12 (Bookworm)
- Set the hostname to `dcu.csh.rit.edu`
- Set the password for the `root` user
- Create a user named `devcade` and set a password
- When you get to disk configutation, select the option to use the entire disk, and put everythin in one partition
- Under software selection, make sure only the only selected options are `SSH Server` and `Basic system utilities`

Once the system is installed, log in to the root user, and install `sudo` through apt.

Once that is installed, add the `devcade` user to the sudoers file.

At this point, the `devcade` user should have permissions to use `sudo`. Once this is the case, log in to the `devcade` user. You should be able to complete the rest of the setup from there.

Install the following packages through apt:
- git
- xterm
- openbox
- compton
- curl
- vim
- gzip
- build-essential
- pkg-config
- libglib2.0-dev
- xorg
- libusb-dev
- meson
- cmake
- libnfc-dev
- libfreefare-dev
- pamixer

Run the following commands to install the dotnet SDK

```
wget https://packages.microsoft.com/config/debian/12/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-6.0
```

Run the following command to install rustup. If it asks you to choose an installation option, select the default option.

```curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh```

Once that is installed, run this command to update the path: ```. "$HOME/.cargo/env"```
Make sure you include the leading dot in the command.

Set the default channel to nightly with `rustup default nightly`

Clone this repo `https://github.com/Mstrodl/flatpak.git`

Follow the guide here to build flatpak https://github.com/Mstrodl/flatpak/blob/main/CONTRIBUTING.md

Run these commands:
```
curl -L https://github.com/nfc-tools/libfreefare/releases/download/libfreefare-0.4.0/libfreefare-0.4.0.tar.bz2 > libfreefare-0.4.0.tar.bz2
bzip2 -d libfreefare-0.4.0.tar.bz2
```

Clone the onboard repo from here: `https://github.com/ComputerScienceHouse/devcade-onboard`

Run the following series of commands:
```
cd devcade-onboard/onboard/backend
cargo build
cd .. 
./build.py
LD_LIBRARY_PATH=/usr/local/lib
```

From the homedir, copy the .xinitrc from devcade-onboard to the homedir

Copy .env.template to .env, and get values for the fields from an RTP or a Devcade Admin

The last step will be to set up volume controls. In order to configure volume controls, the system running devcade must have buttons that send `XF86AudioRaiseVolume` and `XF86AudioLowerVolume`, with an optional mute button that sends `XF86AudioToggleMute`


Run the following command to move to the proper directory: `cd /home/devcade/.config/openbox`

If any of the directories in that path do not already exist, create them.

Once in that directory, add the following code to `rc.xml`:
```
<keybind key="XF86AudioRaiseVolume">
  <action name="Execute">
    <command>pamixer -i 1</command>
  </action>
</keybind>
<keybind key="XF86AudioLowerVolume">
  <action name="Execute">
    <command>pamixer -d 1</command>
  </action>
</keybind>
<keybind key="XF86AudioMute">
  <action name="Execute">
    <command>pamixer -t</command>
  </action>
</keybind>
```
This should be added somewhere inside the `<keyboard> ... </keyboard>` element. There should be other keybinds so just put it right after one if you don't know exactly where to put it.

Once that is done, you should have a fully set up system!
