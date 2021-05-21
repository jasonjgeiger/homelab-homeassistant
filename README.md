Here are instructions for getting HomeAssistant installed or back up and running after an issue.
## TOC
- Pre-booting
- Setup for CC2538 + CC2592
- Boot
- Prerequisites
- Install instructions
- Add-ons
- Configuration
- Backups/storage

## Pre-booting
1. `touch ssh` in the root directory
2. If running wifi add the wpa_supplicant.conf file

## Setup for CC2538 + CC2592
1. Modify `mnt/boot/config.txt`
    - Enable `enable_uart=1` by removing `#`
    - Under `[all]` add the line `dtoverlay=disable-bt` to disable it

## Boot the bitch
1. Power up 
2. SSH into the machine with pi:raspberry

## Software prerequisites
1. Install Docker from bash script
2. Install packages: AppArmor, Network Manager and jq

## Install Home Assistant
Use the installation guide for Home Assistant Supervised to get up and running. Here is a summary and linked references.
1. Install Supervised

[Supervised-installer repo](https://github.com/home-assistant/supervised-installer)