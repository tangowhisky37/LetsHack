
### Raspberry Pi Drops SSH Connections From Remote Hosts

* This is an issue i noticed recently on a Raspbery Pi 2 which was recently upgraded. 
* As part of the upgrade I meant to pull out the older SD card (8 GB) and install a new larger SD Card (32 GB) with the latest version of the Raspbian Operating System on it. 
* Tihe upgrade of the Raspberry Pi went through without a hitch. On reboot I was able to configure the Raspberry Pi to connect to the local wireless network. So everything was running as expected......except ofcourse SSH!!!
* However, whenever I tried to SSH to this new Raspberry Pi over SSH from another Raspberry Pi (on the local network connected via wireless) the SSH client on the other end fails with the error "Connection closed by X.X.X.X". 
* On the Raspberry Pi SSH server logs (/var/log/auth.log), I would see numerous error messages:
  > `sshd error: could not load host key.`

### Root Cause Analysis Suggests.......

* On the SSH client side when you attempt to SSH to the affected Raspberry Pi remote host, you don't quite get to the login screen. Instead your SSH connection is closed right away with the following  message: 
  > `Connection closed by XXXX`  or
  > `Connection reset by XXXX`
* On the affected Raspberry Pi within the system logs, one can see the following error messages (Logfile - /var/log/auth.log on Raspbian) - 
```
Oct 16 08:59:45 openstack sshd[1214]: error: Could not load host key: /etc/ssh/ssh_host_rsa_key
Oct 16 08:59:45 openstack sshd[1214]: error: Could not load host key: /etc/ssh/ssh_host_dsa_key
Oct 16 08:59:45 openstack sshd[1214]: error: Could not load host key: /etc/ssh/ssh_host_ecdsa_key
Oct 16 08:59:45 openstack sshd[1214]: fatal: No supported key exchange algorithms [preauth]
```
* The root cause of this problem is that sshd daemon somehow is not able to load SSH host keys.
* When OpenSSH server is first installed on Raspbian system, SSH host keys should automatically be generated for subsequent use as part of the SSH server post installation process. 
* If, however, key generation was not finished successfully, that can cause SSH login problems similar to what we see here.

### Fixing The Issue

* Let's go ahead and fix the issue by manually creating the SSH keys. The steps are simple but a bit tedious. Watch out for typos. In-correct spelling mean that SSH will continue to complain about missing keys.
* Issue the following commands to create all the required keys. The following command creates the RSA key.
  > `bash# sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key`
* The following command creates the DSA key.
  > `bash# sudo ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key`
* The following command creates the ECDSA key.
  > `bash# sudo ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key`
* Finally the following command creates the ed25519 key.
  > `bash# sudo ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key`
* Once you've created all the above keys, it's time to re-start the SSH server with the following command - 
  > `bash# sudo service ssh restart`
* You should now be able to login from over the network onto the Raspberry Pi. 
* This issue could also occur on other Linux distributions. It just so happens that I experienced this issue on my Raspberry Pi that runs Raspbian Linux which is based off Debian.

Happy Hacking!!!
