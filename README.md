# 🪞 Setting up MagicMirror on a Raspberry Pi Zero 2 W

## 🧰 Hardware

- **Raspberry Pi Zero 2 W** (we’ll call it **RPZ2W** from now on)
- **Micro SD Card** (Capacity doesn't matter, but **use a good brand**)

## 💾 Software

- **Tool:** [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
- **OS:** Raspberry Pi OS (Legacy, 32-bit)

---

## 📲 Flashing the OS to the SD Card

1. Open **Raspberry Pi Imager**.
2. Click the **first button** and select:  
   `Raspberry Pi Zero 2 W`
3. Click the **second button** and choose:  
   `Raspberry Pi OS (Legacy, 32-bit)`
4. Click the **third button** to select your SD Card.
5. Click **"Next"**.

---

## ⚙️ Configuring the OS

### **General Tab**

- Click on **EDIT SETTINGS**.
- You can keep the default hostname: `raspberrypi`.
- Set your **Username** and **Password** — _you’ll need these to log in later_.
- Under **SSID**, enter your Wi-Fi **network name** and **password**.
- (Optional) Change your **Network Location**, **Timezone**, and **Keyboard Layout**.

### **Services Tab**

- Enable **SSH**.
- Select **Authentication via password**.

### **Options Tab**

- Not critical, but feel free to explore.
- Click **Save**, then **YES** to confirm settings.
- Read the warning and click **YES** again if you agree.

---

## 🧑‍💻 First Boot & Remote Access

1. Insert the SD card into the **RPZ2W** and power it up.
2. Open **PuTTY** on your computer.

### PuTTY Settings

- **Host Name:** `raspberrypi.local`  
- **Port:** `22`  
- **Connection type:** `SSH`  
- Click **Open**.

> ⚠️ You might get a security warning — click **Accept**.

3. When prompted:
   - Enter your **username**.
   - Enter your **password**.
4. You should see something like:
   ```
   [user]@raspberrypi:~ $
   ```
   (where `[user]` is your chosen username)

---

## 🔄 Update Your Pi

Before installing anything, update the system:

```bash
sudo apt update && sudo apt upgrade
```

Once that finishes, reboot:

```bash
sudo reboot now
```

> You’ll need to reconnect via PuTTY after rebooting.

---

## ✨ Installing MagicMirror

Use this script from `sdetweil`:

```bash
bash -c  "$(curl -sL https://raw.githubusercontent.com/sdetweil/MagicMirror_scripts/master/raspberry.sh)"
```

> 🖱️ _Right-click in PuTTY to paste._

### During the installation:

- **Disable screensaver?** → `Y` + Enter  
- **Use PM2?** → `Y` + Enter  
- **Update PM2 process name?** → `N` + Enter  

That’s it! MagicMirror should now **autostart** after each reboot.

---

## 🛠️ Useful Commands

- **Restart MagicMirror:**
  ```bash
  pm2 restart MagicMirror
  ```

- **Stop MagicMirror:**
  ```bash
  pm2 stop MagicMirror
  ```

- **View logs:**
  ```bash
  pm2 logs MagicMirror
  ```

---

## 📚 Resources

- **Official Documentation:**  
  [https://docs.magicmirror.builders](https://docs.magicmirror.builders)
