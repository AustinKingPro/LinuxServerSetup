# Linux Server Setup Lab

Welcome to my **Linux Server Setup Lab**! This project demonstrates practical Linux administration skills including user management, secure SSH access, web hosting, and basic firewall configuration. It’s designed to showcase my hands-on experience for my IT portfolio.

---

## Objective
Build a Linux server with:
- User management
- Secure SSH access
- Apache web hosting
- Optional firewall setup

---

## Tools & Technologies
- **Hyper-V** (Windows host)
- **Ubuntu Server 22.04 LTS**
- **Bash scripting**
- **Apache web server**
- **SSH for remote access**
- **UFW firewall** (optional)

---

## VM Setup Steps

1. **Create VM in Hyper-V**
   - Generation 2 VM
   - 2–4 GB RAM (8 GB preferred)
   - 20–40 GB HDD
   - Network: Default Switch

2. **Install Ubuntu Server**
   - Download ISO: https://ubuntu.com/download/server
   - Set username and password
   - Install **OpenSSH server** when prompted

3. **Update System**
```bash
sudo apt update && sudo apt upgrade -y
```

4. **Create Users & Sudo Permissions**
```bash
# Add a new user
sudo adduser john

# Add user to sudo group
sudo usermod -aG sudo john

# Verify
id john
```

5. **Install Apache Web Server**
```bash
sudo apt install apache2 -y
sudo systemctl enable apache2
sudo systemctl start apache2
sudo systemctl status apache2
```

6. **Verify Web Server**
- Open VM browser or host browser and go to `http://<VM-IP>`
- Should display “Apache2 Ubuntu Default Page”

7. **Configure SSH (Optional Security Enhancements)**
```bash
sudo nano /etc/ssh/sshd_config
# Recommended changes:
# PermitRootLogin no
# PasswordAuthentication yes/no depending on key setup
sudo systemctl restart ssh
```

8. **Setup Firewall (Optional)**
```bash
sudo ufw allow OpenSSH
sudo ufw allow 'Apache Full'
sudo ufw enable
sudo ufw status
```

---

## Automation Script Example

`setup.sh` – automates basic server setup:

```bash
#!/bin/bash
# Basic Linux Server Setup Script

# Update system
sudo apt update && sudo apt upgrade -y

# Install Apache
sudo apt install apache2 -y
sudo systemctl enable apache2
sudo systemctl start apache2

# Create a new user
read -p "Enter new username: " username
sudo adduser $username
sudo usermod -aG sudo $username

# Enable firewall
sudo ufw allow OpenSSH
sudo ufw allow 'Apache Full'
sudo ufw --force enable

echo "Setup complete! User $username created, Apache running, firewall enabled."
```

Run it with:
```bash
chmod +x setup.sh
sudo ./setup.sh
```

---

## Repository Layout

```
LinuxServerSetup/
├── scripts/
│   └── setup.sh
├── screenshots/
│   ├── 01_ssh_login.png
│   ├── 02_apache_page.png
│   └── 03_ufw_status.png
└── README.md
```

---

## Outcome
- Linux server ready with **secure SSH access**
- User management configured
- Apache web server hosting a default page
- Firewall rules applied for SSH and Apache

--- 

## Lab Walkthrough & Video

I’ve documented this Linux Server Setup lab with **step-by-step screenshots** and a **full video walkthrough with commentary**. You can view all the materials in this Google Drive folder:

[**Linux Server Setup — Screenshots & Video**](https://drive.google.com/drive/folders/13ADmQdgiRtwsOmF2HAHmPwXqTaYRo_8g?usp=drive_link)

**Contents:**
- Step-by-step photos of key setup stages  
- Video walkthrough (5–10 minutes) showing Hyper-V setup, SSH login, Apache installation, and firewall configuration  
- Optional notes and commands used  

[> Replace `YOUR_DRIVE_FOLDER_ID` with the actual Google Drive folder ID.  
](https://drive.google.com/drive/folders/13ADmQdgiRtwsOmF2HAHmPwXqTaYRo_8g?usp=drive_link)
You can click the link to preview screenshots or download the video for reference.
