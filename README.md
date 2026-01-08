# StarRupture Dedicated Server  
### Home Assistant Add-on (SteamCMD + Wine)

This Home Assistant add-on runs the **official StarRupture Dedicated Server (Windows build)** on **Home Assistant OS** using **SteamCMD and Wine**.

It is designed for **headless operation**, persistent savegames, and easy management through the Home Assistant UI.

---

## Features

- ✅ Official StarRupture Dedicated Server
- ✅ Automatic download & update via SteamCMD
- ✅ Windows server build running via Wine
- ✅ Headless operation using Xvfb
- ✅ Persistent server files and savegames
- ✅ Simple start/stop via Home Assistant

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

> ⏳ First installation may take several minutes because SteamCMD downloads the server files.

---

### 2. Configure Ports (Important)

The server **always runs internally on port `7777`**.

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

## File Locations

All files are stored persistently in the Home Assistant **share** directory.

### Server files
```
/share/starrupture/server
```

### Savegames
```
/share/starrupture/savegame
```

### Access from Windows
```
\\<HOME_ASSISTANT_IP>\share\starrupture\
```

---

## First-Time Setup (Required – In-Game)

⚠️ **Important:**  
After the server starts for the first time, it **must be configured in-game**.

### Claim the Server
- Start StarRupture on your PC
- Go to **Multiplayer → Server Management**
- Select your server
- Claim it as **Administrator**
- Configure server settings (name, password, difficulty, etc.)

Without claiming the server, players may not be able to join.

---

## Joining the Server

Players can join via:
- Server Browser
- Direct IP connection

Example:
```
<YOUR_PUBLIC_IP>:27077
```

---

## Updates

- The server **updates automatically on every start**
- Can be disabled in the add-on options:
```
update_on_start: false
```

---

## Troubleshooting

- Ensure UDP and TCP ports are forwarded
- Verify the server was claimed in-game
- Check add-on logs for errors

---

## Disclaimer

This add-on is **not affiliated with or endorsed by StarRupture or its developers**.
