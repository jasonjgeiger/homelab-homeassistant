Here are instructions for getting HomeAssistant installed or back up and running after an issue.
## TOC
- Pre-booting
- Setup for CC2538 + CC2592
- HA prerequisites
- Install HA
- Add-ons
- Configuration
- Backups/storage

## Pre-booting
Open the boot drive on a writing machine aka - your laptop
1. `touch ssh` in the root directory
2. If running wifi add the wpa_supplicant.conf file

## Setup for CC2538 + CC2592
Open the boot drive on a writing machine aka - your laptop
1. Modify `config.txt` by adding the following at the bottom
```
#disable bluetooth and enable GPIO for zigbee
 enable_uart=1
 dtoverlay=pi3-disable-bt
 ```
2. Boot the bitch and use raspi-config set uart to enabled

## HA prerequisites
1. Install packages: AppArmor, Network Manager and jq
```
sudo apt-get install network-manager apparmor-utils jq git -y
```
2. Install Docker from bash script 
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker pi
```
3. Disable ModemManager `systemctl disable ModemManager.service`. Home Assistant will provide a warning if enabled

4. UUID=36E1-9145 /mnt/video_storage  exfat  defaults  0 0

6. mount external drive to `/usr/share/media` and add mount to `/etc/fstab`

## Install Home Assistant
_This is not needed but worth the experiment_ - Home Assistant Supervised doesn't support adding volumes to the docker containers. I have pulled the [Supervised-installer repo](https://github.com/home-assistant/supervised-installer) down and modified the installer.sh to point to local files directory for the docker-compose setup. The docker-compose was modified in `files/hassio-supervisor` to include the zigbee device and the video_storage volume.

## Add-ons
## Configuration
## Backups/storage

## Resources
- [Really good tutorial for Supervised Install](https://peyanski.com/how-to-install-home-assistant-supervised-official-way/)