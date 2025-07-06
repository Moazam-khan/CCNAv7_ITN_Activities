Packet Tracer - Implement Basic Connectivity
Overview
This Packet Tracer activity focuses on configuring basic connectivity for two Cisco switches (S1 and S2) and two PCs (PC1 and PC2). The tasks include setting up hostnames, passwords, and MOTD banners on the switches, assigning IP addresses to devices, and verifying connectivity using ping commands.
Addressing Table



Device
Interface
IP Address
Subnet Mask



S1
VLAN 1
192.168.1.253
255.255.255.0


S2
VLAN 1
192.168.1.254
255.255.255.0


PC1
NIC
192.168.1.1
255.255.255.0


PC2
NIC
192.168.1.2
255.255.255.0


Objectives

Part 1: Perform a Basic Configuration on S1 and S2
Part 2: Configure the PCs
Part 3: Configure the Switch Management Interface

Background
This activity involves creating a basic switch configuration, assigning IP addresses to switches and PCs, verifying configurations with show commands, and testing connectivity using ping. Switches forward traffic based on MAC addresses and can operate as plug-and-play devices, but IP addresses are configured for management purposes.
Instructions
Part 1: Perform a Basic Configuration on S1 and S2

Configure Hostname on S1:
Click S1, go to CLI tab, and enter:enable
configure terminal
hostname S1




Configure Passwords on S1:
Console password:line console 0
password cisco
login
exit


Privileged EXEC password:enable password class




Verify Passwords:
Question: How can you verify that both passwords were configured correctly?
Exit to user EXEC mode (exit) and attempt to access privileged EXEC mode with enable. Enter class to verify the privileged EXEC password. Log out and log back in via console to verify the cisco password is prompted.




Configure MOTD Banner:
Set a banner to warn unauthorized access:banner motd #Authorized access only. Violators will be prosecuted to the full extent of the law.#




Save Configuration:
Save to NVRAM:write memory


Question: Which command do you issue to accomplish this step?
write memory or copy running-config startup-config




Repeat for S2:
Repeat steps 1–5, replacing S1 with S2 for the hostname.



Part 2: Configure the PCs

Configure IP Addresses:
For PC1:
Click PC1, go to Desktop tab > IP Configuration.
Set IP Address: 192.168.1.1, Subnet Mask: 255.255.255.0.


For PC2:
Click PC2, go to Desktop tab > IP Configuration.
Set IP Address: 192.168.1.2, Subnet Mask: 255.255.255.0.




Test Connectivity:
On PC1, go to Desktop > Command Prompt, and ping S1:ping 192.168.1.253


Question: Were you successful? Explain.
The ping may fail because S1’s VLAN 1 interface is not yet configured with an IP address or is in a down state. Configuration in Part 3 resolves this.





Part 3: Configure the Switch Management Interface

Configure IP Address on S1:
Enter the following commands:configure terminal
interface vlan 1
ip address 192.168.1.253 255.255.255.0
no shutdown
exit


Question: Why do you enter the no shutdown command?
The no shutdown command activates the VLAN 1 interface, bringing it to an up state for IP connectivity.


Question: Why configure an IP address on a switch?
An IP address is used for remote management (e.g., SSH, Telnet) and monitoring, not for data forwarding, which relies on MAC addresses.




Configure IP Address on S2:
Repeat the commands for S2, using IP address 192.168.1.254:configure terminal
interface vlan 1
ip address 192.168.1.254 255.255.255.0
no shutdown
exit




Verify IP Configuration:
Use show ip interface brief or show running-config to confirm IP addresses and interface status.


Save Configurations:
Save to NVRAM:write memory


Question: Which command is used to save the configuration file in RAM to NVRAM?
write memory or copy running-config startup-config




Verify Network Connectivity:
From PC1 Command Prompt, ping:
PC2: ping 192.168.1.2
S1: ping 192.168.1.253
S2: ping 192.168.1.254


Repeat from PC2 or switch CLI. All pings should succeed (100% success after the first attempt). If a ping fails, recheck configurations for errors.



Conclusion
This activity demonstrates configuring hostnames, passwords, and MOTD banners on Cisco switches, assigning IP addresses to switches and PCs, and verifying connectivity. Successful pings confirm proper configuration, preparing users for basic network setup and management tasks.