## Practice Wordpress in VirtualBox

### Step-by-Step Guide to Share Alpine Linux `.OVA` File with Wordpress Preconfigured  

This guide explains how to set up a `.vdi` file with Alpine Linux, configure it for sharing, and provide instructions for others to use it in VirtualBox.

---

## **Step 1: Download the WordPress OVA File**
1. Open the Google Drive link:  
   👉 [Download OVA File](https://drive.google.com/file/d/1GT0TDdZ92WXl0PcEfHm8OSaw7VyQKskJ/view?usp=drive_link)
2. Click **Download** to save the `.OVA` file to your computer.

---

## **Step 2: Download and Install VirtualBox**
1. **Download VirtualBox** from the official site:  
   👉 [https://www.virtualbox.org/](https://www.virtualbox.org/)
2. Install VirtualBox by following the on-screen instructions.

---

## **Step 3: Import the OVA File into VirtualBox**
1. Open **VirtualBox**.
2. Click **File** → **Import Appliance**.
3. Click **Choose File** and **select** the downloaded `.OVA` file.
4. Click **Next**.
5. Review settings (**CPU, RAM, Network**) and adjust if needed.
6. Click **Import** and wait for the process to complete.

---

## **Step 4: Start the WordPress VM**
1. In VirtualBox, select the **imported VM**.
2. Click **Start** to boot the VM.
   Log in using:
   - **Username**: `learn`
   - **Password**: `wd123`

---

## **Step 5: Access WordPress**

#### **5. Find the VM IP Address**:
1. Inside the VM, type:
   ```bash
   ip addr
   ```
2. Note the IP address (e.g., `192.168.1.10`).



#### **6. Map Wordpress to a Hostname on Host Machine**:
- On the host machine, edit the `hosts` file to map the VM's IP to a hostname.

---

### **Edit Hosts File**

#### **Windows**:
1. Path:  
   `C:\Windows\System32\drivers\etc\hosts`
2. Open Notepad as an administrator and add your VM IP: eg:
   ```
   192.168.1.10 mywordpress.test.learn.ac.lk
   ```

#### **MacOS**:
1. Path:  
   `/private/etc/hosts`
2. Open a terminal and edit the file:
   ```bash
   sudo nano /private/etc/hosts
   ```
3. Add:
   ```
   192.168.1.10 mywordpress.test.learn.ac.lk
   ```

#### **Linux**:
1. Path:  
   `/etc/hosts`
2. Edit the file with:
   ```bash
   sudo nano /etc/hosts
   ```
3. Add:
   ```
   192.168.1.10 mywordpress.test.learn.ac.lk
   ```

---
### **7. Access Wordpress site from the Host Machine**:
1. Open a browser on the host machine.
2. Navigate to:
   ```
   http://mywordpress.test.learn.ac.lk
   ```

---


### Notes for Users:
- Ensure VirtualBox's network settings are set to **Bridged Adapter**.
- Ensure the VM is running before accessing Wordpress site.
- Default credentials for the VM:
  - **Username**: `learn`
  - **Password**: `wd123`

This guide ensures users can easily import the `.ova` file, configure the VM, and start practicing Wordpress without additional setup.

---

### **Part 2: Troubleshooting**

Site Not Loading Properly:

Verify nginx and php-fpm services are running:
 ``` bash
rc-service nginx restart
rc-service php-fpm82 restart
```
Error Messages:

Check logs:
``` bash

tail -f /var/log/nginx/error.log
```

Renew DHCP Lease on Alpine Linux
``` bash
/etc/init.d/networking restart
```
then follow [Step 5](https://github.com/LEARN-LK/lms/blob/master/Practice-Moodle-VirtualBox.md#5-find-the-vm-ip-address)










