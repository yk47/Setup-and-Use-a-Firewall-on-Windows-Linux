# 🔒🧱 Firewall Setup and Testing (Windows/Linux)

### 🎯 Objective Configure and test basic firewall rules to allow or block traffic.

## 🛠 Tools
- **UFW (Uncomplicated Firewall)** (Linux)
- **Windows Defender Firewall** (Windows 10/11)

## 🖥️ Linux (UFW) Firewall Configuration

### 1. Enable UFW
Check if UFW is active and enable it if disabled.
```bash
sudo ufw status
sudo ufw enable
```
📸 Screenshot: UFW enabled
<img width="840" height="676" alt="firewall_status_enable" src="https://github.com/user-attachments/assets/0a0197fa-2e45-462e-b266-a144f0cbc578" />


### 2. List Current Rules
```basg
sudo ufw status numbered
```
📸 Screenshot: Current rules list
<img width="840" height="676" alt="firewall_status_enable" src="https://github.com/user-attachments/assets/6f5ca6bb-9d4d-4670-a373-7119466c78cf" />


### 3. Block Telnet (Port 23)
```bash
sudo ufw deny 23/tcp
```
📸 Screenshot: UFW showing Telnet (23/tcp) denied
<img width="840" height="676" alt="block_telnet" src="https://github.com/user-attachments/assets/07f193f9-6fa9-4efe-b176-c3450c02a70b" />


### 4. Test Telnet Block
Attempt to connect to port 23:
```bash
telnet localhost 23
```
Expected result → **Connection failed.**

📸 Screenshot: Telnet connection failed
<img width="840" height="676" alt="connection_failed" src="https://github.com/user-attachments/assets/356e68a0-6ca9-4fa9-8eed-e1a0e3d6f4a3" />



### 5. Allow SSH (Port 22)
```bash
sudo ufw allow 22/tcp
```
📸 Screenshot: UFW showing SSH (22/tcp) allowed
<img width="840" height="676" alt="SSH_allowed" src="https://github.com/user-attachments/assets/d858f75f-e50d-42c2-b4f9-437d65d0db8c" />


### 6. Remove Telnet Block Rule
First, list rules with numbers:
```bash
sudo ufw status numbered
```
Then delete the Telnet rule (replace <rule_number> with actual number):
```bash
sudo ufw delete <rule_number>
```
📸 Screenshot: UFW after deleting Telnet rule
<img width="1920" height="1051" alt="delete_rule" src="https://github.com/user-attachments/assets/061176b8-7b4a-4613-8482-88e54e533f93" />

------


## 🪟 Windows (Windows Defender Firewall) Configuration
### 1. Open Windows Firewall

Press ```Win + R``` → type ```wf.msc``` → Enter

📸 Screenshot: Windows Defender Firewall with Advanced Security window


### 2. Block Telnet (Port 23)
- Go to **Inbound Rules → New Rule**
- Select **Port → TCP → Specific local port: 23**
- Select Block the connection
- Apply to Domain, Private, Public profiles
- Name rule: ```Block Telnet```
  
📸 Screenshot: Block Telnet rule visible in inbound rules list


### 3. Test Telnet Block
Open ```cmd``` and try:
```bash
telnet localhost 23
```
Expected result → **Connection failed.**

📸 Screenshot: Telnet connection failed in cmd


### 4. Allow SSH (Port 22)
- Create new inbound rule for **TCP port 22**
- Select **Allow the connection**
- Apply to **Domain, Private, Public**
- Name rule: ```Allow SSH```
  
📸 Screenshot: Allow SSH rule visible in inbound rules list


### 5. Remove Test Rule
- Right-click **Block Telnet** rule → **Delete**
  
📸 Screenshot: Inbound rules list after removal

------

## 📊 Summary of Results
- On **Linux (UFW)**:
    - Telnet (23/tcp) was blocked successfully.
    - SSH (22/tcp) was allowed.
    - Rule was removed to restore original state.

- On **Windows (Firewall)**:
    - Telnet traffic (23/tcp) was blocked.
    - SSH (22/tcp) was allowed.
    - Telnet rule was later removed.
 

## 🔎 How Firewalls Filter Traffic
- Firewalls act as gatekeepers for network traffic.
- They filter packets based on rules that define whether to allow or block traffic.
- Rules can be based on:
     - **Ports** (e.g., 22 for SSH, 23 for Telnet)
     - **Protocols** (TCP/UDP/ICMP)
     - **IP addresses**
     - **Applications**

👉 In this project:
- **Port 23** was blocked to prevent unauthorized Telnet access.
- **Port 22** was allowed to enable secure SSH connections.
- This demonstrates how firewalls **secure systems by allowing only necessary services** and blocking others.

