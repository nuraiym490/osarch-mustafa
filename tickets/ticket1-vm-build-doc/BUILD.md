# Ticket 1



# Important Terms



Before starting, it is important to understand several basic terms.



\*\*Virtual Machine (VM)\*\*

A virtual machine is a computer created inside another physical computer. It behaves like a separate computer and can run its own operating system. In this project, we will create one Linux VM and one Windows VM.



\*\*Host Computer\*\*

The physical computer on which VMware Workstation is installed. It provides the processor, memory and storage used by virtual machines.



\*\*Guest Operating System\*\*

The operating system installed inside a virtual machine. Ubuntu Server and Windows are the guest operating systems in this project.



\*\*Hypervisor\*\*

Software that creates and manages virtual machines. We use VMware Workstation as our hypervisor.



\*\*ISO File\*\*

An ISO file is an installation image containing the files needed to install an operating system. We need one ISO for Ubuntu Server and another ISO for Windows.



\*\*CPU / vCPU\*\*

The CPU is the processor of the computer. A vCPU is a virtual processor allocated to a virtual machine. It uses processing resources from the host computer.



\*\*RAM\*\*

RAM is temporary working memory used by running programs. A virtual machine receives a portion of the host computer's RAM.



\*\*Virtual Disk\*\*

A virtual disk is a file or group of files stored on the host computer. The guest operating system uses it as its own hard drive.



\*\*Network Adapter\*\*

A virtual network adapter allows a virtual machine to connect to a network.



\*\*NAT (Network Address Translation)\*\*

A network mode that allows a virtual machine to access the internet through the host computer's network connection.



\*\*Bridged Network\*\*

A network mode that connects a virtual machine to the physical network as if it were another device on that network.



\*\*Host-only Network\*\*

A private network between the host computer and virtual machines. It normally does not provide internet access by itself.



\*\*Snapshot\*\*

A saved state of a virtual machine. It allows the user to return to an earlier state if something goes wrong during testing.



\*\*IP Address\*\*

A numerical address assigned to a device on a network. It is used to identify and communicate with other devices.



\*\*Ping\*\*

A command used to test whether another device can be reached over a network.



\---



# Requirements Before Starting



You need:



1\. A physical computer running Windows.

2\. VMware Workstation installed.

3\. An Ubuntu Server installation ISO file.

4\. A Windows installation ISO file.

5\. Enough free disk space and RAM to run both virtual machines.

6\. An internet connection.



Download the operating system installation images from their official sources:



\- Ubuntu Server: https://ubuntu.com/download/server

\- Windows: https://www.microsoft.com/software-download/



Make sure you know where both ISO files are saved. You will need to select them during virtual machine creation.



Before continuing, check the available memory and free disk space on the host computer. Do not allocate all host resources to virtual machines because Windows and VMware also need resources to operate.



\## 3. Install and Open VMware Workstation



1\. Open the VMware Workstation installer.

2\. Follow the installation wizard.

3\. Accept the licence agreement.

4\. Keep the default installation options unless your computer requires a different configuration.

5\. Finish the installation.

6\. Restart the computer if the installer requests it.

7\. Open VMware Workstation from the Windows Start menu.



VMware Workstation is the software that will create and manage the two virtual computers. We use it instead of installing another operating system directly on the physical laptop because virtual machines are easier to isolate, manage and restore.



\## 4. Create the Linux Virtual Machine



&#x20;**Start the virtual machine creation wizard**



1\. Open VMware Workstation.

2\. Click \*\*File\*\* in the top menu.

3\. Select \*\*New Virtual Machine\*\*.

4\. Select \*\*Typical (recommended)\*\*.

5\. Click \*\*Next\*\*.



The Typical option provides a straightforward setup process. It is suitable for a beginner because it guides the user through the main configuration steps.



&#x20; **Select the Ubuntu installation ISO**



1\. Select \*\*Installer disc image file (ISO)\*\*.

2\. Click \*\*Browse\*\*.

3\. Find the Ubuntu Server ISO file on your computer.

4\. Select the ISO file.

5\. Click \*\*Next\*\*.



The ISO file contains the Ubuntu Server installer. Selecting it tells VMware which operating system will be installed inside the virtual machine.



If VMware does not automatically recognise the ISO, select Linux and the appropriate Ubuntu 64-bit version manually.



&#x20;**Name the Linux virtual machine**



1\. Enter the name `Ubuntu-Test`.

2\. Select a location where the virtual machine files will be stored.

3\. Make sure the selected drive has enough free space.

4\. Click Next.



A descriptive name makes it easier to identify the Linux machine later, especially when multiple virtual machines are present.



&#x20;**Configure the virtual disk**



1\. Enter the planned maximum disk capacity: 25GB.

2\. Select Store virtual disk as a single file or Split virtual disk into multiple files, depending on your chosen configuration.

3\. Click Next.



The virtual disk acts as the hard drive of the Ubuntu machine. Its capacity should be sufficient for the operating system and the applications that will be tested.



A single file is convenient to manage as one unit. Splitting the disk can make it easier to move or copy large virtual machines. Either option can work; the important point is to record which one was selected.



&#x20;**Configure hardware resources**



1\. Open Customize Hardware.

2\. Find the Memory setting.

3\. Enter the planned RAM allocation: 2GB.

4\. Find the Processors setting.

5\. Select the planned number of virtual processors: 2vCPu.

6\. Open Network Adapter.

7\. Select the network mode planned for this environment.

8\. Click Close.

9\. Click Finish.



The memory and processor allocations must be based on the actual capacity of the host computer. Giving the VM too many resources can make the host computer slow or prevent the second VM from running properly.



The selected network mode must be compatible with the requirement that both guests have internet access and can communicate with each other.



&#x20;**Install Ubuntu Server**



1\. Select `Ubuntu-Test` in the VMware library.

2\. Click \*\*Power on this virtual machine\*\*.

3\. Wait for the Ubuntu installation menu.

4\. Select the installation option.

5\. Choose the language.

6\. Select the keyboard layout.

7\. Continue through the installer.

8\. Configure the network using the available network interface.

9\. Select the storage configuration for the virtual disk.

10\. Create a username and password.

11\. Confirm the installation settings.

12\. Start the installation.

13\. Wait until the installation finishes.

14\. Reboot the virtual machine when prompted.



Ubuntu Server is installed inside the virtual disk. This does not replace or modify the Windows operating system installed on the physical host.



&#x20;**Verify the Linux installation**



1\. Log in using the username and password created during installation.

2\. Open the terminal if it is not already visible.

3\. Run:



```bash

uname -a

```



4\. Then run:



```bash

cat /etc/os-release

```



5\. Check that the commands display the Linux kernel and Ubuntu release information.



These commands confirm that the guest operating system has booted successfully and help identify the exact version installed.



\## 5. Create the Windows Virtual Machine



\### Step 8. Start another virtual machine creation wizard



1\. Return to the VMware Workstation main window.

2\. Click \*\*File\*\*.

3\. Select \*\*New Virtual Machine\*\*.

4\. Choose \*\*Typical (recommended)\*\*.

5\. Click \*\*Next\*\*.



A second virtual machine is required because the developer needs both Linux and Windows environments for testing.



\### Step 9. Select the Windows ISO



1\. Select \*\*Installer disc image file (ISO)\*\*.

2\. Click \*\*Browse\*\*.

3\. Locate the Windows ISO file.

4\. Select it.

5\. Click \*\*Next\*\*.



The Windows ISO contains the installation files for the Windows guest operating system.



If VMware asks for the Windows version, select the version corresponding to the ISO you downloaded.



\### Step 10. Name the Windows virtual machine



1\. Enter the name `Windows-Test`.

2\. Select a storage location with sufficient free space.

3\. Click \*\*Next\*\*.



Using a separate name and storage location makes it easier to distinguish the Windows guest from the Linux guest.



\### Step 11. Configure the Windows virtual disk



1\. Enter the planned maximum disk capacity: 64GB.

2\. Select the virtual disk storage option.

3\. Click \*\*Next\*\*.



The Windows guest needs its own virtual disk. The capacity must be sufficient for the selected Windows version, updates and applications.



\### Step 12. Configure Windows hardware resources



1\. Open \*\*Customize Hardware\*\*.

2\. Set the planned memory allocation: 4GB.

3\. Set the planned processor allocation: 2 vCPU.

4\. Open \*\*Network Adapter\*\*.

5\. Configure the intended network mode.

6\. Click \*\*Close\*\*.

7\. Click \*\*Finish\*\*.



The Windows VM must have enough resources to operate properly while leaving sufficient resources for the physical host and the Linux VM.



Step 13. Install Windows



1\. Select `Windows-Test`.

2\. Click \*\*Power on this virtual machine\*\*.

3\. Wait for the Windows installer.

4\. Select the language, time and keyboard settings.

5\. Continue with the installation.

6\. Follow the installation prompts.

7\. Select the appropriate Windows edition if asked.

8\. Complete the initial setup.

9\. Create or configure the user account.

10\. Wait until the Windows desktop appears.



Windows is now installed inside the virtual machine and runs independently from the host operating system.



Step 14. Verify the Windows installation



1\. Open the Windows guest.

2\. Press `Win + R`.

3\. Type `cmd`.

4\. Press Enter.

5\. Run:



```cmd

winver

```



6\. Check the installed Windows version.

7\. Then run:



```cmd

ipconfig

```



8\. Check whether the virtual network adapter has an IP address.



These commands verify the Windows version and show the guest's network configuration.



\## 6. Configure and Test Network Connectivity



Both virtual machines must have internet access and must be able to communicate with each other.



\### Step 15. Configure the network adapters



1\. Shut down both virtual machines.

2\. Select the Linux VM in VMware.

3\. Open \*\*Edit virtual machine settings\*\*.

4\. Select \*\*Network Adapter\*\*.

5\. Choose the network mode used for this environment.

6\. Save the settings.

7\. Repeat the same process for the Windows VM.

8\. Start both virtual machines.



NAT is a suitable starting option when the guests need internet access through the host. However, the actual network arrangement must also allow communication between the two guests. If the selected configuration does not provide this, adjust the virtual network settings and test again.



Bridged networking is another option. It connects guests to the physical network, but availability and behaviour depend on the network being used.



\### Step 16. Find the Linux IP address



1\. Open the Ubuntu terminal.

2\. Run:



```bash

hostname -I

```



3\. Write down the IP address shown.



This address identifies the Linux guest on its network.



\### Step 17. Find the Windows IP address



1\. Open Command Prompt inside the Windows VM.

2\. Run:

```cmd

ipconfig

```



3\. Find the active network adapter.

4\. Write down its IPv4 address.



This address identifies the Windows guest on its network.



\### Step 18. Test internet access



On Ubuntu, run:



```bash

ping -c 4 8.8.8.8

```



On Windows, run:



```cmd

ping -n 4 8.8.8.8

```



Check whether replies are received.



A successful response indicates that the guest can reach the external IP address. If the test fails, check the network adapter configuration and whether the network blocks ICMP traffic.



\### Step 19. Test communication between Linux and Windows



First, test from Linux to Windows.



Open the Ubuntu terminal and run:



```bash

ping -c 4 WINDOWS\\\_IP\\\_ADDRESS

```



Replace `WINDOWS\\\_IP\\\_ADDRESS` with the actual IPv4 address of the Windows guest.



Next, test from Windows to Linux.



Open Command Prompt and run:



```cmd

ping -n 4 LINUX\\\_IP\\\_ADDRESS

```



Replace `LINUX\\\_IP\\\_ADDRESS` with the actual IPv4 address of the Ubuntu guest.



Both tests should receive replies. If one test fails, check the IP addresses, network configuration and firewall settings.



Save the actual commands and their outputs in:



`evidence/05-ping-between-guests.txt`



Do not report successful connectivity unless the tests have actually succeeded.





Snapshots provide a way to return to a previous state if something goes wrong during testing.



&#x20;Step 20. Create a Linux snapshot



1\. Start VMware Workstation.

2\. Select `Ubuntu-Test`.

3\. Open the \*\*Snapshot\*\* menu.

4\. Select \*\*Take Snapshot\*\*.

5\. Enter the name `clean-install-linux`.

6\. Add a description explaining that this snapshot represents the clean Linux installation.

7\. Confirm the snapshot.



The snapshot provides a recovery point before further changes are made to the Linux guest.



&#x20;Step 21. Create a Windows snapshot



1\. Select `Windows-Test`.

2\. Open the \*\*Snapshot\*\* menu.

3\. Select \*\*Take Snapshot\*\*.

4\. Enter the name `clean-install-windows`.

5\. Add a description explaining that this snapshot represents the clean Windows installation.

6\. Confirm the snapshot.



The Windows guest requires its own snapshot because it has a separate virtual disk and operating system state.



&#x20;Step 22. Verify the snapshots



1\. Open Snapshot Manager for the Linux VM.

2\. Confirm that `clean-install-linux` appears.

3\. Open Snapshot Manager for the Windows VM.

4\. Confirm that `clean-install-windows` appears.



The snapshots should be visible in VMware before the test environment is considered ready.



# Troubleshooting



If a virtual machine does not start, check that the ISO file is selected correctly and that the host has enough available resources.



If Ubuntu or Windows has no internet access, check the Network Adapter settings and confirm that the virtual network is connected.



If the Linux and Windows guests cannot communicate, verify their IP addresses and confirm that they are connected to a compatible virtual network. Also check whether the guest firewall blocks ping requests.



If a virtual machine becomes unstable after testing, use its snapshot to return to the saved state. Remember that restoring a snapshot discards changes made after that snapshot.



Record the actual problem encountered during this build, the cause you identified, the correction you made and the test that confirmed the problem was resolved.



# Final Checks



Before using the test environment, confirm that:



1\. The Ubuntu Server VM starts and allows login.

2\. The Windows VM starts and allows login.

3\. Both guests have internet access.

4\. Linux can communicate with Windows.

5\. Windows can communicate with Linux.

6\. The resource settings are recorded.

7\. The Linux snapshot exists.

8\. The Windows snapshot exists.

9\. The evidence files are saved in the project's `evidence` directory.



The environment is ready for testing only after these checks have been completed.

