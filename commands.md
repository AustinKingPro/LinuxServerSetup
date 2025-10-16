# Linux Server Setup - Commands & Screenshot Checklist

Use this file to run commands during the lab and to remember what to screenshot for your portfolio.

## Update & Upgrade
```bash
sudo apt update && sudo apt upgrade -y
```

## Install Apache
```bash
sudo apt install apache2 -y
sudo systemctl enable apache2
sudo systemctl start apache2
sudo systemctl status apache2
```

## Create User & Sudo
```bash
sudo adduser <username>
sudo usermod -aG sudo <username>
id <username>
```

## SSH Login
- From host or another VM: `ssh <username>@<VM-IP>`

## Firewall (UFW)
```bash
sudo ufw allow OpenSSH
sudo ufw allow 'Apache Full'
sudo ufw enable
sudo ufw status
```

## Optional Hardening
- Edit SSH config: `sudo nano /etc/ssh/sshd_config`
  - Set `PermitRootLogin no`
  - Consider using SSH keys only: `PasswordAuthentication no`
- Add SSH public key to `~/.ssh/authorized_keys` for your user.

