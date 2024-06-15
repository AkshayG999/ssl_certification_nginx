

## Table of Contents
-   [System Setup](#system-setup)
    -   [Update System Packages](#update-system-packages)
    -   [Node.js Installation](#nodejs-installation)
    -   [NVM Installation](#nvm-installation)
    -   [PM2 Installation](#pm2-installation)
    -   [Google Chrome Installation](#google-chrome-installation)
    -   [Yarn Installation](#yarn-installation)

<div align="right">

[![](#table-of-contents)](#readme-top)

</div>

 
## System Setup

Follow the steps below to prepare your system for development.

### Update System Packages

Start by updating your system's package list to ensure all packages are up to date: 

    sudo apt update

### Node.js Installation

Install the latest LTS version of Node.js using the following commands: 

    curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
    sudo apt-get install -y nodejs 

Verify the installation: 

    node --version

### NVM Installation

Install NVM (Node Version Manager) to manage Node.js versions: 

    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash

 

After the script finishes, apply the changes:

    source ~/.bashrc

 
Verify NVM installation: 

    nvm --version

 

Install the latest version of Node.js using NVM: 

    nvm install node


### PM2 Installation

Install PM2, a process manager for Node.js applications: 

    npm install pm2 -g

Verify PM2 installation: 

    pm2 --version

 

### Google Chrome Installation

Install Google Chrome by following these steps:

1.  Install dependencies required for Google Chrome:
    
    `sudo apt install -y wget apt-transport-https ca-certificates curl`
    
2.  Download the Google Chrome .deb package:
    
	`wget https://dl.google.com/linux/direct/google-chrome-		stable_current_amd64.deb`

    
3.  Install Google Chrome:
    
	`sudo dpkg -i google-chrome-stable_current_amd64.deb`

 
4.  If there are dependency issues, resolve them with: 

	`sudo apt-get -f install`
    
6.  Verify the installation:
    
    `google-chrome --version` 
    
7.  To locate the installation path:
     
    `which google-chrome` 
    

### Yarn Installation

Install Yarn, a package manager, by following these steps:

1.  Add the Yarn repository key:
    
    `curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -` 
    
2.  Add the Yarn repository to your system's package sources:
     
    `echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list` 
    
3.  Update your package index:
    
    `sudo apt update` 
    
4.  Install Yarn:
    
    sudo apt install yarn
    

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk4NjE2NjEyNCwtODEwMzQwMzU4XX0=
-->