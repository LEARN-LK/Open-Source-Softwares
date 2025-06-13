##  Move Your WordPress Site Easily with UpdraftPlus.

So you’re shifting your WordPress site — maybe from a test domain like `mymoodle.test.learn.ac.lk` to a new server or IP address like `192.248.##.###`. Whether you're changing hosts or just switching IPs, **UpdraftPlus** makes the move smooth.

---

## What You Need Before You Start

* Access to both the **old site** (source) and **new site** (destination)
* UpdraftPlus plugin installed on **both** sites

---

## First: Install UpdraftPlus Plugin

You’ll need this plugin on **both** the old site and the new one.

###  On Both Old and New WordPress Sites:

1. Log in to your WordPress Dashboard
   Example: `http://your-site/wp-admin`

2. Go to:
   **Plugins [1] → Add New  [2]**
      
<img src="https://github.com/LEARN-LK/Open-Source-Softwares/blob/main/img/plugin-install1.png" alt="image" style="max-width: 100%;width: 300px;">

4. In the search bar, type [3]:
   `UpdraftPlus`

<img src="https://github.com/LEARN-LK/Open-Source-Softwares/blob/main/img/pg-install-2.png" alt="image" style="max-width: 100%;width: 500px;">

5. Find **“UpdraftPlus WordPress Backup Plugin”** and click:
    **Install Now* [5]*

6. Once installed, click:
    **Activate[6]**
  
<img src="https://github.com/LEARN-LK/Open-Source-Softwares/blob/main/img/pg-activation3.png" alt="image" style="max-width: 100%;width: 500px;">

You’re now ready to start the backup and migration process!

---

##  Step 1: Pack Up Your Old Site (Create a Backup)

1. Go to:
   **Settings → UpdraftPlus Backups**
2. Click **Backup Now [2]**

    <img src="https://github.com/LEARN-LK/Open-Source-Softwares/blob/main/img/tk-backup1.png" alt="image" style="max-width: 100%;width: 300px;">
3. In the popup, check [3]:

   *  Include your database
   *  Include your files

<img src="https://github.com/LEARN-LK/Open-Source-Softwares/blob/main/img/tk-backup2.png" alt="image" style="max-width: 100%;width: 500px;">
     
4. Click **Backup Now** again and wait

When it’s done, you’ll see your backup listed under **Existing Backups**.

5. Click on each item to download [4]:

   * `Database`
   * `Plugins`
   * `Themes`
   * `Uploads`
   * `Others`
   
     <img src="https://github.com/LEARN-LK/Open-Source-Softwares/blob/main/img/tk-backup3.png" alt="image" style="max-width: 100%;width: 500px;">

 Save these files to your computer — they are your complete website.

---

##  Step 2: Prepare the New Site

Now let’s get your new WordPress site ready.

1. Install WordPress on your new server or IP address
   Example: `http://192.248.##.###`

2. Log in to your new site’s dashboard

3. Just like before, install the **UpdraftPlus plugin**:

   * Go to: **Plugins → Add New**
   * Search for `UpdraftPlus`
   * Click **Install Now**, then **Activate**

4. Once activated, go to:
   **Settings → UpdraftPlus Backups**

---

##  Step 3: Bring In the Backup

Now it’s time to “unpack” your old site.

1. In UpdraftPlus, scroll down to the section labeled
   **“Upload backup files”**

2. Drag and drop the five backup files you downloaded earlier (from Step 1)

3. Once uploaded, they will show up under **Existing Backups**

---

## Step 4: Restore the Site on the New Server

1. Click the **Restore** button next to the uploaded backup

    <img src="https://github.com/LEARN-LK/Open-Source-Softwares/blob/main/img/restore%20backup2.png" alt="image" style="max-width: 100%;width: 400px;">

3. Choose what to restore:

   *  Plugins
   *  Themes
   *  Uploads
   *  Others
   *  Database

4. Click **Next**, then click **Restore** again

 It's Take a short tike — UpdraftPlus will rebuild your entire site exactly as it was.

 <img src="https://github.com/LEARN-LK/Open-Source-Softwares/blob/main/img/bk-restore4.png" alt="image" style="max-width: 100%;width: 300px;">
 <img src="https://github.com/LEARN-LK/Open-Source-Softwares/blob/main/img/restore5.png" alt="image" style="max-width: 100%;width: 300px;">
 <img src="https://github.com/LEARN-LK/Open-Source-Softwares/blob/main/img/restore6.png" alt="image" style="max-width: 100%;width: 300px;">

---

##  Step 5: Update the Website Address (If It Changed)


1. Log in to the **new site admin** (after the restore):
   Example: `http://192.248.4.55/wp-admin`

2. Go to:
   **Settings → General**

3. Update these two fields:

   * **WordPress Address (URL)**
   * **Site Address (URL)**
     Change them to:

   ```
   http://192.248.##.###
   ```

4. Click **Save Changes**

You may get logged out — that’s normal. Just log back in using the new address.

---

##  Step 6: Refresh the Links (Permalinks)

This fixes any 404 “Page Not Found” issues that might show up after the move.

1. Go to:
   **Settings → Permalinks**

2. Without changing anything, scroll down and click **Save Changes**

Done! Your site’s internal links and navigation should now work properly.

---

### Tip: Automate Backups (Optional but Recommended)

Now that you’ve installed UpdraftPlus, you can:

* Set up **automatic weekly or daily backups**
* Save backups to **Google Drive, Dropbox, OneDrive**, etc.
* Be prepared in case something ever goes wrong

