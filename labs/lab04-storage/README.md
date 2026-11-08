# Lab 4 — Partition, mirror, fail, recover

Pair: no pair                    Driver first half:
Machine:DESKTOP-TMR0L2E
Date:08.11.2026

# What I did

Linux guest (RAID 1)

Installed mdadm.
Created a GPT partition table and one 900 MiB partition on each of the three extra disks (sdb, sdc, sdd).
Built a RAID 1 mirror from sdb1 and sdc1; sdd1 was kept as a spare.
Formatted the array as ext4 and mounted it at /mnt/raid1.
Wrote a test file and saved its SHA-256 checksum.
Marked sdc1 as failed and removed it. The array became degraded.
Checked the file was still readable and the checksum was the same.
Added sdd1 to the array and waited until the rebuild finished.

Windows guest

Added a new virtual disk and initialized it as <GPT / MBR>.
Created a partition, formatted it as NTFS and assigned the letter <X>.
# Result

State	Array	Checksum
Healthy	clean, [2/2] [UU]	recorded
Degraded	clean, degraded, [2/1] [U_]	same as before
Rebuilt	clean, [2/2] [UU]	same as before

The file survived the loss of one disk and its checksum did not change.

The Windows disk uses <GPT / MBR> because <reason>.

Does RAID 1 help if a colleague deleted the wrong file an hour ago? No. The mirror copies every change to both disks immediately, including a deletion, so the file was gone from both disks at once. RAID protects against disk failure, not human mistakes; for that you need a backup or snapshot.

# What did not work the first time
Saving files from Ubuntu: I had problems saving the evidence and getting it out of the virtual machine to my laptop. 
Downloading tools in Ubuntu: some packages did not install at first ("Unable to locate package"). 
# Evidence
evidence/lsblk-before.txt 
evidence/array-healthy.txt
evidence/array-degraded.txt
evidence/checksum-before.txt
evidence/checksum-after-failure.txt 
evidence/array-rebuilt.txt 
evidence/windows-disk.txt
