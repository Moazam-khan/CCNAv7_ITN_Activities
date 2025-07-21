# **Packet Tracer Lab: Connect a Wired and Wireless LAN - Summary**  

## **Objective**  
This lab focuses on connecting wired and wireless LAN devices in Packet Tracer, ensuring proper cable selection, verifying connections, and examining the physical network topology.  

## **Key Tasks**  
### **Part 1: Connect to the Cloud**  
- Connect **Router0 (F0/0)** to **Cloud (Eth6)** using a **Copper Straight-Through** cable.  
- Connect **Cloud (Coax7)** to **Cable Modem (Port0)** using the appropriate coaxial cable.  

### **Part 2: Connect Router0**  
- Connect **Router0 (Ser0/0/0)** to **Router1 (Ser0/0)** using a **Serial DCE/DTE** cable.  
- Connect **Router0 (F0/1)** to **netacad.pka (F0)** using a **Copper Cross-Over** cable (since autosensing is disabled).  
- Connect **Router0 (Console)** to **Configuration Terminal (RS232)** using a **Console (Rollover)** cable.  

### **Part 3: Connect Remaining Devices**  
- Connect **Router1 (F1/0)** to **Switch (F0/1)** using a **Copper Straight-Through** cable.  
- Connect **Cable Modem (Port1)** to **Wireless Router (Internet Port)** using an Ethernet cable.  
- Connect **Wireless Router (Eth1)** to **Family PC (F0)** using a **Copper Straight-Through** cable.  

### **Part 4: Verify Connections**  
- Test connectivity by **pinging netacad.pka** from Family PC.  
- Access **http://netacad.pka** via the web browser.  
- Ping the **Switch** from Home PC to verify connectivity.  
- Use the **Configuration Terminal** to access **Router0** and check interface statuses (`show ip interface brief`).  

### **Part 5: Examine the Physical Topology**  
- **Cloud:** Check the number of wires connected to the switch in the blue rack.  
- **Primary Network:** Identify devices on the table beside the blue rack.  
- **Secondary Network:** Observe why two orange cables are connected per device (likely for redundancy or dual connections).  
- **Home Network:** Note the absence of a rack (typical for home setups).  

## **Key Takeaways**  
- Proper **cable selection** (Straight-Through vs. Cross-Over vs. Serial vs. Console) is crucial for connectivity.  
- **Ping and web access** tests help verify successful connections.  
- **Physical vs. Logical Topology** provides different perspectives on network structure.  

This lab reinforces fundamental networking concepts, including device interconnection, troubleshooting, and topology analysis.  

---  
**End of Summary**