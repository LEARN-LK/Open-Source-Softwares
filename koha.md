# Complete Koha Installation Guide on Ubuntu 24 Server


## **1. System Preparation**
### **Update and Upgrade the System**
```bash
sudo apt update && sudo apt upgrade -y
```

### **Set Hostname and Hosts File**
Replace `koha-server` with your desired hostname:
```bash
sudo hostnamectl set-hostname koha-server
```
Edit the hosts file:
```bash
sudo nano /etc/hosts
```
Add the following line (replace `<server-ip>` with your actual IP address):
```
127.0.0.1   localhost
<server-ip> koha-server library.myDNSname.org library-intra.myDNSname.org
```
Save and exit (CTRL+X, then Y, then ENTER).

## **2. Install Dependencies**
```bash
sudo apt install -y apache2 mariadb-server mariadb-client libapache2-mpm-itk \
    libdbi-perl libdbd-mysql-perl libxml-libxml-perl libxml-sax-expat-perl \
    libxml-sax-writer-perl libxml2-utils unzip wget git
```

## **3. Add Koha Repository and Install Koha**
```bash
sudo apt install -y gnupg
wget -q -O- https://debian.koha-community.org/koha/gpg.asc | sudo tee /etc/apt/trusted.gpg.d/koha.asc
sudo sh -c 'echo "deb http://debian.koha-community.org/koha stable main" > /etc/apt/sources.list.d/koha.list'
```
Update package lists and install Koha:
```bash
sudo apt update
sudo apt install -y koha-common
```

## **4. Configure Database**
Start MariaDB and secure installation:
```bash
sudo systemctl enable --now mariadb
sudo mysql_secure_installation
```

Log into MariaDB:
```bash
sudo mariadb -u root -p
```
Run the following SQL commands:
```sql
CREATE USER 'koha'@'localhost' IDENTIFIED BY 'yourpassword';
GRANT ALL PRIVILEGES ON *.* TO 'koha'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
EXIT;
```

## **5. Create Koha Instance**
```bash
sudo koha-create --create-db library
```
Verify database tables:
```bash
sudo koha-mysql library -e "SHOW TABLES;"
```

## **6. Configure Apache for Koha**
Enable required Apache modules:
```bash
sudo a2enmod rewrite cgi headers proxy_http
sudo systemctl restart apache2
```

Edit the Koha Apache configuration file:
```bash
sudo nano /etc/apache2/sites-enabled/library.conf
```
Ensure the following settings exist:
```
<VirtualHost *:80>
    ServerName library.myDNSname.org
    Include /etc/koha/apache-shared.conf
    Include /etc/koha/apache-shared-opac.conf
</VirtualHost>

<VirtualHost *:80>
    ServerName library-intra.myDNSname.org
    Include /etc/koha/apache-shared.conf
    Include /etc/koha/apache-shared-intranet.conf
</VirtualHost>
```
Save and exit.
Restart Apache:
```bash
sudo systemctl restart apache2
```

## **7. Start Koha Services**
```bash
sudo koha-plack --start library
sudo koha-zebra --start library
sudo systemctl restart apache2
```
Verify services:
```bash
sudo systemctl status apache2
sudo koha-plack --status library
sudo koha-zebra --status library
```

## **8. Access Koha Web Interface**
- **OPAC:** http://library.myDNSname.org/
- **Staff Interface:** http://library-intra.myDNSname.org/

## **9. Create a Superuser**
Run the following command and follow prompts:
```bash
sudo koha-create --create-db library
```
Then, create an administrator user:
```bash
sudo koha-mysql library
```
Run the following SQL command (replace values accordingly):
```sql
INSERT INTO borrowers (cardnumber, userid, password, surname, categorycode, branchcode)
VALUES ('admin', 'admin', MD5('yourpassword'), 'Administrator', 'S', 'MAIN');
```
Exit MariaDB:
```sql
EXIT;
```

## **10. Set Up Background Jobs (Optional)**
Enable and start Koha cron jobs:
```bash
sudo koha-enable-sip library
sudo koha-enable-sip library
sudo systemctl restart apache2
```

### **Koha is now fully installed and ready to use!** 🚀

https://koha-community.org/manual/24.11/en/html/installation.html
https://wiki.koha-community.org/wiki/Koha_on_ubuntu_-_packages

