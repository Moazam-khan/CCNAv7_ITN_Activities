Conclusion for Packet Tracer - Basic Switch and End Device Configuration
The configuration of the small LAN was successfully completed as per the provided requirements. Both switches, Room-145 and Room-146, were configured with appropriate hostnames, IP addresses, and subnet masks on VLAN 1 using the Cisco IOS command-line interface (CLI). The specified passwords (8ubRu for all lines and C9WrE as the secret password) were applied, with all clear text passwords encrypted for security. An appropriate message-of-the-day (MOTD) banner was configured to display relevant information. The two host devices, Manager and Reception, were assigned IP addresses according to the addressing table. The running configurations on both switches were saved to ensure persistence. Connectivity between all devices was verified, confirming end-to-end communication across the network. This exercise demonstrated the ability to configure and manage a basic LAN setup effectively.


# Enter global configuration mode
enable
configure terminal

# Set hostname for Room-145
hostname Room-145
# (For Room-146, replace with: hostname Room-146)

# Configure password for console access
line console 0
password 8ubRu
login
exit

# Configure password for VTY (Telnet/SSH) access
line vty 0 4
password 8ubRu
login
exit

# Configure enable secret password
enable secret C9WrE

# Encrypt all clear text passwords
service password-encryption

# Configure MOTD banner
banner motd #Authorized Access Only - Room-145 LAN#

# Configure IP address on VLAN 1 for Room-145
interface vlan 1
ip address 128.107.20.10 255.255.255.0
no shutdown
exit
# (For Room-146, replace IP with: ip address 128.107.20.15 255.255.255.0)

# Save the running configuration to startup configuration
write memory
# or
copy running-config startup-config