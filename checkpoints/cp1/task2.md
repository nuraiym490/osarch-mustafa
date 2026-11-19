# Task 2



||Ubuntu Server|Windows 11|
|-|-|-|
|vCPU|1 (2 is comfortable)|2|
|RAM|1 GB (2 GB comfortable)|4 GB|
|Disk|\~5 GB minimum|24 GB|
|Other|none|UEFI, Secure Boot, TPM 2.0 (vTPM in VMware)|



FOR UBUNTU

nproc → the vCPU count you set

free -h = RAM setting

lsblk -d -o NAME,MODEL,SIZE,ROTA,TRAN = Linux specs

ip -br a → one interface with an address

FOR WINDOWS

Get-CimInstance Win32\_Processor= vCPU count

Get-CimInstance Win32\_ComputerSystem about =RAM

Get-Volume = for your storage

ipconfig address

