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

## banner motd
-legally binding logon banner; incase someone tries to access devices without authorization.
-banner motd for inline; #banner motd $ do not log on $ where '$' is the delimiting character.
-banner motd for a text editor for a longer motd #banner motd % insert longer message here % where '%' is the delimiting character.

## mac addresses

- show mac address-table 8dfb.f9cf.fb1a - filters for known specific addresses
- show mac address-table fa0/1 - filters mac addresses connnected to that particular interface
- show spanning tree - loop prevention mechanism that mitigates an occurence of a [broadcast storm](https://en.wikipedia.org/wiki/Broadcast_storm#:~:text=A%20broadcast%20storm%20or%20broadcast,unable%20to%20transport%20normal%20traffic.)

## Power over Ethernet(PoE)
Can be powered through a PoE switch(endspan) or power injector(midspan)<br>
Used for powering devices such as VoIP phones, wireless access point(WAP) and security cameras. uses 802.3AF to release 15.4 watts or with devices getting more hungry for power there's the 802.3at that churns out, wait for it.....25.5 watts.

The following configurations is used to setup and troubleshoot PoE;
- show power line - shows available, used and remaining power on the switch, helps you know the limit reached on the amount of power on the switch for planning purposes<br>
- power inline ? - consumption adjusts consumption of power on a device never for troubleshooting device incase it freezes(basically switching on/off) auto - reboots

## VLANS & ROUTER ON A STICK
creating vlans.<br>
VLANS creates a security boundary, by way of segmenting the network.<br>
By default, the ports are set to dynamic mode.You should set this to access mode.<br>
the dynamic trunking protocol will be susceptible to a [VLAN hopping attack](https://www.techtarget.com/searchsecurity/definition/VLAN-hopping).

- switchport mode access, switchport mode access vlan 10; will deter any unauthorised device from becoming a trunk port and having full access to add vlans and setup ports to whatever vlans they want.Therein lies breach of security

![vlans](https://github.com/vic-rono/CCNA/assets/61822296/c134cb42-414e-4597-91fb-3767ed5a8e36)

Configurations for PCs through gns3's VCPS - IP address, mac address and default gateway. Oh for computers connected on VLan 10 (they are pingable)
![pingable](https://github.com/vic-rono/CCNA/assets/61822296/91198dcf-98a8-4176-a5e9-159fb92f4f9f)

## Configuring router on a stick(trunking)
- To enable communication between router and a switch, so that the various vlans can be able to communicate. This is a layer 3 thing        hence the need to setup trunking 
- Vlan 10 will be able to communicate with vlan 20 with sub-interfaces created in the router.
- Trunking uses 802.1Q encapsulation to enable trunking.

![TRUNK](https://github.com/vic-rono/CCNA/assets/61822296/87a435ba-2b0b-4161-9e44-d718e52cba05)





