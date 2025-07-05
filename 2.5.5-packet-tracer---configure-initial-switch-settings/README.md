# 📘 Packet Tracer - Configure Initial Switch Settings

## 🎯 Objective

This lab guides you through configuring a Cisco Catalyst 2960 switch in Cisco Packet Tracer. Tasks include:
- Securing CLI and console access
- Encrypting passwords
- Setting message banners
- Saving the config to NVRAM
- Replicating the setup on a second switch (S2)

---

## 🔹 Part 1: Verify the Default Switch Configuration

Step 2: Show Running Configuration
bash
Copy
Edit
Switch# show running-config
Step 3: Examine System Info
bash
Copy
Edit
Switch# show startup-config
❓ Questions:
Fast Ethernet interfaces: Typically 24 (Fa0/1 to Fa0/24)

Gigabit Ethernet interfaces: Usually 2 (Gi0/1 and Gi0/2)

VTY line range: line vty 0 4

Command to show NVRAM: show startup-config

Why "startup-config is not present?" → No config has been saved yet.

🔹 Part 2: Basic Switch Configuration
Step 1: Set Hostname
bash
Copy
Edit
Switch# configure terminal
Switch(config)# hostname S1
S1(config)# exit
Step 2: Secure Console Access
bash
Copy
Edit
S1# configure terminal
S1(config)# line console 0
S1(config-line)# password letmein
S1(config-line)# login
S1(config-line)# exit
S1(config)# exit
Step 3: Test Console Login
bash
Copy
Edit
S1# exit
[Press Enter]

User Access Verification
Password: letmein
📌 Why use login? It tells the switch to require a password on the console line.

🔹 Step 4: Set Enable Password (Plaintext)
bash
Copy
Edit
S1# configure terminal
S1(config)# enable password c1$c0
S1(config)# exit
🔹 Step 5: Set Enable Secret Password (Encrypted)
bash
Copy
Edit
S1# configure terminal
S1(config)# enable secret itsasecret
S1(config)# exit
💡 enable secret is more secure (uses MD5 hashing) and overrides enable password.

🔹 Step 6: View Configuration
bash
Copy
Edit
S1# show running-config
🔍 What you'll see:

enable secret 5 $1$... → Encrypted hash

enable password c1$c0 → Still visible in plain text (until next step)

🔹 Step 7: Encrypt Plaintext Passwords
bash
Copy
Edit
S1# configure terminal
S1(config)# service password-encryption
S1(config)# exit
💡 This encrypts console and vty passwords using Type 7 encryption (not as strong as MD5).

🧠 Future passwords will also be encrypted.

🔹 Part 3: Configure MOTD Banner
Step 1: Add a Login Banner
bash
Copy
Edit
S1# configure terminal
S1(config)# banner motd "This is a secure system. Authorized Access Only!"
S1(config)# exit
🧾 When is it shown?
Before any login prompt.

⚠️ Why use it?
To legally warn unauthorized users and protect access.

🔹 Part 4: Save Configuration to NVRAM
Step 1: Save the Running Config
bash
Copy
Edit
S1# copy running-config startup-config
[Press Enter to confirm filename]
✅ Short version:

bash
Copy
Edit
S1# copy run start
Step 2: Verify the Saved Config
bash
Copy
Edit
S1# show startup-config
📌 All configuration changes will now persist after a reboot or power loss.

🔹 Part 5: Configure S2 Switch
Repeat all previous steps on S2, using the following:

🔧 S2 Configuration Commands:
bash
Copy
Edit
configure terminal
hostname S2

line console 0
password letmein
login
exit

enable password c1$c0
enable secret itsasecret

banner motd "This is a secure system. Authorized Access Only!"
service password-encryption

exit
copy running-config startup-config
✅ Summary of Key Commands
Purpose	Command
Enter privileged mode	enable
Enter global config mode	configure terminal
Set hostname	hostname S1
Set console password	line console 0
password letmein
login
Set enable password (plain)	enable password c1$c0
Set enable secret (encrypted)	enable secret itsasecret
Encrypt all plain text passwords	service password-encryption
Set MOTD banner	banner motd "message"
Save configuration	copy running-config startup-config
Show running config	show running-config
Show saved config	show startup-config