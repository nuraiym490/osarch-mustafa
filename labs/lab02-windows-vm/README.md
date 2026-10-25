# Lab 2 — A Windows guest, and a network between them

Pair: Amira Bolatbek / Nuraiym Mustafa. Driver first half: Mustafa Nuraiym



Machine: DESKTOP-EA7P1RT



Date: 24.10.2026

## What I did

My partner was mainly responsible for operating the computer, while I helped with the instructions, network configuration, troubleshooting, and checking the results.

1. Install Windows 11 Enterprise evaluation ISO
2. Installed Win11 and the guest tools
3. Chose VMware NAT as the network
4. ipconfig / ip addr - found wach guests' IPv4 address
5. Couldn't save the evidence via CMD. Was able to access the path via PowerShell
6. cd \\\\vmware-host\\Shared Folders\\evidence
7. ipconfig > ipconfig-windows.txt
8. ssh arrrs@192.168.201.129 ip addr > ip-addr-linux.txt
9. git add . / git commit -n "creating a file and testing smt" / git push
10. Tested whether PowerShell pushed files looked broken on GitHube (they did not)
11. ping -n 192.168.201.129
12. ping -c 4 192.168.201.130
13. Get-NetConnectionProfile
14. New-NetFirewallRule -DisplayName "Lab02 - allow ping (ICMPv4 echo)" -Direction Inbound -Protocol ICMPv4 -IcmpType 8 -RemoteAddress LocalSubnet -Action Allow
15. Get-NetFirewallRule -DisplayName "Lab02\*"
16. ping -n 4 192.168.201.129 > ping-both-ways.txt
17. ssh student@192.168.201.129 ping -c 4 192.168.201.130 >> ping-both-ways.txt
18. ping -n 2 8.8.8.8 / ping -c 2 8.8.8.8
19. Took a host-memory-before.png screenshot from task manager
20. Allocated 4GB for Ubuntu and 12GB for Windows 11
21. Windows 11 VM refused to start, giving an "Not enough system resources..." error
22. Increased host's paging size to 16-24GB
23. sudo apt install -y stress-ng / stress-ng --vm 1 --vm-bytes 90% --vm-keep --timeout 300s
24. Loaded multiple Youtube and reddit pages on Windows 11 VM
25. Took a host-memory-after.png screenshot from task manager
26. Changed the VMs' values back to normal

## Result

Network diagram:



\&#x20;                 Internet



\&#x20;                    |



\&#x20;     \\\[ Host: my PC ]   real network: Wi-Fi, 192.168.1.11



\&#x20;                    |



\&#x20;      ( NAT router of the hypervisor )   gateway 192.168.201.2



\&#x20;                    |



\&#x20;   ===== virtual switch: VMnet8 (NAT) ======



\&#x20;          |                         |



\&#x20;  \\\[ lab01-ubuntu ]          \\\[ lab02-win11 ]



\&#x20;  ens33                     Ethernet0



\&#x20;  192.168.201.129           192.168.201.130



The firewall:



The first ping from Linux to Windows failed because Windows classifies the new network as Public and blocks incoming echo requests by default. To fix this, I added an inbound rule to allow only ICMPv4 type 8 echo requests from the local subnet: New-NetFirewallRule -DisplayName "Lab02 - allow ping (ICMPv4 echo)" -Direction Inbound -Protocol ICMPv4 -IcmpType 8 -RemoteAddress LocalSubnet -Action Allow



Overcommitment experiment:



Host total - 16GB (13.9 usable)



Sum promised to the guests - 20GB (8GB Ubuntu, 12GB Windows 11)



Before - 6.3GB in use, 7.6GB available, 11.9/16.9GB committed



After - 13.6GB in use, 317MB available, 33.5/33.9GB committed



How host felt - slight mouse lag, huge delay in opening/closing/moving windows



What the host and hypervisor did - since memory was dropping close to zero, the host heavily relied on memory compression and page file swapping. The hypervisor honored the memory requests, causing system slowdowns and high disk usage as the host and guests competed for physical memory.

## What did not work the first time

Our work in class:

During my first attempt to install Windows in VMware, I encountered an issue with insufficient disk space. While working with the virtual machine, the available storage space on my SSD decreased rapidly until there was no free space left. As a result, I was unable to continue the installation process normally.



## Evidence

* evidence/ipconfig-windows.txt
* evidence/ip-addr-linux.txt
* evidence/ping-both-ways.txt
* evidence/host-memory-before.png
* evidence/host-memory-after.png

