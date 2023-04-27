# CCNA
Networking repo.

A repo for cisco [ios](https://www.techtarget.com/searchnetworking/definition/Cisco-IOS-Cisco-Internetwork-Operating-System) commands.<br>
Will aid in remembering configurations for IP addressing, VLANS among others (that are complex).

## Process of password recovery (passwordrecovery.txt)

Steps for perfoming password recovery from cisco devices.<br>
- Connect console port (Prolific USB to Serial comm port(COM6))<br>
- Reboot the device and send a break signal (Ctrl + B) within 30 secs, this will break from the normal boot process to get to the rom monitot(ROMON) before it gets to the OS<br>
- Modify the configuration register (from 0x2102 to 0x2142) - will recover previous configuration, reset password and save - the return to 0x2142 and reboot.

## gns3 network simulation

[gns3](https://en.wikipedia.org/wiki/Graphical_Network_Simulator-3) toplogy for metropolitan with Nairobi serving other towns. This is an emulation of the networking infrastructure. It runs on the GNS3 VM (acts as the server) that enables you run and configure cisco devices virtually. In this case i used VMware workstation to run the GNS3 VM. Used the two-tier architecture manifesting in the presence of the core and access switches.<br>

![metro](https://user-images.githubusercontent.com/61822296/233679365-049dea64-2275-4831-938c-61666ac5d776.png)<br>

[PuTTY](https://en.wikipedia.org/wiki/PuTTY) for running cisco ios commands virtually.<br>

![PuTTY](https://user-images.githubusercontent.com/61822296/233679386-593fed53-65da-448b-901f-6f292297a3f8.png)

![gnsVM](https://user-images.githubusercontent.com/61822296/233967056-d4b970cd-6b3d-4662-8b69-4f5377bd1507.png)
<br>
<br>

## Basic IP configuration

Includes;<br>
- Assigning IP addresses to the routers and switches.
- Creating VLANs on switches.
- Assigning hostname. 
- Assigning banner motd.
- logging synchronous on line console 0 to prevent syslog messages that interrupt while typing commands (LINEPROTO-5-UPDOWN: Line protocol on Interface      GigabitEthernet0/0, changed state to up).
- Disabling ip-domain lookup to prevent dns lookup when you encounter an error while typing commands.
- Enabling password on the enable terminal.
- Enabling password on line vty for telnet and SSH communication.
- wr to save changes.


## mac addresses



