

#  Practice WordPress in VirtualBox / UTM

This guide explains how to set up and access a preconfigured **WordPress VM** using VirtualBox or UTM.

---

## **Part 1: Download and Install the Virtual Machine**

### **Step 1: Download the VM**

* **VirtualBox Users (.OVA)**:

  1. Open the Google Drive link:
      [Download OVA File](https://drive.google.com/file/d/1KuV93lV0gh0kq377uJbFrM3rEg8Z2xAI/view?usp=sharing&hl=en&tab=t.0)
    <!--  [Download OVA File](https://drive.google.com/file/d/1KuV93lV0gh0kq377uJbFrM3rEg8Z2xAI/view?usp=drive_link)-->

  2. Click **Download** to save the `.OVA` file.

       

* **UTM Users (.UTM)**:

  1. Open the Google Drive link for the UTM file.
[Download UTM File](https://drive.google.com/file/d/1byVEVpOK9KJ1RsvgZxqcdPJErvls141t/view?usp=sharing&hl=en&tab=t.0)

<!-- [Download UTM File](https://drive.google.com/file/d/1byVEVpOK9KJ1RsvgZxqcdPJErvls141t/view?usp=sharing)-->

  2. Download the `.UTM` file to your Mac.

---

### **Step 2: Install the Virtualization Software**

* **VirtualBox (Windows/Linux/macOS Intel/AMD)**:

  1. Download from [VirtualBox Official Site](https://www.virtualbox.org/)
  2. Install using default options.

* **UTM (macOS Apple Silicon M1/M2/M3)**:

  1. Download from [UTM Official Site](https://mac.getutm.app/)
  2. Open the `.dmg` file and drag **UTM.app** to Applications.

---

## **Part 2: Import the VM**

* **VirtualBox**:

  1. Open VirtualBox → **File > Import Appliance**.
  2. Select the downloaded `.OVA` file → Click **Next**.
  3. Review settings (CPU, RAM, Network) → Click **Import**.

* **UTM**:

  1. Open UTM → **File > Import Virtual Machine** or click **+**.
  2. Select the downloaded `.UTM` file.
  3. The VM appears in the UTM Library.

---

## **Part 3: Start the VM**

1. Select the VM → Click **Start** (VirtualBox) or **Play ▶** (UTM).
2. Log in with the VM credentials:

   * **Username**: `learn`
   * **Password**: `wd123`

---

## **Part 4: Configure Networking**

1. **VirtualBox only:** Go to VM **Settings → Network**.
2. Set **Attached to** = **Bridged Adapter**.
3. Ensure the VM is **running** before accessing WordPress.

---

## **Part 5: Find the VM IP Address**

1. Log into the VM.
2. Run:

   ```bash
   ip addr show
   ```
3. Look for the `inet` entry under your network adapter (example: `192.168.1.10`).

---

## **Part 6: Map WordPress to a Hostname**

We will map the IP to `mywordpress.test.learn.ac.lk` so you can access WordPress from the host browser.

### **macOS / Linux**

1. Open a terminal.
2. Edit hosts file(Linux):

   ```bash
   sudo nano /etc/hosts
   ```
   Edit hosts file(MacOS):

   ```bash
   sudo nano /private/etc/hosts
   ```
3. Add:

   ```
   192.168.1.10   mywordpress.test.learn.ac.lk
   ```
4. Save in nano:

   * **Ctrl + O** → Enter → **Ctrl + X**
5. Verify:

   ```bash
   cat /etc/hosts
   ```

### **Windows**

1. Open **Notepad as Administrator**.
2. Open file:

   ```
   C:\Windows\System32\drivers\etc\hosts
   ```
3. Add:

   ```
   192.168.1.10   mywordpress.test.learn.ac.lk
   ```
4. Save (Ctrl + S)
5. Flush DNS:

   ```cmd
   ipconfig /flushdns
   ```

---

## **Part 7: Access WordPress**

1. Open a browser on the host machine.
2. Navigate to:

   ```
   http://mywordpress.test.learn.ac.lk
   ```
3. WordPress should load successfully.

---

## **Part 8: WordPress Login (Dashboard)**

* Go to:

  ```
  http://mywordpress.test.learn.ac.lk/wp-admin
  ```
* Login credentials:

  * **Username**: `learn`
  * **Password**: `wd123` *(example — replace with actual if different)*

---

## **Important Notes**

* Make sure **Bridged Adapter** is selected (VirtualBox).
* VM must be **running** before accessing WordPress.
* Default VM credentials:

  * **Username**: `learn`
  * **Password**: `wd123`
* Hostname mapping is necessary for friendly access.

---

