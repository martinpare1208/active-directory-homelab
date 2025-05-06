# active-directory-homelab

## Overview:
This is a virtualized homelab where I used VirtualBox, Windows Server 2022, Windows 10 Pro to simulate a corporate Active Directory system. Below will be a loose step-by-step process of setting up the AD DS and its configurations.

## Installation and Setup:
- VMware/VirtualBox (I used VirtualBox)
- Windows 10 ISO File (free on Microsoft)
- Windows Server 2022 ISO File (Also free)
- 16 GB of RAM
- Recommended 100 GB of dedicated storage for the VMs

## Network Topology Used
- ![Network Topology](https://github.com/user-attachments/assets/948b6076-d61d-423e-859a-5f9fc3caa51a)



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

## Step 6: Installing the AD DS
- Go to server manager which should be located on your task bar.
- ![image](https://github.com/user-attachments/assets/3b0c70cb-155f-450d-b690-ce9fcf61781f)
- Click on Add roles and features
- Follow the settings configurations on each screenshot when clicking Next
- ![image](https://github.com/user-attachments/assets/9bf871a8-008a-4e89-9972-f5c178b4d0fd)
- ![image](https://github.com/user-attachments/assets/d0c90981-8cea-47eb-8492-429796030b14)
- Keep in mind your server name can be different, as long as you see your own, select it.
- ![image](https://github.com/user-attachments/assets/04efc61d-d52a-4e18-82ff-1e6ee54eb20b)
- ![image](https://github.com/user-attachments/assets/d73bc153-1c1a-4131-82aa-9f4358d82fa7)

- Keep clicking Next until you get to this screen.
- ![image](https://github.com/user-attachments/assets/9c205891-307e-4ee5-8145-bff97dbef74d)
- Then click on **Install**.

## Step 7: Configuring the AD DS Controller
- After finishing the installation, go to the top right of the server manager and click on the flag with a triangle icon.
- ![image](https://github.com/user-attachments/assets/ac0af2d8-ed03-4ca0-8978-b3ca4b9dde30)
- **Select Promote this server to a domain controller**
- ![image](https://github.com/user-attachments/assets/6b5eff0b-570b-430f-8978-e1fee5a91b33)
- ![image](https://github.com/user-attachments/assets/3c3cc07b-0da0-4460-9780-c6e5c9841baf)
- Follow the configurations, you can choose whatever domain name you want, just remember and document your configurations.
- ![image](https://github.com/user-attachments/assets/c1534fcd-2255-4605-b9e5-76889ef21238)
- Choose any password and document it.
- Follow the configurations.
- ![image](https://github.com/user-attachments/assets/1a886d57-0ee5-4140-9d39-44471288da65)
- ![image](https://github.com/user-attachments/assets/9e031b8a-d5c8-48d4-8e85-a76ccace4f6c)
- ![image](https://github.com/user-attachments/assets/74fd9633-4991-4800-a342-ec868cfddc97)
- ![image](https://github.com/user-attachments/assets/6e64fbf7-a12b-4191-9188-e413cc88a71d)
- Click on **Install**. This will restart the VM.
- After restarting, go to the Windows Logo, then click on Windows Administrative tools and you should see all of the AD DS tools that have been installed. This means the installation was successful.
- ![image](https://github.com/user-attachments/assets/aa9dad9e-67bb-4678-bd8b-37bf046f76f1)
- This is how to get your AD DS up and running. Refer to your AD DS documentation of the corporate architecture.

## Step 8: Adding RAS / NAT to allow our virtual network to have Internet Connectivity
- Follow these configurations using the Add Roles and Features Wizard in Server Manager
- ![image](https://github.com/user-attachments/assets/f5ac0e03-b009-4085-a3c8-f2bf1793c32a)
- ![image](https://github.com/user-attachments/assets/f15c864d-6fcb-459d-9147-10a35884582b)
- After it is finished installing, go to the top right and click on the flag icon with the triangle and click on **Open the Getting Started Wizard**
- ![image](https://github.com/user-attachments/assets/1ab84a07-4d0b-4a90-8ef5-285cb29315ea)
- After that, go to top right and click on **Tools** and scroll down and select **Routing and Remote Access**
- ![image](https://github.com/user-attachments/assets/2dee0600-b40d-4010-b177-09e90a73a19b)
- Right click on the (local) machine and click on **Configure and Enable Routing and Remote Access**
- ![image](https://github.com/user-attachments/assets/56bdeb68-de6d-4b8b-8a21-a9ded5d0255e)
- Select **Network Address Translation (NAT)**
- Select your internet NIC Adapter.
- ![image](https://github.com/user-attachments/assets/d57fcc09-8e99-4c6f-a229-deee6fc46e30)
- After finishing the installation, you can now select the dropdown of your local machine in the Routing and Remote Access window.
- ![image](https://github.com/user-attachments/assets/4ae73ac4-4274-4d57-b877-b5a445466eb6)

## Step 9: Setting up DHCP to allow our Workstations to have internet access
- Go back to dashboard and "Add roles and features"
- ![image](https://github.com/user-attachments/assets/00b183a6-9ccc-4063-ba4e-1b6dbaa28830)
-  Select DHCP Server and install.
-  Complete the Post-Install Deployment Configuration (The flag with the triangle icon again). Use whatever configurations, just document them.
-  ![image](https://github.com/user-attachments/assets/76cca70c-a555-41ae-a7c1-f675c9627f6b)

-  ![image](https://github.com/user-attachments/assets/f5c4ee93-35e8-4357-a615-e59940aba5ca)
-  After installation, go to Tools -> DHCP
-  ![image](https://github.com/user-attachments/assets/6640be19-98dc-41a7-826d-86000ec8c8eb)
-  Right click IPv4 -> New Scope
-  Use whatever configuration you have, I am following my own network topology graph.
-  Your DHCP server is now setup.

## Step 10: Launch your Windows 10 Pro/Enterprise VM
- I am assuming that you already setup your Win 10 Pro/Enterprise Workstation VM.
- If you are not getting internet, then check your VM's network adapter and that the server is running.

## Step 11: Join the Domain
- Right click on the Windows Start Icon -> System
- ![image](https://github.com/user-attachments/assets/eada1c1c-9666-4d8b-847d-eb06a14fc83e)
- Scroll down to **Rename this PC (advanced)** and click on it
- ![image](https://github.com/user-attachments/assets/6b7e0f2c-04ab-4879-94c2-11ffe0c5b910)
- Click on **Change**
- ![image](https://github.com/user-attachments/assets/38c4f147-6d92-44c7-b887-3ef77b5ed635)
- Then put in your configurations, refer back to your documentation, topology, etc.
- ![image](https://github.com/user-attachments/assets/8fc9b3e2-3d8e-456e-8a6a-742462798be2)
- A window will pop up to use an authenticated and authorized account in the domain. Put in your username and password.
- ![image](https://github.com/user-attachments/assets/b1909d15-9580-4920-9699-1b120ba1f3e7)
- When successful, a confirmation window shows that you have joined the domain.
- Congratulations, you have created a Windows 10 Active Directory Server using Windows Server 2022 and implemented a workstation to the domain.





