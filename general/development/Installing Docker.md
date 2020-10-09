---
permalink: /general/development/docker
title: Installing Docker
sort: 1
---

# Overview 

TRA API and TRA Analysis both use Docker for development. Docker is a software which allows you to run containers on your computer. Containers are a standardized unit of software that allows developers to isolate their app from its environment, solving the “it works on my machine” headache. These containers come preconfigured with all the software that you need to get started developing the TRA API and TRA Analysis. VSCode also allows you to develop inside these containers for a seamless experience. 

# System Requirements
## Windows
* Windows 10 64-bit: Pro, Enterprise, or Education (Build 16299 or later). If you have a 32-bit edition of Windows, please contact the Titan Scouting lead. 
* Windows 10 Home 64-bit: Follow this guide [here](https://docs.docker.com/docker-for-windows/install-windows-home/)
* 64-bit processor (All Intel or AMD CPUs from the last 15 years are 64-bit processors).
* 4GB RAM 
* Virtualization must be enabled in your BIOS (click [here](https://docs.docker.com/docker-for-windows/troubleshoot/#virtualization-must-be-enabled) to learn how to check if it is enabled).

## macOS
* 2010 or new Mac hardware
    - If you are not sure whether your hardware is supported, enter `sysctl kern.hv_support` into the terminal. It should output `kern.hv_support: 1`.
* macOS 10.13 or newer
    - macOS Catalina, Mojave, or High Sierra
* At least 4GB of RAM

## Instructions for Windows
### Enabling WSL2
Docker for Windows primarily runs off of the Windows Subsystem for Linux, which lets developers run a GNU/Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup. WSL2 is a new version of the Windows Subsystem for Linux architecture that powers the Windows Subsystem for Linux to run ELF64 Linux binaries on Windows. Docker uses the WSL2 backend which allows for better performance. 

To enable WSL:

1. Click on the Start button on your taskbar.
2. Type "Turn Windows Features On or Off".
3. Scroll down the menu and check the box next to "Windows Subsystem for Linux".
4. Click "OK". Allow Windows to install all the neccessary components, and reboot when prompted. 

### Installing Docker

1. Click [here](https://download.docker.com/win/stable/Docker%20Desktop%20Installer.exe) to download Docker. 
2. Run the downloaded executable.
3. Click "OK", ensuring "Enable WSL 2 Windows Features" and "Add shortcut to desktop" are enabled.
4. Allow the installer to finish.
5. Click "Close on restart". Docker has now been installed and will start on system startup. 
6. After restarting, you may be prompted to install the WSL 2 Linux Kernel. Follow the instructions to install the kernel, and then click the restart button from the prompt.

## Instructions for macOS

1. Click [here](https://download.docker.com/mac/stable/Docker.dmg) to download Docker. 
2. Double click the downloaded `.dmg` file and drag the Docker icon to the Applications folder.
3. Double-click `Docker.app` in the Applications folder to start Docker.
