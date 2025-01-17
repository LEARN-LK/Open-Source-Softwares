## WordPress Installation Step 

### **Step 1: Update the System**
```bash
apk update && apk upgrade
```

---

### **Step 2: Install Required Packages**
```bash
apk add nginx php82 php82-fpm php82-mysqli php82-xml php82-mbstring php82-curl php82-json php82-session php82-iconv mariadb mariadb-client wget curl tar
```

---

### **Step 3: Configure Nginx**
1. Start and enable Nginx:
   ```bash
   rc-update add nginx
   rc-service nginx start
   ```

2. Create a new Nginx configuration file for WordPress:
   ```bash
   nano /etc/nginx/conf.d/wordpress.conf
   ```
   Add the following configuration:
   ```nginx
   server {
       listen 80;
       server_name your-server-ip;

       root /var/www/wordpress;
       index index.php index.html index.htm;

       location / {
           try_files $uri $uri/ /index.php?$args;
       }

       location ~ \.php$ {
           include fastcgi_params;
           fastcgi_pass 127.0.0.1:9000;
           fastcgi_index index.php;
           fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
       }

       location ~ /\.ht {
           deny all;
       }
   }
   ```

3. Test and restart Nginx:
   ```bash
   nginx -t
   rc-service nginx restart
   ```

---

### **Step 4: Configure PHP-FPM**
1. Edit `/etc/php82/php-fpm.conf` and `/etc/php82/php-fpm.d/www.conf` to ensure:
   ```ini
   listen = 127.0.0.1:9000
   user = nginx
   group = nginx
   ```

2. Start and enable PHP-FPM:
   ```bash
   rc-update add php-fpm82
   rc-service php-fpm82 start
   ```

---

### **Step 5: Configure MariaDB**
1. Start and secure MariaDB:
   ```bash
   rc-service mariadb setup
   rc-service mariadb start
   mysql_secure_installation
   ```

2. Create a WordPress database and user:
   ```bash
   mysql -u root -p
   ```
   Run these commands:
   ```sql
   CREATE DATABASE wordpress;
   CREATE USER 'wordpressuser'@'localhost' IDENTIFIED BY 'wd123';
   GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'localhost';
   FLUSH PRIVILEGES;
   EXIT;
   ```

---

### **Step 6: Download WordPress**
1. **Preferred Method: Using `wget` or `curl`**
   ```bash
   wget https://wordpress.org/latest.tar.gz
   ```
   Or, if `wget` fails:
   ```bash
   curl -O https://wordpress.org/latest.tar.gz
   ```

2. **Alternative Method: Manual Download**
   If the above commands fail:
   - Download WordPress on another machine from [https://wordpress.org](https://wordpress.org).
   - Transfer the file to the Alpine server using `scp` or any file-sharing tool:
     ```bash
     scp latest.tar.gz user@your-server-ip:/path/to/destination
     ```

3. Extract the WordPress archive:
   ```bash
   tar -xvzf latest.tar.gz
   mv wordpress /var/www/
   ```

4. Set permissions:
   ```bash
   chown -R nginx:nginx /var/www/wordpress
   chmod -R 755 /var/www/wordpress
   ```

---

### **Step 7: Configure WordPress**
1. Create a configuration file:
   ```bash
   cp /var/www/wordpress/wp-config-sample.php /var/www/wordpress/wp-config.php
   ```

2. Edit the file:
   ```bash
   nano /var/www/wordpress/wp-config.php
   ```
   Update these lines:
   ```php
   define('DB_NAME', 'wordpress');
   define('DB_USER', 'wordpressuser');
   define('DB_PASSWORD', 'wd123');
   define('DB_HOST', 'localhost');
   ```

---

### **Step 8: Finalize Installation**
1. Restart all services:
   ```bash
   rc-service nginx restart
   rc-service php-fpm82 restart
   ```

2. Open your browser and navigate to:
   ```
   http://your-server-ip
   ```

3. Follow the WordPress setup wizard to complete the installation.

---

This method ensures WordPress is installed even if direct download issues occur. Let me know if you need help troubleshooting further!
