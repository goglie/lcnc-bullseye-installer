## General installation approach

The key is to have a cleanly made Debian 11 (Bullseye) install. I tend to use an nonfree firmware iso from: https://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/current-live/amd64/iso-hybrid/

Typically I use the xfce nonfree iso   (direct link removed as it changes too much).

When doing the install do NOT set a root password.  If you do you will have to add your user to the sudo group.  Search google for how to do that.

#Add user to Sudoer
su root -> Enter password 
sudo usermod -aG sudo [USER]
*Reboot after this command and test if your user is sudoer

#Install Open SSH Server
sudo apt install openssh-server

#AutoLogon
Edit lightdm conf file
sudo nano /etc/lightdm/lightdm.conf
Uncomment and complet file (only in the [Seat] Section) autologin-user=username

#Disable DPMS (screensaver,etc..)
sudo nano /home/[USER]/.bashrc

At the end of the file I added this
# setting to stop screen from going to sleep
xset s off
xset s noblank
xset -dpms



1. Ensure git is installed:

`sudo apt install git`

2. Create a directory and clone the repo to it.  Either clone or download a zip file.

```
cd ~
mkdir dev
cd dev
git clone https://github.com/joco-nz/lcnc-bullseye-installer.git
cd lcnc-bullseye-installer
./install_for_lcnc.sh
```

Run install_for_lcnc.sh to complete a full linuxcnc install including installed debians.  Note that at this time doc's are not being built due to the time it takes and some build issues appearing with the doc build.

Run updater.sh to update the install.

## For noting: Files that must be executable

install_for_lcnc.sh

sudo_helper.sh

updater.sh

