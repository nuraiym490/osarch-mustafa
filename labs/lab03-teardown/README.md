# Lab 3 — Teardown, and the same machine from the command line

Manufacturer: Lenovo      Date: 1.11.2026

Model: Lenovo Legion Y540-15IRH

Host operating system: Windows

Virtualization software: VMware Workstation

Linux environment: Ubuntu Server running in a virtual machine

manual link: https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/legion-series/legion-y540-15irh-pg0/81sy/documentation/doc\_userguide

## What I did

Identified my laptop as a Lenovo Legion Y540-15IRH (Machine Type: 81SY).

Used Windows PowerShell to collect information about the CPU, RAM, and storage devices.

Saved the Windows hardware information in windows-specs.txt.

Started an Ubuntu Server virtual machine using VMware Workstation.

Used Linux terminal commands to collect hardware information:

lscpu — CPU information.

free -h — memory information.

lsblk — disk information.

Saved the Linux command output in linux-specs.txt.

Configured a shared folder in VMware Workstation to transfer the Linux output to Windows.



Used Windows PowerShell to collect CPU information:

Get-CimInstance Win32\_Processor |

Format-List Name,NumberOfCores,NumberOfLogicalProcessors

Collected RAM information:

Get-CimInstance Win32\_PhysicalMemory |

Format-Table Manufacturer,Capacity,Speed,PartNumber

Collected disk information:

Get-CimInstance Win32\_DiskDrive |

Format-Table Model,MediaType,Size



Started Ubuntu Server in VMware Workstation.

Used the following commands:

CPU:

lscpu

Memory:

free -h

Disks:

lsblk -o NAME,SIZE,TYPE,MODEL

Saved the command outputs in linux-specs.txt.
```

## Result



Collected CPU, memory and disk information using Windows PowerShell.

Ran Linux commands in Ubuntu Server.

Created a Linux hardware information file.

Compared the commands used by Windows and Linux to retrieve similar hardware information.



|Hardware Information|Windows command|Linux command|
|-|-|-|
|CPU|Get-CimInstance Win32\_Processor|lscpu|
|Memory|<br />Get-CimInstance Win32\_PhysicalMemory|free -h|
|Disks|<br />Get-CimInstance Win32\_DiskDrive|lsblk|





## What did not work the first time

Saving Linux output: The output file was created inside Ubuntu, but it was not immediately available in Windows.

Shared folders: The VMware shared folder did not initially appear under /mnt/hgfs.

Copying the file: The cp command returned a No such file or directory or cannot create regular file error because the shared folder was not accessible at the expected path.

## Evidence

evidence/windows-specs.txt

evidence/linux-specs.txt

evidence/inner\_components.png

evidence/motherboard\_CPU\_cooling.png

evidence/RAM\_SSD.png



