## Practice Wordpress in VirtualBox

### Step-by-Step Guide to Share Alpine Linux `.OVA` File with Wordpress Preconfigured  

This guide explains how to set up a `.vdi` file with Alpine Linux, configure it for sharing, and provide instructions for others to use it in VirtualBox.

---

## **Step 1: Download the WordPress OVA File**
1. Open the Google Drive link:  
   👉 [Download OVA File](https://drive.google.com/file/d/1qKhRPvUqG1lpz7ed28L0fCF5rGhm7jN6/view?usp=drive_link)
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

---

## **Step 5: Access WordPress**
1. Open a browser **inside the VM**.
2. Enter `http://localhost` or the assigned IP (e.g., `http://192.168.x.x`).
3. You should see the **WordPress login page**.

---

## **Step 6: (Optional) Find the VM’s IP Address**
- Open a terminal in the VM and run:
  ```sh
  ip a
  ```
- Look for the **inet** IP address (e.g., `192.168.x.x`).
- Use this IP to access WordPress **from another device** on the same network.

---

Now you’re ready to use WordPress in VirtualBox! Let me know if you need any help. 🚀
