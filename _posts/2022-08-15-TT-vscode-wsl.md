---
toc: true
comments: true
layout: post
title: VSCode Download with WSL
description: Instructions for Windows users on how to use VSCode with WSL in order to add a Linux-based development.
permalink: /techtalk/vscode-wsl
image: images/wsl.png
type: pbl
week: 0
---

## Instructions to Download Visual Studio Code Remote - WSL
> Windows is the number one desktop operating system.  However, Linux is a preferred standard for many developers.  Using WSL you can develop in a Linux-based environment, use Linux-specific tool chains and utilities, and run and debug your Linux-based applications all from the comfort of Windows.  This gives the developer on Windows the best of both worlds.

### Download WSL 
> This section of the document is intended to get the WSL distribution of Ubuntu installed on you Windows PC.  
1. Open a PowerShell. Enter WSL installation command at Prompt:
```bash
wsl --install
```
2. If you receive error ```the required operation requires elevation```  You will need to perform wsl install command again, but 1st elevate permissions using command: ```start-process PowerShell -verb runas```
3. As it states in output in shell, you will need to reboot your computer.  My suggestion is to select <mark>Restart</mark> or if available <mark>Update and Restart</mark>. 
4. After booting up there are several things that could occur
- A Command or PowerShell prompt could automatically pop up prompting you for a username. Choose a username and password to create an account.
- Some other event may occur.  Make sure you establish password when requested.  Verifying or take action in Command or Powershell, try these as ```C:\Users\<username>```...
   - Type ```wsl --list```, you should see Ubuntu
   - If no Ubuntu, Type ```wsl --list --online```, then use ```wsl --install -d Ubuntu```
   - After success
5. After WSL install, verify the following before you continue:
- Open Command or Powershell, <mark>Run as your own user account</mark>.
    - Type ```wsl```, this should put you in a different looking prompt. From ```C:\Users\<username>``` to ```<username>@MSI:```
    - If you ever need to elevate permission for installation ```sudo wsl```, followed by your computer password.
- Observe that drive changes from ```C:\``` to ```/mnt/c``` when you change prompt from native Windows to WSL.

### Download Visual Studio Code
> Installing Visual Studio Code (VSCode) with the Remote extension lets you use the WSL as your full-time development environment right from VS Code
1. Install VSCode, [Download VSCode Windows Version](https://code.visualstudio.com/)
2. When prompted to Select Additional Tasks during installation, be sure to check the Add to PATH option so you can easily open a folder in WSL using the VSCode ```code``` command.
3. Install the [Remote Development extension pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)

### Opening up VSCode with WSL
1. Open a WSL terminal window (using the start menu item or by typing wsl from a command prompt / PowerShell)
2. Navigate to a folder you'd like to open in VS Code
Here are some useful commands for our work
```bash
cd ~     # takes you to your personal directory on Windows
mkdir vscode   # creates a folder to clone your repositories
ls     # views the content of the directory you are currently on
cd ~/vscode  # changes the directory to path for vscode files
git clone https://github.com/nighthawkcoders/APCSP.git # clone repo
cd APCSP  # changes the directory to path for APCSP repos assets
code .  # opens APCSP in VSCode
cd ..    # changes the directory to the previous/parent directory
git config --global user.email mygmail@gmail.com  # tell git your email
git config --global user.name mygithub   # tell git your github id
```
3. Type ```code .``` in the terminal. When doing this for the first time, you should see VS Code fetching components needed to run in WSL. This should only take a short while, and is only needed once.

#### Opening up VSCode with WSL terminal
> Here is sample of steps with WSL <username> equal to ```shay```  These steps will need to be adapted to your environment.

- These two commands help git to understand your identity
```bash
shay@MSI:/mnt/c/Users/ShayM$ git config --global user.email shay@gmail.com
shay@MSI:/mnt/c/Users/ShayM$ git config --global user.name shay
```

- These commands clone a respository and load VSCode for work
```bash
shay@MSI:/mnt/c/Users/ShayM$ mkdir vscode
shay@MSI:/mnt/c/Users/ShayM$ cd vscode
shay@MSI:/mnt/c/Users/ShayM/vscode$ git clone https://github.com/nighthawkcoders/APCSP.git
Cloning into 'APCSP'...
remote: Enumerating objects: 8306, done.
remote: Counting objects: 100% (2360/2360), done.
remote: Compressing objects: 100% (723/723), done.
remote: Total 8306 (delta 1312), reused 2305 (delta 1262), pack-reused 5946
Receiving objects: 100% (8306/8306), 16.27 MiB | 1.11 MiB/s, done.
Resolving deltas: 100% (4360/4360), done.
shay@MSI:/mnt/c/Users/ShayM/vscode$ cd APCSP
shay@MSI:/mnt/c/Users/ShayM/vscode/APCSP$ code .
Installing VS Code Server for x64 (6d9b74a70ca9c7733b29f0456fd8195364076dda)
Downloading: 100%
Unpacking: 100%
Unpacked 2416 files and folders to /home/shay/.vscode-server/bin/6d9b74a70ca9c7733b29f0456fd8195364076dda.
shay@MSI:/mnt/c/Users/ShayM/vscode$
```

#### Setup Observation
> VSCode with WSL shows a WSL indicator in the bottom left corner of Window.
![WSL Status Bar]({{site.baseurl}}/images/wsl-statusbar-indicator.png)

#### Resource
> Read more on WSL and VSCode
[VSCode doc](https://code.visualstudio.com/docs/remote/wsl)
