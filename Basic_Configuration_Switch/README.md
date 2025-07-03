# 🔌 Cisco 2960 Switch - Basic Configuration and Simulation Activity

This project contains the configuration and explanation for a **Cisco Catalyst 2960 switch**, used in a simulation where two PCs are connected to the switch and tested for communication using ICMP (ping). It includes securing the switch, assigning a management IP, and verifying connectivity in Cisco Packet Tracer.

---

## 🛠️ Switch Configuration (Cisco 2960)

PASSWORD == cisco
hostname CCNA

no ip domain-lookup

enable secret [ENCRYPTED_PASSWORD]

service password-encryption

spanning-tree mode pvst
spanning-tree extend system-id

interface Vlan1
 ip address 192.168.10.2 255.255.255.0
 no shutdown

banner motd ^C"Auth People Alllowed only"^C

line con 0
 password 7 0822455D0A16
 login

line vty 0 4
 password 7 0822455D0A16
 login

line vty 5 15
 password 7 0822455D0A16
 login
