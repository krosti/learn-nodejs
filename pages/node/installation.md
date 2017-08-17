---
title: Installation
keywords: nodejs
last_updated: August 16, 2017
sidebar: node
permalink: installation.html
---

## Installation

### Windows

The NodeJS Runtime:

The source code written in source file is simply JavaScript. It is interpreted and executed by the NodeJS interpreter.

You can download the latest version of NodeJS installable archive file from [https://nodejs.org/en/](https://nodejs.org/en/) and follow the installation steps by clicking Next in each screen.

### Linux

We can easily install NodeJS on linux/ubuntu/centOS/fedora/linuxmint etc. To install NodeJS on Linux (Ubuntu) operating system, follow these instructions:

1. Open Ubuntu Terminal (You can use shortcut keys (Ctrl+Alt+T)
2. Type command `sudo apt-get install python-software-properties`
3. Press Enter (If you have set a password for your system then it will ask for the password)
4. Type the password and press Enter
5. Type command `sudo apt-add-repository ppa:chris-lea/node.js` and press Enter twice
6. Type command `sudo apt-get update` ( Wait for sometime or go for a coffee)
7. Type command `sudo apt-get install nodejs npm`
8. Type command `sudo apt-get install nodejs`

### Mac

You can download the latest version of NodeJS installable archive file from [https://nodejs.org/en/](https://nodejs.org/en/) and follow the installation steps by clicking Next in each screen.

But the easiest way of install NodeJS in Mac is using [Brew](https://brew.sh)

If you don't have brew installed, you can install it with the following command line 

`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

then run `brew update && brew doctor`

Next, add Homebrew's location to your `$PATH` in your `.bash_profile` or .`zshrc` file.

`export PATH="/usr/local/bin:$PATH`

Next, install Node (npm will be installed with Node):

`brew install node`

## Checks

When the installation is completed you can check the version of NodeJS by running `node --version`

And check the version of npm by running `npm -v`