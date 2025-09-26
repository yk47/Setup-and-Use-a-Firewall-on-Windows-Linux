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
Expected result → Connection failed.

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
