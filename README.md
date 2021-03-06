# Dullahan
Create a headless X11 setup in the cloud and on your workstation 

## What for ?
Getting X11 up and running on a headless linux machine can sometimes be pretty tricky and time consuming, especially if the machine is not accessible or impossible to connect a display even temporarily. One particlar case are linux instances on public cloud providers like Amazon or Softlayer. Those instances come with a baremetal linux installation without X11 support and the internet is full of desperate souls looking for solutions to install X11 on their VMs, so they can remote into their instances using VNC or B11. 
Dullahan is here to help! It is a simple installer that makes the task of installing X11 for headless servers really easy.

## Status
At the moment Dullahan only exists for Debian and only has been thoroughly tested on Ubuntu but RPM based distributions are to come soon. It has been tested on Amazon Ubuntu Server 14.04 / 16.04 LTS and on SoftLayer Ubuntu 14.04 / 16.04 instances as well as on standalone workstations.

## Download the Dullahan installer
Just get it from [here](https://github.com/ccc-tomr/Dullahan/blob/master/installer/ubuntu1404/dullahan_1.0_amd64.deb) (right-click and Save Link as...) 

## How to create the Dullahan installer 
Only necessary if you want to modify the installer, you can ignore this if you downloaded the prebuild installer already as mentioned in 'Download the Dullahan installer'.

After cloning the repo, just do

./makepkg.sh

and the script will create a debian package under installer/<distro>

## How to use the Dullahan installer

### Ubuntu

#### from the command line
Use gdebi to install Dullahan:

1. Update your distro: ```sudo apt-get update```

2. Install gdebi:
```sudo apt-get install gdebi```

3. Install Dullahan:
```sudo gdebi installer/<distro>/dullahan_<..>.deb```

4. reboot:
```sudo reboot```

After the reboot, your system should run X11 headless and if you use a remote tool like vnc or b11, you can connect to your system and interact with its desktop. You can verify this by 'ps -ef | grep Xvfb'. As part of the installation the account 'ubuntu' will be set up to auto login.

#### via GUI (that would actually require X11 to run already...)

Just double click the installer package (installer/ubuntuxx/dullahan_<..>.deb) and follow the online instructions.

### ...and how do I connect to that desktop ?

In order to actually see the desktop of your newly setup x11 instance, you would have to install remoting software.
Remoting software we like and recommend:
- [TightVNC](http://www.tightvnc.com/ "TightVNC"), a free and lightweight Remote Control / Remote Desktop Software
- [B11](http://coloradocodecraft.com/ "B11") (our own SW), an extremely fast remoting software that runs in the browser and supports multi user collaboration. 

