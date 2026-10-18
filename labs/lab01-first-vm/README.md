# Lab 1 — Your first virtual machine

Pair:                     Driver first half:
Machine:DESKTOP-HBRLNMA
Date: 10.18.2026

## What I did

Created a virtual machine named Ubuntu-Server-Lab1 in VMware Workstation Pro.

Installed Ubuntu Server LTS using an ISO image.

Configured the virtual machine with \[number of vCPUs] vCPUs, \[RAM amount] GB of RAM, and a \[disk size] GB virtual disk.

Created a snapshot named clean-install before making any changes to the guest operating system.

Deleted /etc/hostname to simulate a system configuration problem.

Restored the virtual machine from the clean-install snapshot and checked that the hostname file was restored.```

## Result

Ubuntu Server was installed and booted successfully in VMware Workstation Pro.

I verified the guest operating system version using lsb\_release -a.

I tested the snapshot recovery process by deleting /etc/hostname and restoring the virtual machine to its previous state.

## What did not work the first time

After installation, Ubuntu asked me to remove the installation medium before rebooting. I also forget my login and tried to recall what it was. 

## Evidence

* evidence/vm-settings.png — virtual machine CPU, memory, and disk settings.
* evidence/guest-release.txt — output of lsb\_release -a, showing the Ubuntu Server version.
* evidence/broken.png — terminal showing the missing /etc/hostname file.
* evidence/snapshot-list.png — VMware snapshot list showing clean-install after rollback.

