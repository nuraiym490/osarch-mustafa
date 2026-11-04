# Feedback on Nuraiym's BUILD.md



Reviewer: Amira

Commit reviewed: https://github.com/nuraiym490/osarch-mustafa/blob/main/tickets/ticket1-vm-build-doc/BUILD.md

Hypervisor I used: VMware Workstation. Version 17 Pro



## First step where I got stuck

Step number: Step 15

What the step says: Configure the network adapters and choose the network mode used for this environment.

What I did: Checked the network settings for both the Ubuntu and Windows VMs and selected NAT mode.

What happened / what I had to guess: I had to briefly consider whether to use NAT or Bridged networking to ensure both VMs could reach the internet and talk to each other, but the instructions provided helpful guidance pointing out that NAT is a suitable starting option.



## Other places I hesitated

Step 4 (Configure the virtual disk): Had to decide between splitting the virtual disk into multiple files versus storing it as a single file, though the document neatly outlines the trade-offs to help make that choice.



## Settings I would not have chosen without the document

Figuring out the right amount of RAM and CPU to give the virtual machines without slowing down my main computer.



Creating the clean-install-linux and clean-install-windows snapshots right away so I could easily roll back if something broke.



## One thing that worked well

The inclusion of the "Important Terms" section at the beginning set a very clear foundation and made all the setup steps much easier to understand.

