# Ticket 1 — Test Machine for a New Developer



# 1\. What Was Asked



The request was received from Aigerim T., Office Manager.



> Hi, we have someone starting on Monday and he needs a test computer  

> set up. Nothing special, just so he can try things without breaking  

> anything. Can you write down how to do it so I can do the next one  

> myself? Thanks



The request was to prepare a test computer for a new developer and document the setup process so that the Office Manager could repeat it independently. The main goal was to provide an environment where the developer could experiment without damaging the main computer or its existing files.



# 2.What Was Actually Needed



The original request did not contain enough technical information to build the test environment without making some assumptions. It did not specify which operating systems were required, how much memory or disk space should be allocated, which virtualization software should be used, or whether the virtual machines needed to communicate with each other and access the internet.



Before starting, I would ask which operating systems the developer needs, what applications or tools will be used, and whether the test environment must be isolated from the office network. I would also confirm the available hardware resources of the host computer and whether the organization has valid installation media and licences for the required operating systems.



For this task, I assumed that the test environment should contain two virtual machines: one running Linux and one running Windows. I used VMware Workstation as the hypervisor. I also assumed that both virtual machines should have internet access and be able to communicate with each other. Virtual machines were chosen instead of installing the operating systems directly on the host because they provide separation from the main system and allow the environment to be restored using snapshots.



The request says that the setup should be “nothing special”, but a working test environment still requires decisions about networking, resource allocation, storage, and recovery. These settings are important because an incorrect configuration could make the virtual machines too slow, prevent them from communicating, or expose them to a network where they should not be accessible.



# 3.What I Did



First, I checked the host computer's available hardware resources, including its physical memory and available disk space. These figures were used to decide how much RAM, CPU capacity, and storage could be assigned to the virtual machines without making the host computer unusable. The host computer had \[insert actual RAM amount] of RAM and \[insert actual available disk space] of available disk space.



Next, I prepared the installation media for both operating systems and opened VMware Workstation. I created a new virtual machine for Linux and selected the appropriate installation image. During the setup, I configured the virtual machine's name, processor, memory, virtual disk, and network adapter. I chose these settings according to the host computer's available resources and the requirements of the guest operating system.



After creating the Linux virtual machine, I installed the operating system and checked that it started correctly. I then repeated the process to create a separate Windows virtual machine. Keeping the systems in separate virtual machines makes it possible to test software in one environment without directly changing the other environment or the host operating system.



I configured the network adapters so that both guests could access the internet and communicate with each other. I then checked the IP addresses of both virtual machines and tested connectivity using the `ping` command. The actual results of these tests are saved in the evidence folder.



After confirming that the virtual machines worked, I created snapshots. A snapshot provides a restore point that can be used to return a virtual machine to an earlier state if an experiment causes problems. This is useful for a test machine because the developer can try different configurations without having to reinstall the operating system every time.



One issue I encountered during the setup was \[describe the actual problem you encountered]. I resolved it by \[describe the actual solution]. After making this correction, I repeated the relevant test to check that the problem was fixed.



The detailed installation and configuration procedure is documented in `BUILD.md`. It is written so that another person can follow the instructions and recreate the two virtual machines.



# 4.Evidence



The `evidence` folder contains the files collected during the setup and testing process. The file `01-new-vm-wizard.png` shows the virtual machine creation wizard and provides evidence of the initial configuration. The file `02-disk-settings.png` shows the virtual disk configuration and documents the storage settings selected for the virtual machine. The file `03-network-adapter.png` shows the network adapter configuration used for connectivity.



The file `04-guest-uname.txt` contains the output of the Linux `uname` command and information about the installed Linux system. It helps verify which operating system is running inside the Linux virtual machine. The file `05-ping-between-guests.txt` contains the ping commands and their actual results. It is used to demonstrate whether the two virtual machines can communicate with each other. The file `06-snapshot-list.png` shows the available snapshots and provides evidence that restore points were created.



# 5\. What I Would Do Differently



If I repeated this task, I would clarify the requirements with the requester before creating the virtual machines. In particular, I would confirm which Linux distribution and Windows version are required, how much storage and memory the developer needs, and whether the test environment should be isolated from the office network.



I would also test the networking configuration earlier in the process, immediately after installing the operating systems. This would make it easier to identify connectivity problems before completing the rest of the configuration. Finally, I would ask another person to follow `BUILD.md` from the beginning without additional help. Their feedback would help identify unclear instructions and improve the document so that the next setup can be completed independently.

