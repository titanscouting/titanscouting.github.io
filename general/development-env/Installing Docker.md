---
permalink: /development/docker
title: 1. Installing Docker
---

# Overview 

TRA API and TRA Analysis both use Docker for development. Docker is a software which allows you to run containers on your computer. Containers are a standardized unit of software that allows developers to isolate their app from its environment, solving the “it works on my machine” headache. These containers come preconfigured with all the software that you need to get started developing the TRA API and TRA Analysis. VSCode also allows you to develop inside these containers for a seamless experience. 

# System Requirements
For Windows: 
* Windows 10 64-bit: Pro, Enterprise, or Education (Build 16299 or later). If you have Windows 10 Home or a 32-bit edition of Windows, please contact the Titan Scouting lead. 
* 64-bit processor (All Intel or AMD CPUs from the last 15 years are 64-bit processors).
* 4GB RAM 
* Virtualization must be enabled in your BIOS (click [here](https://docs.docker.com/docker-for-windows/troubleshoot/#virtualization-must-be-enabled) to check if it is enabled).

## Instructions for Windows
### 1. Enabling WSL2
Docker for Windows primarily runs off of the Windows Subsystem for Linux, which lets developers run a GNU/Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup. WSL2 is a new version of the Windows Subsystem for Linux architecture that powers the Windows Subsystem for Linux to run ELF64 Linux binaries on Windows. Docker uses the WSL2 backend which allows for better performance. 

#### Instructions

1. Click on the Start button on your taskbar.
2. Type "Turn Windows Features On or Off".
3. Scroll down the menu and check the box next to "Windows Subsystem for Linux".
4. Click "OK". Allow Windows to install all the neccessary components, and reboot when prompted. 

### 2. Installing Docker

1. Click [here](https://download.docker.com/win/stable/Docker%20Desktop%20Installer.exe) to download Docker. 
2. Run the downloaded executable.
3. 
