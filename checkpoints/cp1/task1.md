# Task 1



1A



|Figure|This computer|Command it came form|
|-|-|-|
|CPU model|AMD Ryzen 7 260 w/ Radeon 780M|Get-CimInstance -ClassName Win32\_Processor \| Select-Object Name, NumberOfCores, NumberOfLogicalProcessors|
|Cores|8 cores, 16 logical processors|Get-CimInstance -ClassName Win32\_Processor \| Select-Object Name, NumberOfCores, NumberOfLogicalProcessors|
|Hardware Virtualization|enabled|systeminfo|
|memory total/available now|16252063744 / |Get-CimInstance Win32\_ComputerSystem|
|system disk:size, free space, SSD or HDD|475.92 GB, 289.77 GB, SSD|Get-Volume, Get-PhysicalDisk \| Format-List \*|
|Partition style of the system disk|GPT|Get-Disk|
|OS and version|Майкрософт Windows 11 Домашняя для одного языка|syteminfo|



1B

&#x20;A machine you have never seen: a thin-and-light laptop

Part	Specification

CPU	2 cores / 4 threads, 1.1 GHz; AMD-V supported and enabled

Memory	8 GB LPDDR4X, soldered to the board

Storage	128 GB eMMC, soldered, 31 GB free

OS	Windows 11 Home in S mode

1

Both guests? Could this laptop run both of the guests you built in Labs 1–2 at the same time, at the sizes you gave them (take them from your build log)? Show the arithmetic for CPU, memory and disk, and say what you assumed for the host itself.



My answer: No it can not. Because usually windows needs more memory and therefore there will be no memory for second virtual machine to be runned. And CPU has only 8 GB that is small amount of memory to run both guests at the same time but it is possible . I assume giving first virtual machine(Ubuntu) 2 maximum GB memory and 5 GB of storage, and i would give second virtual machine 4 GB memory and 24 GB storage.



2

Upgrade first. What would you upgrade or change first, and why? Can it actually be upgraded on this machine? If the honest answer is “nothing can be”, say so and say what you would do instead.



My answer: I would first of all upfrade memory up to 16 GB as a first upgrade(if it is possible i would give another upgrade to 32 GB, but considering that it is thin and light laptop I would not do that). Then I wolud of course upgrade storage at least to 256 GB for comfortable work

