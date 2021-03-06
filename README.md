# Installing Ubuntu 14.04 and Windows 7/8/10 in Dual-boot Mode

## Installation Guide

Revision History
Rev 1.00 (December 10, 2016)
* Initial release.



## 1. Introduction
This document describes how to set up a “dual-boot” configuration on your system for Windows® and Ubuntu. Each operating system is installed and configured on a different partition.Please contact your AMD Field Applications Engineer or technical representative with any questions about this document.


## 2. Installation Requirements
Before you begin the installation process, make sure that there is adequate space on your system's hard disk and that the following prerequisites are met:
* Boot mode is set to Native UEFI 
* Internet connection is available 
* Installation media is available:  * Windows® 7/Windows® 8 installation disc  * Ubuntu 14.04 LTS installation disc (also available for download from[http://www.ubuntu.com](http://www.ubuntu.com))

## 3. Installation ProceduresThe following procedures describe how to install both Windows® and Ubuntu on your system. When both operating systems are correctly installed, a dual-boot menu should appear each time you start your system.

### 3.1 Installing Windows®Complete the following steps to install Windows. For more detailed installation instructions, see the documentation that is available with your operating system.

1. Insert the Windows installation CD into the CD-ROM drive, open Boot Manager, and boot your system using the UEFI CDROM option as shown below.

2. Select the appropriate language and click Next.

3. When prompted, select to install Windows only.

4. Delete all existing partitions, leaving the whole hard disk empty, and click Next.
5. Create a new partition that is half the size of the hard disk.
6. Click OK to allow additional partitions to be created by Windows as needed.
7. MakesurethattheRecovery,System,MSR,andPrimarypartitionshavebeen created, and click Next to continue with the installation.
8. Complete all remaining installation steps until Windows is fully set up and running.

### 3.2 Installing UbuntuComplete the following steps to install Ubuntu. For more detailed installation instructions, see the documentation that is available with your operating system.
1. Insert the Ubuntu installation CD into the CD-ROM drive, open Boot Manager, and boot your system using the UEFI CDROM option as shown below.

2. Select to install Ubuntu.
3. Select the appropriate language and click Continue.
4. When prompted, click Continue to prepare the installation.
5. Select an installation type of Something else and click Continue.
6. Create a partition for the installation by clicking free space followed by Add.
7. In the Use as field, select swap area. Specify a partition size that is the same as your physical memory size, e.g., 4096.
8. When the swap partition is created, it should appear as shown below. Create another partition by clicking free space followed by Add.9. In the Use as field, select the Ext4 option and select / as the Mount point. Specify all remaining space as the partition size.10. When the Ext4 partition is created, it should appear as shown below. Click Install Now to begin the installation.
A status bar appears at the bottom of the window during installation as shown below.
11. When prompted, select your nearest location and click Continue.
12. Select the appropriate keyboard layout and click Continue.
13. Provide your credentials as needed and click Continue.
14. Once the installation is complete, remove the installation CD and press Enter to restart your system.
15. In the GRUB boot screen, select Ubuntu (Linux). Do not enter recovery mode.
16. When Ubuntu boots to GUI mode, as shown below, press Ctrl + Alt + F1 to switch to text mode.
17. When in text mode, enter your credentials username and password as required.
18. Type sudo passwd root to change the root password.
19. Type su - to switch to root user.
  * Note: All steps from this point must carried out by the root user. If the system restarts, make sure that you log on to the system with as the root user.20. Do one of the following:
  ➭ Type grub-probe --target=fs_uuid /boot/efi/efi/Microsoft/Boot/ bootmgfw.efi and record the output (for example, “EC8F-14C6” as shown below).

  ➭ Type ls /dev/disk/by-uuid/ -l and record the output (for example, “EC8F-14C6” which points to “../../sda2” as shown below).
  
21. Type “nano boot/grub/grub.cfg” and do the following:
  ➭ Find the first instance of menuentry and insert the following before it:         menuentry ‘Windows UEFI’ {            search --fs-uuid --no-floppy --set=root EC8F-14C6            chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi}
  ➭ Replace “EC8F-14C6” with the output recorded in the previous step.
    ➭ Press Ctrl + X to exit and press Y to save your changes.
  
22. Reboot your system. The dual-boot menu should now appear.
