# 📡 pocketSRT

**Mobile SRT/SRTLA Streaming App mit eingebettetem RTMP-Server**

pocketSRT empfängt RTMP-Streams und sendet sie per SRT oder SRTLA weiter – direkt vom Android-Handy, ohne externe Hardware. Jede Kamera oder Software die RTMP unterstützt kann als Quelle genutzt werden. DJI Kameras profitieren zusätzlich von einer nativen Auto-Connect Integration.

---

## 📥 Download

👉 [Neueste Version (APK)](../../releases/latest)

> **Android 8.0+** erforderlich · DJI Auto-Connect getestet mit Osmo Action 4

---

## 🔄 Wie funktioniert pocketSRT?

```
DJI Kamera → (Bluetooth LE / RTMP) → pocketSRT → SRT(LA) → Streaming-Ziel
```

pocketSRT enthält einen eingebetteten RTMP-Server (Node.js). Die DJI Kamera streamt per RTMP an diesen Server, pocketSRT leitet den Stream dann als SRT oder SRTLA weiter.

Die interne Pipeline:

```
DJI Kamera → RTMP → Node.js Server → FFmpeg (-c:v copy) → UDP lokal → srtdroid → SRT/SRTLA → Ziel
```

---

## ⚡ Schnellstart

### 1. SRT / SRTLA Ziel eingeben

Im **OUTPUT** Bereich:
- **Protokoll** wählen: `SRT` oder `SRTLA`
- **Ziel-URL** eingeben:
  ```
  srt://dein-server.com:5000?streamid=dein-key
  srtla://dein-server.com:5000?streamid=dein-key
  ```
- Optional: **Max. Bitrate** in kbps setzen (leer = unbegrenzt)

### 2. Kamera / Quelle verbinden

pocketSRT enthält einen eingebetteten RTMP-Server. Die **RTMP URL** wird direkt in der App angezeigt (z.B. `rtmp://192.168.1.100:1935/live/stream`).

**Jede Quelle die RTMP unterstützt kann streamen:**
- 📷 Actionkameras (DJI, GoPro, etc.)
- 🎥 Camcorder mit RTMP Support
- 💻 OBS / Streaming Software
- 📱 Andere Streaming Apps

**Option A – DJI Auto-Connect (empfohlen für DJI Kameras):**
1. Menü (☰) → **DJI Settings** öffnen
2. WLAN-Daten für die Kamera eingeben
3. RTMP-URL eintragen (wird in der App angezeigt)
4. **Verbinden** tippen → Kamera startet automatisch den Stream

**Option B – Manuell per RTMP:**
- Kamera/Software auf RTMP-Streaming konfigurieren
- Die in der App angezeigte **RTMP URL** als Ziel eintragen
- Verbindung starten

### 3. Stream starten

- **STREAM STARTEN** tippen
- Der grüne Punkt bei OUTPUT zeigt eine aktive Verbindung
- Bitrate wird in Echtzeit angezeigt

---

## 🌐 SRTLA – Bonding mit mehreren Verbindungen

SRTLA ist eine Erweiterung von SRT die mehrere Netzwerkpfade gleichzeitig nutzt. Das erhöht die Stabilität und Bandbreite.

### Nur ein Handy

pocketSRT nutzt auf einem einzelnen Handy automatisch **WiFi und Mobilfunk gleichzeitig** als zwei getrennte Pfade – das allein verbessert bereits die Stabilität erheblich.

```
pocketSRT (ein Handy)
  ├─ WiFi      → SRTLA Server
  └─ Mobilfunk → SRTLA Server
```

### Mit PocketBond (mehrere Handys)

Mit der kostenlosen [pocketBond](https://github.com/romestylez/pocketBond/) App können weitere Android-Handys als zusätzliche Bonding-Nodes eingebunden werden. Jedes Hilfs-Handy stellt seine eigene Mobilfunk-Verbindung zur Verfügung.

```
pocketSRT (Haupt-Handy)
  ├─ WiFi             → SRTLA Server
  ├─ Mobilfunk        → SRTLA Server
  ├─ PocketBond Handy 2 (Telekom 5G)  → SRTLA Server
  └─ PocketBond Handy 3 (Vodafone 4G) → SRTLA Server
```

**PocketBond Setup:**
1. PocketBond auf Hilfs-Handys installieren
2. Gleiches Password wie in pocketSRT eingeben
3. Alle Handys im selben WiFi → automatische Verbindung!
4. Jedes Hilfs-Handy braucht einen aktiven Mobilfunk-Datentarif

---

## 📊 Monitoring & Logs

- **Grüner Punkt** = Verbindung aktiv
- **Roter Punkt** = nicht verbunden
- **Bitrate** wird live angezeigt
- **Menü (☰) → Log** öffnet den vollständigen Log inkl. Export-Funktion (hilfreich für Fehleranalyse)

---

## 🎯 Kompatible SRT(LA) Server

pocketSRT funktioniert mit Standard SRT(LA)-Servern, z.B.:
- [irl-srt-server](https://github.com/irlserver/irl-srt-server)
- [srt-live-server](https://github.com/OpenIRL/srt-live-server/)
- [srtla-receiver](https://github.com/OpenIRL/srtla-receiver)
- Eigener Server

---

## 🚀 Roadmap

- 🔜 Weitere DJI Kamera Modelle
- 🔜 GoPro Support
- 🔜 Statistiken Dashboard
- 🔜 QR-Code Pairing für PocketBond

---

## 🙏 Credits

Dieses Projekt basiert auf großartigen Open-Source Projekten:

| Projekt | Verwendung | Lizenz |
|---|---|---|
| [ffmpeg-kit](https://github.com/arthenica/ffmpeg-kit) | RTMP→MPEG-TS Transcoding | LGPL 2.1 |
| [srtdroid](https://github.com/ThibaultBee/srtdroid) | SRT/SRTLA Protokoll | Apache 2.0 |
| [Moblin](https://github.com/eerimoq/moblin) | DJI BLE Protokoll | MIT |
| [Node-Media-Server](https://github.com/illuspas/Node-Media-Server) | RTMP Server | MIT |
| [MediaSrvr](https://github.com/dimadesu/MediaSrvr) | RTMP Server | MIT |
| [nodejs-mobile](https://github.com/nicktindall/nodejs-mobile) | Node.js auf Android | MIT |

Vollständige Lizenzen: [THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md)

---

## ☕ Support

Wenn dir pocketSRT gefällt:

- ☕ [Ko-fi](https://ko-fi.com/romestylez)
- 🐙 [GitHub Sponsors](https://github.com/sponsors/romestylez)

---

## 📄 Lizenz

Apache License 2.0 – siehe [LICENSE](LICENSE)
