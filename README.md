# Matebook-X-Pro-Hackintosh-latest-update.
Use on par with my guide. Note: Since I've been busy with school lately, r/gnodipacc886 has really taken over this project. The EFI folder here is from the work of him. So if you liked this guide and want to help me, consider donating to him first for all the hard work that he's done. :)

CLOVER install if for the USB installer, and the CLOVER folder is for after you install it. 

Use on par with my Reddit Guide 

Simplified Guide Here:

First we need to be in a mac OS environment, so we  will need to create a virtual machine. Adhere to this guide to get started. If you have a Macbook, you can skip this step.
https://techsviewer.com/install-macos-high-sierra-vmware-windows/

Download the MacOS Mojave Installer from this link: 
https://drive.google.com/file/d/1leeIszys4k_njCghWbVebzzMvNfYvhC1/view
Unzip it and drag it into the applications folder.

We will format the USB correctly with the use of terminal. In terminal, type:

**diskutil list**

Next you will need to put these lines into terminal.
(Replace /dev/disk___ with whatever your disk is located at)

**# repartition /dev/disk1 MBR, two partitions**

**# first partition, "CLOVER EFI" FAT32, 200MiB**

**# second partition, "install_osx", HFS+J, remainder**

**diskutil partitionDisk /dev/disk1 2 MBR FAT32 "CLOVER EFI" 200Mi HFS+J "install_osx" R**

-----------------------------------------------------
Now, we will make the bootloader using this program: https://sourceforge.net/projects/cloverefiboot/


First, click **"Change Install Location"** and change it to **"CLOVER EFI".**


Now, click **"Customize"**


You need to select the following:
**"Install for UEFI booting only"**
Under themes, select "BGM"

Under **Drivers64UEFI** we need to select the following:
**OsxAptioFIxDrv-64.efi**
**ApfsDriverLoader-64.efi**
**VboxHfs-64.efi**


After your done with these, select "Install"

-----------------------------------------------------------------------------------------
When it is done installing, open up the partition on the USB named **"CLOVER EFI"**
We are going to replace the whole folder named **"CLOVER"** with the **CLOVER** from this link:
**BE SURE TO COPY AND PASTE THE CLOVER THAT SAY'S "CLOVER INSTALL"**
Once you replace it, rename it from CLOVER Install to, "Clover"

Now that the bootloader's done, we need to get the Mojave installer on the SSD.
Go back to terminal and input this line:

**copy installer image**
Now we already dragged the installer into the applications folder, but if you missed that, do it now.

**sudo "/Applications/Install macOS Mojave.app/Contents/Resources/createinstallmedia" --volume /Volumes/install_osx --nointeraction**

Then rename it with the line:

**rename**

**sudo diskutil rename "Install macOS Mojave" install_osx**

Now Turn off Safe Boot on your Matebook and boot Clover. 
Now you want to use your arrow keys to move to the partition named 'install_osx" 
Click Disk Utility and reformat the SSD/Hard drive to "Mac OS X Extended (Journaled)"

Once it reboots, choose **Boot macOS install from (Your Partition name)** to finish up the install.

Once you're in, open up the Clover program again and install it to the hard drive. This time you will also include **Install RC scripts on target volume** and **Install all RC scripts on all other boot volumes**
Then just load up the EFI Mounter app, mount the EFI, replace CLOVER, reboot, and you should be good. 
 
 
## Also, if you really want to, you can help me out with a small donation..Thanks!
| Paypal | 
| ------------- | 
| ![Preview](https://github.com/Darrenpan20/Matebook-X-Pro-Mojave-hackintosh-/blob/master/paypal.jpg) |
| https://paypal.me/DarrenPan |
