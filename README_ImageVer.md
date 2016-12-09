# Installing Ubuntu 14.04 and Windows 7/8/10 in Dual-boot Mode

## Installation Guide

Revision History
Rev 1.00 (December 2, 2015)
* Initial release.



## 1. Introduction
This document describes how to set up a “dual-boot” configuration on your system for Windows® and Ubuntu. Each operating system is installed and configured on a different partition.
Please contact your AMD Field Applications Engineer or technical representative with any questions about this document.


## 2. Installation Requirements
Before you begin the installation process, make sure that there is adequate space on your system's hard disk and that the following prerequisites are met:
* Boot mode is set to Native UEFI 
* Internet connection is available 
* Installation media is available:
  * Windows® 7/Windows® 8 installation disc
  * Ubuntu 14.04 LTS installation disc (also available for download from
[http://www.ubuntu.com](http://www.ubuntu.com))

## 3. Installation Procedures
The following procedures describe how to install both Windows® and Ubuntu on your system. When both operating systems are correctly installed, a dual-boot menu should appear each time you start your system.

### 3.1 Installing Windows®
Complete the following steps to install Windows. For more detailed installation instructions, see the documentation that is available with your operating system.

1. Insert the Windows installation CD into the CD-ROM drive, open Boot Manager, and boot your system using the UEFI CDROM option as shown below.![1](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/1.png)

2. Select the appropriate language and click Next.![2](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/2.png)

3. When prompted, select to install Windows only.
![3](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/3.png)

4. Delete all existing partitions, leaving the whole hard disk empty, and click Next.![4](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/4.png)
5. Create a new partition that is half the size of the hard disk.![5](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/5.png)
6. Click OK to allow additional partitions to be created by Windows as needed.![6](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/6.png)
7. MakesurethattheRecovery,System,MSR,andPrimarypartitionshavebeen created, and click Next to continue with the installation.![7](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/7.png)
8. Complete all remaining installation steps until Windows is fully set up and running.![8](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/8.png)

### 3.2 Installing Ubuntu
Complete the following steps to install Ubuntu. For more detailed installation instructions, see the documentation that is available with your operating system.

1. Insert the Ubuntu installation CD into the CD-ROM drive, open Boot Manager, and boot your system using the UEFI CDROM option as shown below.![9](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/9.png)

2. Select to install Ubuntu.![10](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/10.png)
3. Select the appropriate language and click Continue.![11](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/11.png)
4. When prompted, click Continue to prepare the installation.![12](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/12.png)
5. Select an installation type of Something else and click Continue.![13](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/13.png)
6. Create a partition for the installation by clicking free space followed by Add.![14](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/14.png)
7. In the Use as field, select swap area. Specify a partition size that is the same as your physical memory size, e.g., 4096.![15](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/15.png)
8. When the swap partition is created, it should appear as shown below. Create another partition by clicking free space followed by Add.![16](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/16.png)
9. In the Use as field, select the Ext4 option and select / as the Mount point. Specify all remaining space as the partition size.![17](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/17.png)
10. When the Ext4 partition is created, it should appear as shown below. Click Install Now to begin the installation.![18](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/18.png)
A status bar appears at the bottom of the window during installation as shown below.![19](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/19.png)
11. When prompted, select your nearest location and click Continue.![20](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/20.png)
12. Select the appropriate keyboard layout and click Continue.![21](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/21.png)
13. Provide your credentials as needed and click Continue.![22](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/22.png)
14. Once the installation is complete, remove the installation CD and press Enter to restart your system.![23](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/23.png)
15. In the GRUB boot screen, select Ubuntu (Linux). Do not enter recovery mode.![24](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/24.png)
16. When Ubuntu boots to GUI mode, as shown below, press Ctrl + Alt + F1 to switch to text mode.![25](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/25.png)
17. When in text mode, enter your credentials username and password as required.![26](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/26.png)
18. Type sudo passwd root to change the root password.![27](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/27.png)
19. Type su - to switch to root user.![28](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/28.png)
  * Note: All steps from this point must carried out by the root user. If the system restarts, make sure that you log on to the system with as the root user.
20. Do one of the following:
  ➭ Type grub-probe --target=fs_uuid /boot/efi/efi/Microsoft/Boot/ bootmgfw.efi and record the output (for example, “EC8F-14C6” as shown below).![29](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/29.png)

  ➭ Type ls /dev/disk/by-uuid/ -l and record the output (for example, “EC8F-14C6” which points to “../../sda2” as shown below).![30](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/30.png)
  
21. Type “nano boot/grub/grub.cfg” and do the following:
  ➭ Find the first instance of menuentry and insert the following before it:
         menuentry ‘Windows UEFI’ {
            search --fs-uuid --no-floppy --set=root EC8F-14C6
            chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
  ➭ Replace “EC8F-14C6” with the output recorded in the previous step.
  
  ➭ Press Ctrl + X to exit and press Y to save your changes.![31](https://raw.githubusercontent.com/auspbro/Ubuntu-Windows_dual-boot_mode/master/res/31.png)
  
22. Reboot your system. The dual-boot menu should now appear.
