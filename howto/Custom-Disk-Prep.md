

## Hacking the Disk Layout on a Raspberry Pi Model A 

This guide was put together while i was assembling 4 Raspberry Pi's for the local Raspberry Pi Hackers group i run. I've had some challenges building the Raspberry Pi A. I used the stock Raspbian distro on a 8 GB SDHC card. The default file system is around ~4GB in size with SWAP around ~128 MB in size. This made working on the Raspberry Pi nearly impossible. Every command would take ages to run and updates to the operating system would run for 20-30 mins as compared to 2-3 ins on a Raspberry Pi 2, or Raspberry Pi 3.  

Also, since the updates ran really slow, i couldn't get any software loaded on it. So I finally decided to re-build the partitions and throw in some additional swap space. The memory on the device was 128MB with SWAP as 128 MB created part of the default install. The intention was to resize the disk partition such that i was able to allocate more space to SWAP. This in my mind would increase the performance of the machine and in reality it did so. 

Please Note - You are responsible for all actions you undertake. If you end up frying your SD card, destroying all your data, loosing all your partitions or evening burning your Pi, you will only have yourself to blame. So use the instructions below with caution. Think before you act and do your homework well. 

The steps to extending the file system and creating a new one are as follows - 

* Backup your system in case of a mistake!
* Use the following command to view partitions - 

> `bash# fdisk /dev/mmcblk0` 

* Carefully note down the start and end sectors for your main partition based on the output of the above command.
* Make sure you have cross checked and double cross checked the sector start/end information.
* Use fdisk to delete the partition, but PLEASE DO NOT reboot.
* Recreate a new partition (similar type i.e. ext4 Linux) but with a larger size starting at the same location as the previous one. I extended mine by another 2 GB to give me a total of 6 GB.
* Create a new SWAP file system. I gave mine ~1GB of space. 
* Reboot to activate the partition changes. You should check to see changes using - 

> `bash# fdisk -l` 

* On rebooting use the following command to enlarge the Linux Root File System

> `bash# resize2fs /dev/mmclk0p2` 

* Some sites recommended using the following command to perform a file system check. This however didn't work for me hence i used the next step.

> `bash# e2fsck -f /dev/mmcblk0p2` 

* If you execute the following command, you will force an fsck at every boot. Just make sure you have the following entry in your /etc/fstab, `/dev/mmcblk0p2	/  ext4	defaults, noatime	0	1`.

> `bash# touch /forcefsck` 

* Create the new SWAP file system by using the following command - 

> `bash# mkswap /dev/mmcblk0p3`

* Configure the /etc/fstab file with the following, `/dev/mmcblk0p3	swap	swap	defaults	0	0`
* Reboot your Raspberry Pi and you should see SWAP auto mounted. 

Here are some additional links to read up to understand how the above process works technically - 

* [Link1](https://www.raspberrypi.org/forums/viewtopic.php?f=51&t=45265)
* [Link 2](https://www.raspberrypi.org/forums/viewtopic.php?f=29&t=86536)
* [Link 3](https://www.raspberrypi.org/forums/viewtopic.php?t=15870&p=884216)

### Hacking the Disk Layout on a Raspberry Pi Model A : Update (180517) -

I've been doing a bit of reading and realized that after all re-partitioning might not be really required to increase SWAP. On the Raspberry Pi one can edit a few configuration files and create SWAP space dynamically. 

* To modify the amount of SWAP space required edit the following file /etc/dphys-swapfile and set the swap file size.

> `bash# vi /etc/dphys-swapfile`

* Once you are done configuring the SWAP size you will need to initilize SWAP using, 

> `bash# sudo dphys-swapfile setup`

* Once initialization is complete you are ready to start SWAP by issuing the following command, 

> `bash# sudo dphys-swapfile swapon`

* To turn off SWAP issue the following command, 

> `bash# sudo dphys-swapfile swapoff`

* Based on some of the reading I've done, some authors recommended against setting up large disk partitions for SWAP. According to these authors this reduced the life of the Raspberry Pi's SD card. 


Thanks!!! Hopefully you've learned something from my experiences including the information documented here. 

