# StarRupture Dedicated Server  
### Home Assistant Add-on (SteamCMD + Wine)

This Home Assistant add-on runs the **official StarRupture Dedicated Server (Windows build)** on **Home Assistant OS** using **SteamCMD and Wine**.

It is designed for **headless operation**, persistent savegames, and easy management through the Home Assistant UI.

---

## Features

- Official StarRupture Dedicated Server
- Automatic download & update via SteamCMD
- Windows server build running via Wine
- Headless operation using Xvfb
- Persistent server files and savegames
- Same proven setup style as Palworld servers
- Simple start/stop via Home Assistant

---

## Requirements

- Home Assistant OS (HAOS)
- amd64 / x86_64 system
- Internet access (SteamCMD download)
- One free TCP + UDP port (internal port is **7777**)

---

## Installation

### 1. Install the Add-on

1. Open **Home Assistant**
2. Go to **Settings → Add-ons → Add-on Store**
3. Scroll down to **Local Add-ons**
4. Select **StarRupture Dedicated Server**
5. Click **Install**

First installation may take several minutes because SteamCMD downloads the server files.

---

### 2. Configure Ports (Important)

The server **always runs internally on port 7777**.

You may change the **external (host) port** in the add-on settings.

Example:
```
7777/udp → 27077
7777/tcp → 27077
```

If you do not change it, port **7777** will be used.

---

### 3. Start the Add-on

After installation:
1. Click **Start**
2. Open the **Log** tab
3. Wait until you see messages like:

```
[SteamCMD] Update OK
[StarRupture] STARTING SERVER VIA WINE
```

When the log stops scrolling, the server is running.

---

## Uploading / Placing the Server Files on Home Assistant (Required)

This add-on stores everything in the Home Assistant **share** folder.

### Server directories

- Server files:
  ```
  /share/starrupture/server
  ```
- Savegames:
  ```
  /share/starrupture/savegame
  ```

---

### Option A (Recommended): Automatic download via SteamCMD

1. Install the add-on
2. Ensure the option:
   ```
   update_on_start: true
   ```
3. Start the add-on once and watch the logs

SteamCMD will automatically download and install the server into:
```
/share/starrupture/server
```

---

### Option B: Copy files manually from a Windows PC (SMB)

1. On your Windows PC, open File Explorer
2. Enter the following path:
   ```
   \\<HOME_ASSISTANT_IP>\share\
   ```
3. Create these folders if they do not exist:
   ```
   starrupture\server
   starrupture\savegame
   ```
4. Copy your StarRupture server files into:
   ```
   \\<HOME_ASSISTANT_IP>\share\starrupture\server\
   ```

If you already have savegames, copy them into:
```
\\<HOME_ASSISTANT_IP>\share\starrupture\savegame\YourServerName
Create a file
\\<HOME_ASSISTANT_IP>\share\starrupture\savegame\SaveData.dat
Edit the File
add /YourServerName/AutoSaveXX <- Yourlast Savefile

```

---

### Option C: Copy files using Home Assistant File Editor or SSH

**File Editor Add-on**
- Browse to:
  - `/share/starrupture/server`
  - `/share/starrupture/savegame`
- Upload files and folders there

**SSH / Terminal**
```bash
mkdir -p /share/starrupture/server /share/starrupture/savegame
# copy files into /share/starrupture/server
```

---

## First-Time Setup (Required – In-Game)

After the server starts for the first time, it **must be configured in-game**.

### Claim the Server

1. Start **StarRupture** on your PC
2. Go to **Multiplayer → Server Management**
3. Find your dedicated server in the list
4. Claim it as **Administrator**
5. Configure server settings:
   - Server name
   - Password
   - Difficulty
   - Player limit
   - Other gameplay options

This step is **mandatory**.  
If the server is not claimed, settings will not apply and players may not be able to join.

---

## Joining the Server

Players can join via:
- Server Browser
- Direct IP connection

Example:
```
<YOUR_PUBLIC_IP>:27077
```

Use the external port configured in the add-on.

---

## Updates

- The server updates automatically on every start
- This can be disabled in the add-on options:
```
update_on_start: false
```

To force an update:
1. Stop the add-on
2. Enable `update_on_start`
3. Start the add-on again

---

## Troubleshooting

### Server does not appear in Server Management
- Wait 30–60 seconds
- Refresh the list
- Check the add-on logs

### Players cannot connect
- Ensure UDP and TCP ports are forwarded
- Check firewall/router rules
- Verify the server was claimed in-game

### Log stops after startup
This is normal.  
The server runs silently until players connect.

---

## Technical Notes

- SteamCMD AppID: **3809400**
- Windows server build forced
- Runs via Wine with headless Xvfb
- Savegames persist across restarts and updates

---

## Disclaimer

This add-on is **not affiliated with or endorsed by StarRupture or its developers**.  
All trademarks belong to their respective owners.


This project is developed and maintained in my free time.
If it helps you and you like my work, I would be very happy about a small donation via PayPal to support further development.
Paypal: CyCleMat@googlemail.com
