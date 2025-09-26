# 🔒 Firewall Setup and Testing (Windows/Linux)

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

### 2. List Current Rules
```basg
sudo ufw status numbered
```
