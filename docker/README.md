# Docker

## First steps with Docker

If you have not already installed and setup Docker, see the below [Setup](#setup) section.

For your first step to learning Docker, watch/go through [Docker Tutorial for Beginners](https://www.youtube.com/watch?v=pTFZFxd4hOI) and then the [Docker beginning practice](./docker_practice_beginners.md).

## Setup
How you need to go about installing Docker on your system varies. Below are instructions for [MacOS](#macos), [GNU/Linux](#linux), and [Windows](#windows).

### MacOS
MacOS currently has the simplest installation - just visit [the Docker website](https://www.docker.com/products/docker-desktop/) and install/open the `.dmg` file to install.

Note that on MacOS, Docker uses a virtualized GNU/Linux OS to actually run Docker and its containers - this is not too important to know when using Docker, but just note that Docker desktop must be running (which will run the virtualized GNU/Linux OS automatically) in order to user Docker, even from the command line.

### Linux
As there are many different distributions for GNU/Linux, Docker has instructions for Docker Desktop installation for the following:
- [Debian](https://docs.docker.com/desktop/install/debian/)
- [Fedora](https://docs.docker.com/desktop/install/fedora/)
- [Ubuntu](https://docs.docker.com/desktop/install/ubuntu/)
- [Arch](https://docs.docker.com/desktop/install/archlinux/)

### Windows
Docker Desktop installation on Windows _can_ be a bit more involved.

Similar to MacOS, Windows cannot run Docker natively: a virtualized GNU/Linux distribution must be used. For Windows, a GNU/Linux distro can be installed easily using Windows Subsystem for Linux (WSL). Before that, though, there are two things that must be done:
1. Virtualization _must_ be enabled in your machine's UEFI/BIOS
2. Windows Subsystem for Linux (WSL) must be installed and setup

#### Ensure Virtualization is enabled
On Windows, Docker requires that virtualization be enabled - the same virtualization that is required or something like [VirtualBox](https://www.makeuseof.com/what-is-virtualbox-what-does-it-do/) and the same one that Windows Subsystem for Linux and Docker use (in a different way, mind you). To put it simply, virtualization allows an operating system to run a virtual (i.e. simulated) operating system on top of itself.

For VirtualBox, this means running a whole set of virtualized (again, simulated) hardware, along with the operating system on top of it. For things like Docker, running virtualized hardware is not necessary, saving a lot of resources when using Docker containers versus using something like using an operating system within VirtualBox - see [here](https://www.freecodecamp.org/news/docker-vs-vm-key-differences-you-should-know/) for more info.

To ensure virtualization is enabled in your PC’s [BIOS](https://en.wikipedia.org/wiki/BIOS), do the following:
1. Check whether virtualization is enabled or not
    a. Follow one of the procedures [here](https://techviral.net/check-if-virtualization-is-enabled/) to check if virtualization is enabled
2. If virtualization is not enabled, you will need to access your UEFI/BIOS menu by...
    a. (For UEFI - a newer form of a BIOS) Follow [this video](https://www.youtube.com/watch?v=GBKe5V26yQs) on how to boot into the UIFI/BIOS menu, where you can change boot and other base system settings, in Windows.
        > NOTE: The above video will show how to check if your system supports (and therefore likely runs) UEFI 
    b. (For legacy BIOS) Follow [this article](https://www.lifewire.com/enter-bios-on-windows-10-5095780)
        i. Unfortunately, you will need to restart your computer and hold a certain key (which key may be shown on your computer’s boot splash screen at the bottom), and what the menu or BIOS looks like will depend on you computer - in some cases you will taken directly to the BIOS menu, in others you may need to choose the appropriate option from a menu.
3. Enable virtualizations:
    a. This procedure will depend on your BIOS menu (which depends on your PC), but in general involves finding the Advanced Options or Security section, enabling virtualization - the setting name should be one of Intel Virtualization Technology (Intel PC) or SVM Mode (AMD PC) - and saving and exiting the BIOS.
    b. You should be able to navigate the menu using the arrow keys, using `[Esc]` to exit sub menus/the whole UEFI/BIOS menu without saving, and `[F10]` to save and exit.

#### Install Windows Subsystem for Linux (WSL)
Instructions for installing Windows Subsystem for Linux (WSL) are available [here](https://learn.microsoft.com/en-us/windows/wsl/setup/environment). It mainly just involves opening a command prompt/PowerShell session and running `wsl --install`. The installation will likely take quite a long time (10-20 minutes), as this command is basically installing a whole virtualized operating system (Ubuntu).

Be sure to update [Ubuntu subsystem](https://learn.microsoft.com/en-us/windows/wsl/setup/environment) after it if fully installed. If you get errors about no connection, try doing the following:
1. Close this Ubuntu shell
2. Open PowerShell and run: `wsl --set-default-version 1 && wsl --set-version Ubuntu 1`
3. Re-open the Ubuntu shell and try updating again: `sudo apt update && sudo apt upgrade`
    > NOTE: You will likely have to reply `y` or `yes` once the update is ready to confirm you want to perform the update.
    
Once you have WSL setup, running Docker Desktop should be all you need to do as it will handle running the Ubuntu virtual OS that Docker needs to work.

#### Install Docker Desktop

Go [here](https://docs.docker.com/engine/install/) and install Docker Desktop for Windows. Then open/run Docker Desktop and ensure it starts properly - see the bottom-left corner of the Docker Desktop GUI: should be green and list "Engine running".

