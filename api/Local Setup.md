---
permalink: /api/local-setup
title: Local Setup
---

# Overview of Local API Development Setup

1. Download WSL2
2. Download Windows Terminal (optional)
3. Install node
4. Install yarn
5. Install redis server
6. Clone github repository
7. Copy and paste the .env config file

## Download WSL2

1. Navigate to the Windows Powershell in the start menu and run as administrator 
2. Run the following command to install WSL and Ubuntu: 
```bash 
wsl --install -d ubuntu
``` 
3. Restart your computer
4. Create a username and password within the Ubuntu terminal
### Reccomended
5. Create a source directory and enter it using the following commands:
```bash
mkdir src
cd src
```
https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-10#1-overview


## Optional: Download Windows Terminal
1. Go to the Microsoft app store and download windows terminal to use for multiple tabs of WSL Ubuntu. 
2. Create tabs using the dropdown arrow in the top tab and selecting Ubuntu

## Install Node, Yarn, and Redis
1. Run the following global commands to download the necessary packages
```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo npm install -g yarn
sudo apt install redis-server
```
https://github.com/nodesource/distributions
https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04

https://www.digitalocean.com/community/tutorials/how-to-install-and-use-the-yarn-package-manager-for-node-js

https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-redis-on-ubuntu-18-04

## Clone the Titan scouting Red-Alliance-API github repository
1. Run the following commands to clone the repository then open it up in vscode:
```bash
git clone https://github.com/titanscouting/red-alliance-api.git
cd red-alliance-api
code .
```

## Paste in the environment file
1. Ask a titanscouting API member (Shaan, Blessita, or Dev) to send you the .env file
2. Copy this file and paste it into your directory, making sure the name is .env

## To run for development
1. Open up windows terminal and create two tabs of Ubuntu
2. cd into your src directory for both terminals if you created one, and then into the red-alliance-api directory
3. In one window, open up VScode through the command terminal using code . 
4. In the other window, run the following command:
```bash
redis-server
```
5. Within VScode, open up the terminal and run the following:
```bash
yarn start
```
6. You should see a success message saying "Redis Client Connected!"
7. you are now ready to begin API Development. Happy Coding!

## Troubleshooting
1. If your setup doesn't work, try the links above to see what's wrong
2. If problems persist, contact a Titan Scouting API Member (Shaan, Blessita, Dev)
