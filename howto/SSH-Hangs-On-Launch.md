
### SSH Hangs On Launch

I've been having a strange issue with SSH for the last year or so. I've tried looking for answers a while ago but never made much progress and eventually I did give up. What was happening was that I could connect to the Raspberry Pi via SSH. I would then be prompted for a username and password as usual, but then once I typed in the password and hit enter nothing happened. So the SSH session seemed to be hanging after we had completed authentication. It just sat there and wouldn’t respond to any input at all. One had to eventually close the session window. A real strange issue indeed and something that has stumped me for months. 

Not having SSH was tough because file transfers between my Raspberry Pi hosts now were a lot more painful than ever before. Previously I could just transfer files over SCP but now I had to upload them to one of my servers on the internet, move the files onto the Apache Document Root and then download the files via HTTP/S onto the Raspberry Pi. I eventually decided that this was really stupid and a thoroughly in-efficient way of working. So I set out to find a solution to the issue. 


### What Could The Issue Be

This information below has been sourced from the blogs at [Express Hosting](https://expresshosting.net/ssh-hanging-authentication/). Head over to the website for the original article.

* After thorough investigation we realized that it could be a combination of a few different issues. 
* One the latest version of SSH installed on the Raspberry Pi uses QoS headers to ensure speedy delivery of packets over the network. 
* For interactive connections (standard shell SSH connections) it sets the IP header for IP_TOS to be 0x10 (low delay or latency). 
* For non-interactive connections (scp, etc) it sets the IP header for IP_TOS to be 0x08 (max throughput).
* The problem in our case seems to be that our network router doesn’t really like those values set on the packet headers. We aren’t sure if this issue is with the router itself, or something in between. 
* Since this connection is occurring over WiFi and our router handles the Wifi, we suspect that the router is where the issue lies though.
* In summary the wireless router was having issues managing the Quality Of Services on the SS, SSHD packets. 
* Additionally, we were able to determine that this impacted both SSH and SSHd, so both incoming and outgoing SSH connections were impacted by this issue.


### Fixing The SSH Issue

* The work around to the issue is pretty simple and requires modification of two of the SSH configuration files. So let's get going. 
* Open up the following two SSH configuration files in your favorite text editor on the Raspberry Pi :
  > `bash# vim /etc/ssh/ssh_config`
  > `bash# vim /etc/ssh/sshd_config`
* To both of the configuration files you will need to add the following entries at the bottom of the file on a new line -
  > `IPQoS 0x00`
* Once done please restart the sshd service on the Raspberry Pi using the following comand - 
  > `bash# sudo service sshd restart`
* The configuration changes made will modify the TOS value sent out by SSH and SSHD. This should prevent the router from going beserk and causing the connection to hang. 


Hopefully you've found the above information useful. Thanks to the folks at Express Hosting for figuring this out for us. 
Enjoy !!!

