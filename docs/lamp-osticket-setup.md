# Deploying osTicket

This guide explains how to set up **osTicket v1.18.1**, a free helpdesk ticketing system, on **Ubuntu 24.04 Desktop** using **VirtualBox**. Itâ€™s written for beginners to help you get osTicket running step-by-step. Sensitive details (like passwords or IP addresses) are replaced with placeholders to keep things safe.

**Warning**: This setup is for testing or development. Do **not** use it in production without adding HTTPS (SSL), a firewall, and other security measures (see â€œWhat to Do Nextâ€ section).

## What Youâ€™ll Need

- A computer with **Oracle VirtualBox** installed (download from [virtualbox.org](https://www.virtualbox.org)).
- The **Ubuntu 24.04 Desktop ISO** file (get it from [ubuntu.com](https://ubuntu.com)).
- A basic understanding of how to use a computer terminal (weâ€™ll explain commands clearly!).
- About 1â€“2 hours to follow along.

## Using Placeholders

This guide uses placeholders for sensitive information:

- Replace `YOUR_DB_PASSWORD` with a strong password (e.g., generate one with `openssl rand -base64 12` in the terminal).
- Replace `<vm-ip>` with your VMâ€™s IP address (find it by running `ip addr show` in the terminal and looking for the IP under `inet`, usually starting with `192.168.`).
- Replace `osticket-server.localdomain` with your VMâ€™s hostname or IP if needed.

## What This Guide Does

This guide will help you:

- Create a virtual machine (VM) in VirtualBox.
- Install Ubuntu 24.04 Desktop on the VM.
- Set up a web server, database, and PHP (the â€œLAMP stackâ€).
- Install osTicket v1.18.1 and make it secure.
- Check that everything works.

## Table of Contents

1. [Set Up Your Virtual Machine](#set-up-your-virtual-machine)
2. [Install Ubuntu](#install-ubuntu)
3. [Set Up the Web Server and Database](#set-up-the-web-server-and-database)
4. [Set Up the Database](#set-up-the-database)
5. [Install osTicket Files](#install-osticket-files)
6. [Configure the Web Server](#configure-the-web-server)
7. [Run the osTicket Web Installer](#run-the-osticket-web-installer)
8. [Secure Your Setup](#secure-your-setup)
9. [Check That It Works](#check-that-it-works)
10. [Troubleshooting Common Issues](#troubleshooting-common-issues)
11. [What to Do Next](#what-to-do-next)

## Set Up Your Virtual Machine

1. Open VirtualBox and click **New** to create a virtual machine.
2. Name it (e.g., â€œosTicket-VMâ€).
3. Choose **Linux** as the type and **Ubuntu (64-bit)** as the version.
4. Set these settings:
   - **CPUs**: 2
   - **RAM**: 4 GB (or 8 GB if your computer has enough memory)
   - **Disk**: 40 GB (this gives space for tickets and logs)
   - **Network**: Choose â€œBridged Adapterâ€ so the VM can connect to your network.
   - **VT-x**: Enable in your computerâ€™s BIOS if itâ€™s not already on (check VirtualBoxâ€™s error messages if it fails).
5. Select the Ubuntu 24.04 Desktop ISO file when prompted and start the VM.

## Install Ubuntu

1. The VM will boot from the Ubuntu ISO. Follow the on-screen steps to install Ubuntu 24.04 Desktop.
2. Choose a hostname (e.g., `osticket-server`) and a domain (e.g., `localdomain`) during setup.
3. Complete the installation and log in to the Ubuntu desktop.

## Set Up the Web Server and Database

1. Open the **Terminal** (search for it in Ubuntuâ€™s menu or press `Ctrl + Alt + T`).
2. Update your system and install Apache (web server), MySQL (database), PHP, and required tools:

```bash
sudo apt update
sudo apt install -y apache2 mysql-server php libapache2-mod-php php-mysql php-imap php-intl php-gd php-xml php-cli php-mbstring unzip curl
sudo systemctl enable --now apache2 mysql
```

- **What this does**: Updates your system, installs the web server, database, and PHP, then starts them.

3. Check that Apache and MySQL are running:

```bash
systemctl status apache2
systemctl status mysql
```

- **What to look for**: You should see â€œactive (running)â€ for both. Press `Ctrl + C` to exit each status check.

4. Confirm PHP is installed (version should be 7.2 or higher):

```bash
php -v
```

## Set Up the Database

1. **Secure MySQL**:
   - Run this command to make MySQL safer:

```bash
sudo mysql_secure_installation
```

- Follow the prompts:
  - Keep the default `auth_socket` for local root access (just press Enter).
  - Remove anonymous users (say â€œYesâ€).
  - Disallow remote root login (say â€œYesâ€).
  - Drop the test database (say â€œYesâ€).
  - Reload privileges (say â€œYesâ€).

2. **Create a database and user for osTicket**:
   - Log in to MySQL:

```bash
sudo mysql
```

- Run these commands (replace `YOUR_DB_PASSWORD` with a strong password, e.g., generate one with `openssl rand -base64 12`):

```sql
CREATE DATABASE IF NOT EXISTS osticket;
CREATE USER 'osticketuser'@'localhost' IDENTIFIED BY 'YOUR_DB_PASSWORD';
GRANT ALL PRIVILEGES ON osticket.* TO 'osticketuser'@'localhost';
FLUSH PRIVILEGES;
```

- Exit MySQL:

```sql
EXIT;
```

3. Verify MySQL version and authentication plugin:

```sql
SELECT VERSION();
```

- **What to look for**: You should see MySQL 8.x and `caching_sha2_password` as the default plugin.

## Install osTicket Files

1. Download osTicket v1.18.1 from [GitHub](https://github.com/osTicket/osTicket/releases/tag/v1.18.1). Save the ZIP file to your VM (e.g., in `/tmp`).
2. If the ZIP file doesnâ€™t work (e.g., corrupt), download it again.
3. Extract the ZIP and copy the `upload/` folder contents to the web serverâ€™s directory:

```bash
sudo cp -r /tmp/upload/* /var/www/html/osticket/
```

- **Note**: If you unzipped the file and the `upload` folder is intact (not extracted), use this instead:

```bash
sudo mv /tmp/upload /var/www/html/osticket
```

4. Set the correct ownership so the web server can access the files:

```bash
sudo chown -R www-data:www-data /var/www/html/osticket
```

## Configure the Web Server

1. Create a configuration file for osTicket at `/etc/apache2/sites-available/osticket.conf`:
   - Use a text editor like `nano`:

```bash
sudo nano /etc/apache2/sites-available/osticket.conf
```

- Add this content (replace `osticket-server.localdomain` with your VMâ€™s hostname or IP):

```apache
<VirtualHost *:80>
    ServerName osticket-server.localdomain
    DocumentRoot /var/www/html/osticket
    <Directory /var/www/html/osticket>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/osticket_error.log
    CustomLog ${APACHE_LOG_DIR}/osticket_access.log combined
</VirtualHost>
```

- Save and exit (`Ctrl + O`, Enter, `Ctrl + X`).

2. Enable the site and URL rewriting:

```bash
sudo a2ensite osticket.conf
sudo a2enmod rewrite
sudo systemctl daemon-reload
sudo systemctl reload apache2
```

3. Check that the configuration is correct:

```bash
sudo apache2ctl configtest
```

- **What to look for**: It should say `Syntax OK`. If not, check for typos in `osticket.conf`.

## Run the osTicket Web Installer

1. Open a web browser on the VM (or your host computer) and go to `http://<vm-ip>/osticket/setup/` (replace `<vm-ip>` with your VMâ€™s IP address, found via `ip addr show` in the terminal).
2. You should see the osTicket setup page. If not, check that Apache is running (`systemctl status apache2`).
3. Fill in the database details:
   - **Hostname**: `localhost`
   - **Database**: `osticket`
   - **User**: `osticketuser`
   - **Password**: (the secure password you set earlier)
4. Follow the setup wizard to complete installation.
5. Note: The installer may say the APCu extension is optional. You can install it later if needed:

```bash
sudo apt install php-apcu
```

## Secure Your Setup

1. During installation, osTicket copies a sample config to `ost-config.php`.
2. Remove the setup folder to prevent unauthorized access:

```bash
sudo rm -rf /var/www/html/osticket/setup/
```

3. Lock down the config file so only the web server can read it:

```bash
sudo chmod 0444 /var/www/html/osticket/include/ost-config.php
sudo chown root:www-data /var/www/html/osticket/include/ost-config.php
```

4. Double-check file permissions:

```bash
ls -l /var/www/html/osticket/include/ost-config.php
```

- It should show `-r--r--r-- root www-data`.

## Check That It Works

1. Open `http://<vm-ip>/osticket/` in your browser. You should see the osTicket client portal.
2. Log in to the staff panel (usually at `http://<vm-ip>/osticket/scp`) with the admin credentials you set during installation.
3. Check that the database tables were created:
   - Log in to MySQL:

```bash
sudo mysql -u osticketuser -p
```

- Enter your `YOUR_DB_PASSWORD`.
- Run:

```sql
USE osticket;
SHOW TABLES;
```

- You should see a list of tables (e.g., `ost_ticket`, `ost_user`).

4. Check for insecure files in the web directory (this should return nothing):

```bash
sudo find /var/www/html/osticket -type f -perm -o=w -ls
sudo find /var/www/html/osticket -type d -perm -o=w -ls
```

## Troubleshooting Common Issues

- **Corrupt ZIP file**: If the osTicket ZIP doesnâ€™t extract, it might have downloaded incorrectly. Re-download from [GitHub](https://github.com/osTicket/osTicket/releases/tag/v1.18.1).
- **MySQL shows `->` prompt**: This means you didnâ€™t finish a command. Type `;` to complete it or `\c` to cancel.
- **ERROR 1064 in MySQL**: This happens if you press Enter too soon or use wrong syntax. Check your command and verify MySQL version:

```sql
SELECT VERSION();
```

- **ERROR 1410 (GRANT)**: This means the user doesnâ€™t exist or youâ€™re not logged in as root. Use `sudo mysql` to log in as root.

## What to Do Next

**Important**: This setup is for testing only. For production, you must add security measures like HTTPS and a firewall to protect your osTicket instance.

- Set up an email account for osTicket to send notifications (use a custom domain and a service like Gmail to avoid spam issues).
- Add HTTPS for security using Letâ€™s Encrypt:

```bash
sudo apt install certbot python3-certbot-apache
sudo certbot --apache
```

- Set up a firewall to allow web traffic:

```bash
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
```

- Install `fail2ban` to protect against brute-force attacks:

```bash
sudo apt install fail2ban
```

- Back up your web files and database regularly:

```bash
sudo tar -czf /backup/osticket_backup_$(date +%F).tar.gz /var/www/html/osticket/
mysqldump -u osticketuser -p osticket > /backup/osticket_db_$(date +%F).sql
```

- Keep your system updated:

```bash
sudo apt update && sudo apt upgrade
```

