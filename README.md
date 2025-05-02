# active-directory-homelab

## Overview:
This is a virtualized homelab where I used VirtualBox, Windows Server 2022, Windows 10 Pro to simulate a corporate Active Directory system. Below will be a loose step-by-step process of setting up the AD DS and its configurations.

## Installation and Setup:
- VMware/VirtualBox (I used VirtualBox)
- Windows 10 ISO File (free on Microsoft)
- Windows Server 2022 ISO File (Also free)
- 16 GB of RAM
- Recommended 100 GB of dedicated storage for the VMs

## Step 1: Setting Up VirtualBox
- Make sure you install VirtualBox or your preferred hypervisor.
- Install it and run VirtualBox
- ![image](https://github.com/user-attachments/assets/38f7088c-6351-4576-acad-d9a8c516d07f)
- Click on **New**

## Step 2: Creating the VM
- ![image](https://github.com/user-attachments/assets/0e9d7ad6-e982-4610-9e4c-7888f9ca37f2)
- Configure the name, select the correct ISO image, and make sure you select **Windows Server 2022 Desktop Experience** after you selected the Windows Server 2022 ISO image.
- Make sure you have enough RAM and Storage, I recommend 4 GB of RAM and 60 GBs of storage.

## Step 3: Run the VM
- The screen should bring you to the installation screen. This should take about 10-15 minutes and a product key is not needed as we are just using it as a homelab and a trial version will be used.

## Step 4: Setting up NIC for Server
- After you installed everything and you are in the Windows home screen, make sure you **Power Off** the VM. It should not be in a **Saved State** or left running.
- Select the Server VM in VirtualBox and click on Settings
- ![image](https://github.com/user-attachments/assets/be81fc6c-84c6-4c7c-94a7-818d5af7f137)
- This settings window should pop up and on the left side, click on Network.
- Make sure Adapter 1 is **Attached to: NAT**
- Click on Adapter 2 and click **Enable Network Adapter**
- ![image](https://github.com/user-attachments/assets/8088ab03-caf2-42a7-a791-9b11c40b8e38)
- Your internal network name can be anything, as long as these settings match.
- Verify that the NICs are registered in the **Network and Internet** Control Panel Applet.
- ![image](https://github.com/user-attachments/assets/67bb52e4-766c-4ba5-8075-744a4e5446d3)
- You can rename for convenience purposes.
## Step 5: Configure NIC settings
- Right click on your Internal Network Adapter -> Properties -> Internet Protocol Version 4 (TCP/IPv4) Click on it
- ![image](https://github.com/user-attachments/assets/5e75eb23-1880-4ed5-bd28-734f7fbb54bc)
- These are the settings I used from my Network Topology diagram. You can use your own, just make sure you test them.


  

