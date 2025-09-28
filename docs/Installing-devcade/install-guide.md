# Setting up a Devcade Machine

This guide will walk you through the steps involved in setting up a Devcade machine. The goal is to walk through the basic setup that is needed in order to reach the point where you have a working system that can run the onboard (Located [here](https://github.com/ComputerScienceHouse/devcade-onboard))

## Installing the Operating System

The first step in the process of setting up a Devcade machine is to install an operating system. Devcade is designed to run on Debian Linux, but should be able to run on other Linux distributions as well.

Choose a Linux distribution, and install it. A few notes about the installation:

- Make sure to set a hostname you will remember. You will need this to connect to the system remotely in the future.
- Set a root password, and make sure to remember it. You will need to sign in as root to do initial setup after the installation is complete.
- If you are given the option to create a user, do that now. Set a username and password you will remember. This will be your main user, and most of the things you do on this machine will be performed by this user.
- Feel free to configure your disk however you would like. The simplest option is using the entire disk and putting everything in one partition, but feel free to customize it if you would like.

Beyond those steps, you are welcome to customize your operating system installation however you would like. We recommend not installing a desktop environment, as Devcade does not use one, and having the system boot directly to the command line will make later setup steps easier.

If prompted to choose what additional software you would like to install, we recommend installing an SSH server, as well as `standard system utilities` (if that is an option). If you are not able to, or do not want to install any of these things, you can always install them later, so don't feel pressured if you don't know what you want to install.

We recommend not installing a desktop environment, as it will make some of the later setup steps easier. However, if you would like to install a desktop environment, you are welcome to do so, but the official Devcade software does not use a desktop environment in any capacity.

Other things to consider when installing the operating system:
- Make sure you are able to get a network connection. Either a wired or a wireless connection will work, as long as you know how to set it up and get your system on the network.
- Make sure you set the system language, keyboard layout, and timezone as necessary
- When prompted to configure the package manager, it is recommended that you select the mirror that is closes to you geographically. If you are unsure which one to pick, the default is a good choice. If you ever find that package installations or updates are taking a long time, you can always manually change the mirrors.

Once the operating system has finished installing, reboot the system, and remove the installation media once the system is powered off (if applicable)

## Software Setup

#### Sudo Permissions for Non-Root User
Once you power on the system with the operating system installed, sign in to the user you created during the installation process

> [!NOTE] If you did not create a user during the system installation, sign in as the root user, and create a new user now.

Once you have a user, you need to make sure that user has access to `sudo`. To do this, you first need to make sure you have `sudo` installed. Run the command `visudo` as root to edit your `sudoers` file.

> [!NOTE] If you are already signed in as your non-root user, an easy way to switch to the root user is to run the command `su -`. You will then be prompted to enter the password for the root user account.

Once you have done that, return to your non-root user for the remainder of the setup process.

#### Software Installation

The next step will be to install all of the required packages. First, install all of the following packages using your system's package manager. You are welcome to swap some of these packages out for alternatives if you would like. Just keep in mind that the rest of this guide will assume you used these packages, so if you use alternatives you may have to set certain things up differently.

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
- x11-utils
- libusb-dev
- meson
- cmake
- libnfc-dev
- libfreefare-dev
- openssl
- libssl-dev

> [!NOTE] The package names listed here are the names of the packages that you will need to install on Debian. If you are using a different Linux distribution, some packages may have slightly different names.

Next, install the .NET SDK. The following commands will install it on Debian. To see how to install it on other Linux distributions, check [this page](https://learn.microsoft.com/en-us/dotnet/core/install/linux)

```
wget https://packages.microsoft.com/config/debian/12/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
sudo apt-get update && sudo apt-get install -y dotnet-sdk-6.0
```

Then, install rust using the rustup install script. If prompted to choose an installation option, selecting the default is fine.

```curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh```

Once rust is installed, make sure you update your PATH to include `$HOME/cargo/env`.

#### Setting up Flatpak

The next step in the process is to set up Flatpak. The all of the games are built into flatpaks before they are uploaded to Devcade.

In order to do this, you first need to clone this repo: `https://github.com/Mstrodl/flatpak.git`.

Once the repo is cloned, the following series of commands will build flatpak so that you are able to run the onboard. The following steps assume you are running Debian. If you are using a different distribution, some syntax may be slightly different.

Navigate to the directory of the repo you just cloned (ex: `cd flatpak`)

Run the following series of commands to build flatpak

```
sudo apt build-dep flatpak
git submodule update --init
meson setup --prefix=/usr --sysconfdir=/etc --localstatedir=/var -Dselinux_module=disabled -Dinstalled_tests=true -Ddbus_config_dir=/usr/share/dbus-1/system.d -Dprivileged_group=sudo -Drun_media_dir=/media -Dsystem_bubblewrap=bwrap -Dsystem_dbus_proxy=xdg-dbus-proxy -Dsystemdsystemunitdir=/lib/systemd/system -Dsystemdsystemenvgendir=/lib/systemd/system-environment-generators -Dsystem_helper_user=_flatpak -Dgtkdoc=disabled _build
meson compile -C _build
meson test -C _build
sudo meson install -C _build
```

The next step is setting up nfc support, which can be done by running the following commands

```
curl -L https://github.com/nfc-tools/libfreefare/releases/download/libfreefare-0.4.0/libfreefare-0.4.0.tar.bz2 > libfreefare-0.4.0.tar.bz2
bzip2 -d libfreefare-0.4.0.tar.bz2
```

Once you have done that, you are now ready to set up the onboard.

#### Onboard Setup

First, clone the onboard repo: https://github.com/ComputerScienceHouse/devcade-onboard

Navigate to `[ONBOARD DIRECTORY]/onboard`, replacing `[ONBOARD DIRECTORY]` with the path to the repo you just cloned.

From there, you should make a copy of the file `.env.template`, name it `.env`, and put it in your home directory. Then, fill in the values.

Save that file, and then navigate to the `./backend` and run `cargo build`

Once that is done, navigate up a directory, back to `[ONBOARD DIRECTORY]/onboard`

You should then be able to run the onboard with the command `./onboard`

If you get an error about not having permission, make sure the `onboard` file has execute permissions.
(Try running the command `chmod +x onboard`)
