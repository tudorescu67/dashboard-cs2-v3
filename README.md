# CS2 RCON Dashboard 🎮

Dashboard modern și interactiv pentru gestionarea serverului Counter-Strike 2 prin RCON.

## 🌟 Features

- ✅ **VIP Management** - Acordă și elimină privilegii VIP
- ✅ **Admin Management** - Gestionează administratorii serverului
- ✅ **Player Control** - Kick, Ban, Slay, Mute jucători
- ✅ **Server Control** - Schimbă hărți, restart, pause
- ✅ **Custom RCON** - Execută orice comandă RCON
- ✅ **Real-time Console** - Monitorizare live a răspunsurilor
- ✅ **Modern UI** - Design futuristic și responsive

## 📦 Instalare

### Metoda 1: Direct pe server

1. Clonează repository-ul:
```bash
git clone https://github.com/yourusername/cs2-rcon-dashboard.git
cd cs2-rcon-dashboard
```

2. Deschide `cs2-dashboard.html` în browser

### Metoda 2: Hosting Web

1. Încarcă fișierul `cs2-dashboard.html` pe orice server web
2. Accesează URL-ul în browser

## ⚙️ Configurare Server CS2

Adaugă în `server.cfg`:

```
// RCON Settings
rcon_password "your_secure_password_here"
sv_rcon_whitelist_address "0.0.0.0/0"  // Pentru acces de oriunde (NESIGUR în producție!)
sv_rcon_maxignores 5
sv_rcon_maxfailures 10
sv_rcon_minfailures 5
sv_rcon_minfailuretime 30

// Asigură-te că portul este deschis
hostport 27015
```

**IMPORTANT:** Schimbă `rcon_password` cu o parolă puternică!

## 🔒 Securitate

⚠️ **ATENȚIE:** Dashboard-ul este pentru uz local/privat. NU expune direct pe internet fără:

1. **HTTPS** - Folosește SSL/TLS
2. **Autentificare** - Adaugă login
3. **Whitelist IP** - Restricționează accesul
4. **Firewall** - Configurează reguli stricte

## 🚀 VPS Gratuite Recomandate pentru CS2

### ⭐ Cele mai bune opțiuni:

1. **Oracle Cloud Free Tier** ⭐⭐⭐⭐⭐
   - 4 ARM cores + 24GB RAM (GRATUIT PERMANENT!)
   - 200GB storage
   - 10TB bandwidth/lună
   - **BEST CHOICE pentru CS2!**
   - Link: https://www.oracle.com/cloud/free/

2. **Google Cloud Platform** ⭐⭐⭐⭐
   - $300 credit pentru 90 zile
   - e2-micro gratuit (0.5GB RAM) - PREA SLAB pentru CS2
   - Bun pentru testing
   - Link: https://cloud.google.com/free

3. **AWS Free Tier** ⭐⭐⭐
   - t2.micro (1GB RAM) - PREA SLAB pentru CS2
   - 750 ore/lună pentru 12 luni
   - Bun pentru dashboard, nu pentru server
   - Link: https://aws.amazon.com/free/

4. **Azure** ⭐⭐⭐
   - $200 credit pentru 30 zile
   - B1S instance
   - Link: https://azure.microsoft.com/free/

### 📊 Cerințe Minime CS2 Server:

- **CPU:** 2+ cores (4+ recomandat)
- **RAM:** 4GB minim (8GB+ recomandat pentru 32 players)
- **Storage:** 30GB+ SSD
- **Network:** 100Mbps+
- **OS:** Ubuntu 20.04/22.04 LTS

### 🎯 Recomandarea mea: **Oracle Cloud Free Tier**

De ce Oracle Cloud?
- ✅ Permanent gratuit (nu expiră după X luni)
- ✅ 4 ARM cores + 24GB RAM - perfect pentru CS2!
- ✅ 200GB storage
- ✅ Performance excelent
- ✅ Uptime de 99.9%

## 📝 Instalare CS2 pe Ubuntu (Oracle Cloud)

```bash
# 1. Update sistem
sudo apt update && sudo apt upgrade -y

# 2. Instalează dependențe
sudo apt install -y lib32gcc-s1 lib32stdc++6 wget tar

# 3. Creează user pentru CS2
sudo useradd -m -s /bin/bash cs2server
sudo su - cs2server

# 4. Instalează SteamCMD
mkdir ~/steamcmd && cd ~/steamcmd
wget https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz
tar -xvzf steamcmd_linux.tar.gz

# 5. Instalează CS2 Server
./steamcmd.sh +login anonymous +force_install_dir ~/cs2-server +app_update 730 validate +quit

# 6. Configurează server
cd ~/cs2-server/game/csgo/cfg
nano server.cfg
# Adaugă configurația RCON de mai sus

# 7. Pornește serverul
cd ~/cs2-server
./game/bin/linuxsteamrt64/cs2 -dedicated +map de_dust2 +maxplayers 32 -port 27015
```

## 🔧 Comenzi RCON Utile

```bash
# VIP (necesită plugin SourceMod)
sm_addvip <steamid> <duration>
sm_removevip <steamid>

# Admin (SourceMod)
sm_admin <steamid> <level>
sm_removeadmin <steamid>

# Player Management
kickid <userid>
banid <minutes> <userid>
slay <player>
mute <player>

# Server Control
changelevel <map>
mp_restartgame 1
mp_pause_match
mp_unpause_match

# Info
status
users
listmaps
```

## 🔌 Plugin-uri Recomandate (SourceMod)

1. **SourceMod** - Framework pentru admin
2. **MetaMod** - Base pentru plugin-uri
3. **VIP Core** - Sistem VIP
4. **Admin System** - Management admin
5. **RankMe** - Ranking jucători

### Instalare SourceMod:

```bash
cd ~/cs2-server/game/csgo
wget https://sm.alliedmods.net/smdrop/1.11/sourcemod-1.11.0-git6968-linux.tar.gz
tar -xzf sourcemod-1.11.0-git6968-linux.tar.gz

# Configurează admins
nano addons/sourcemod/configs/admins_simple.ini
# Adaugă: "STEAM_0:0:12345678" "99:z"
```

## 📱 Utilizare Dashboard

1. **Conectare:**
   - Introdu IP-ul serverului
   - Port RCON (default: 27015)
   - Parola RCON
   - Click "CONNECT TO SERVER"

2. **VIP Management:**
   - Introdu Steam ID (format: STEAM_0:0:12345678)
   - Selectează durata (în zile)
   - Click "GRANT VIP"

3. **Admin Management:**
   - Introdu Steam ID
   - Selectează nivelul (1-99)
   - Click "GRANT ADMIN"

4. **Player Actions:**
   - Introdu numele sau ID-ul jucătorului
   - Alege acțiunea (Kick/Ban/Slay/Mute)

5. **Custom Commands:**
   - Orice comandă RCON validă
   - Ex: "status", "users", "sv_cheats 0"

## 🐛 Troubleshooting

**Dashboard nu se conectează:**
- Verifică dacă serverul CS2 rulează
- Verifică parola RCON în `server.cfg`
- Asigură-te că portul 27015 este deschis în firewall

**Plugin-urile nu funcționează:**
- Verifică dacă SourceMod este instalat corect
- Rulează `meta list` în consola serverului
- Verifică logurile: `~/cs2-server/game/csgo/addons/sourcemod/logs/`

**Server crash/lag:**
- Verifică RAM-ul disponibil: `free -h`
- Monitorizează CPU: `htop`
- Reduce numărul de sloturi în `server.cfg`

## 📄 Licență

MIT License - folosește liber pentru servere private sau publice.

## 💬 Support

Pentru probleme sau întrebări:
- GitHub Issues
- Discord: [Server Link]
- Email: support@yourserver.com

## 🎯 Roadmap

- [ ] WebSocket pentru real-time communication
- [ ] Player statistics
- [ ] Ban management system
- [ ] Map voting system
- [ ] Auto-restart on crash
- [ ] Multi-server support
- [ ] Dark/Light theme toggle

---

**Creat cu ❤️ pentru comunitatea CS2 din România**

**⚡ Enjoy și mult succes cu serverul tău!**
