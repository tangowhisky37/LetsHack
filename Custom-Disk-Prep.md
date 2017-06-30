

### Hacking the Disk Layout on a Raspberry Pi Model A 

- Update (180517) - 
  - I've been doing a bit of reading and realized that after all re-partitioning might not be really required to increase SWAP
  - On the Raspberry Pi one can edit /etc/dphys-swapfile and set the swap file size
  - Then initilize SWAP using "sudo dphys-swapfile setup"
  - Once initialization is complete start SWAP using "sudo dphys-swapfile swapon" and "sudo dphys-swapfile swapoff" to run off SWAP.
  - Some sites suggests setting up SWAP or large amounts of SWAP is not a good idea since it reduces the life of the SD CARD. 

This guide was put together while i was assembling 4 Raspberry Pi's for the local Raspberry Pi Hackers group i run. I've had some challenges building the Raspberry Pi A. I used the stock Raspbian distro on a 8 GB SDHC card. The default file system is around ~4GB in size with SWAP around ~128 MB in size. 

The updates ran really slow and i couldn't get any software loaded on it. So I decided to re-do the partitions and throw in some additinoal swap space. The memory on the device was 128MB with SWAP as 128 MB created part of the default install.

- The steps to extending the file system and creating a new one are as follows - 
  - Backup your system in case of a mistake!
  - Use "fdisk /dev/mmcblk0" to view your partitions. Note down the start and end sectors for your main partition.
  - Make sure you have cross checked and double cross checked the sector start/end information.
  - use fdisk to delete the partition, but do not reboot.
  - Recreate a new partition (similar type i.e. ext4 Linux) but with a larger size starting at the same location as the previous one. I extended mine by another 2 GB to give me a total of 6 GB.
  - Create a new SWAP file system. I gave mine ~1GB of space. 
  - Reboot to activate the partition changes. You should check "fdisk -l" to see the changes.
  - On rebooting use "resize2fs /dev/mmclk0p2" to enlarge the root Linux file system.
  - Some sites recommended using, "e2fsck -f /dev/mmcblk0p2" to perform a file system check. This however didn't work for me hence i used the next step.
  - If you perform the following, "touch /forcefsck" you will force an fsck at every boot. Just make sure you have the following entry in your /etc/fstab, "/dev/mmcblk0p2	/  ext4	defaults, noatime	0	1"
  - Create the new SWAP file system by using, "mkswap /dev/mmcblk0p3". 
  - Configure the /etc/fstab file with the following, "/dev/mmcblk0p3	swap	swap	defaults	0	0"
  - Reboot and you should see SWAP auto mounted. 
  - Links to read - 
    - https://www.raspberrypi.org/forums/viewtopic.php?f=51&t=45265
    - https://www.raspberrypi.org/forums/viewtopic.php?f=29&t=86536
    - https://www.raspberrypi.org/forums/viewtopic.php?t=15870&p=884216

Thanks!!!

