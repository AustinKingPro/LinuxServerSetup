# Linux Server Setup - Commands & Screenshot Checklist

Use this file to run commands during the lab and to remember what to screenshot for your portfolio.

## Update & Upgrade
```bash
sudo apt update && sudo apt upgrade -y
```
**Screenshot:** Terminal showing update completed.

## Install Apache
```bash
sudo apt install apache2 -y
sudo systemctl enable apache2
sudo systemctl start apache2
sudo systemctl status apache2
```
**Screenshot:** Browser showing `http://<VM-IP>` with Apache default page (save as `02_apache_page.png`).

## Create User & Sudo
```bash
sudo adduser <username>
sudo usermod -aG sudo <username>
id <username>
```
**Screenshot:** `id <username>` output (save as `04_user_id.png`).

## SSH Login
- From host or another VM: `ssh <username>@<VM-IP>`
**Screenshot:** Terminal after successful SSH login (save as `01_ssh_login.png`).

## Firewall (UFW)
```bash
sudo ufw allow OpenSSH
sudo ufw allow 'Apache Full'
sudo ufw enable
sudo ufw status
```
**Screenshot:** `sudo ufw status` output (save as `03_ufw_status.png`).

## Optional Hardening
- Edit SSH config: `sudo nano /etc/ssh/sshd_config`
  - Set `PermitRootLogin no`
  - Consider using SSH keys only: `PasswordAuthentication no`
- Add SSH public key to `~/.ssh/authorized_keys` for your user.
**Screenshot:** Snippet of `sshd_config` changes or `ls -la ~/.ssh` showing `authorized_keys`.

## Notes
- Commit screenshots to `screenshots/` folder before pushing to GitHub.
- Record a short walkthrough video (5–10 minutes) showing the key steps and commentary; upload to Google Drive and link from the README.
