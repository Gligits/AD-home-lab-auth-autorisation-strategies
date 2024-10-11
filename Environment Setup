# Environment Setup

## This environment includes:

Two Windows Server VMs named DC1 and DC2.
One client VM named CL1.

## Potential Issues:
- Client Machine:

-- Issue: If the client VM creation gets stuck at a certain percentage (commonly at 79%), it’s usually due to insufficient hard disk space.

-- Solution: 
Increase the hard disk space to 70GB or 80GB instead of 60GB. If this doesn’t resolve the issue, recreate the VM, and during the creation process, ensure the option "Split virtual disk into multiple files" is selected instead of "Store virtual disk as a single file". This should fix the problem.

- Server Machines (DC1, DC2):

-- Issue: After installing the server VMs, you will need to promote them to domain controllers (Active Directory).
Before doing this, you must ensure the network connection between your host machine (laptop) and the VM is working correctly.

-- Solution:
Check the network status by looking for the laptop icon on the VM’s taskbar. If it shows a red "X," follow these steps on your host machine:
Go to Control Panel > Network and Internet > Network Connections.
You may notice that the VM’s Ethernet connection is not properly configured (this issue is common with VMware Workstation).
Open VMware Workstation Pro (not the Player version) and click on Edit > Virtual Network Editor.
Click Change Settings, then create a new network and name it VMnet2, setting it to Host-Only.
Save everything and return to Network Connections on your host machine, where you should now see a new Ethernet connection for the VM.
Restart VMware Workstation, power on the server, and the network issue should be resolved.
