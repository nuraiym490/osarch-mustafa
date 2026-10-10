# Lab 0 — Inventory your own machine

Pair: No pair                    Driver first half:
Machine:DESKTOP-HBRLNMA
Date:10.10.2026

## What I did

unpacked zip to my repository

1. git clone https://github.com/nuraiym490/osarch-mustafa.git
2. cd osarch-mustafa 
3. cd labs\\lab00-inventory
4. cd evidence
5. Get-CimInstance Win32\_Processor | Format-List \* | Out-File -Encoding utf8 .\\cpu.txt
6. Get-ChildItem
7. Get-CimInstance Win32\_PhysicalMemory | Format-Table DeviceLocator, Capacity, Speed, Manufacturer, PartNumber -AutoSize | Out-File -Encoding utf8 .\\memory.txt
8. Get-CimInstance Win32\_DiskDrive | Format-Table Model, MediaType, InterfaceType, Size -AutoSize | Out-File -Encoding utf8 .\\disk.txt
9. Get-CimInstance Win32\_BIOS | Format-List Manufacturer, SMBIOSBIOSVersion, ReleaseDate | Out-File -Encoding utf8 .\\firmware.txt
10. systeminfo
11. Get-CimInstance Win32\_ComputerSystem
12. Get-PhysicalDisk | Format-List \*
13. Get-Volume
14. Get-Content .\\cpu.txt
15. Get-CimInstance Win32\_BIOS
16. $env:firmware\_type

## Result

|What|Value|Where I got it|
|-|-|-|
|Total memory|8589934592|Get-CimInstance Win32\_ComputerSystem|
|Number of RAM modules|1|Get-CimInstance Win32\_PhysicalMemory|
|RAM speed|2667|Get-CimInstance Win32\_PhysicalMemory|
|Disk model|HFM512GDHTNG-8310A|Get-CimInstance Win32\_DiskDrive|
|Disk type|SSD, NVMe|Get-PhysicalDisk \| Format-List \*|
|free disk space|114.46 GB|Get-Volume|
|CPU model|Intel(R) Core(TM) i5-9300HF CPU @ 2.40GHz|Get-Content .\\cpu.txt|
|CPU core count|4|Get-Content .\\cpu.txt|
|CPU threat count|8|Get-Content .\\cpu.txt|
|Firmware version|BHCN36WW|Get-CimInstance Win32\_BIOS|
|Firmware type|UEFI|$env:firmware\_type|
|Firmware date|2/10/2020|systeminfo|
|Hardware Virtualization|enabled|systeminfo|



## What did not work the first time

The Confirm-SecureBootUEFI command returned an access denied error. I checked the firmware mode using msinfo32 and confirmed that it is UEFI.



I also initially used an incorrect file path when saving evidence. I corrected the path and saved the files in the evidence directory.

## Evidence

* [evidence/](evidence/)cpu.txt
* [evidence/](evidence/)memory.txt
* [evidence/](evidence/)disk.txt

