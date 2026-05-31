# CaravanControl Releases (Binary-Only) ✨

CaravanControl ist die lokale Steuer- und Integrationsplattform fuer Caravan-/Boots-Setups auf ESP32-S3.
Dieses Repository enthaelt ausschliesslich signierte und verifizierbare Release-Artefakte.

## Projekt-Highlights

CaravanControl ist eine lokale Steuer- und Integrationsplattform fuer Caravan-/Boots-Setups auf ESP32-S3. Das System laeuft internetunabhaengig als lokale Appliance und verbindet Netzwerkdienste, Victron-Integration, Shelly-Geraete und Update-Workflows in einer gemeinsamen Laufzeit.

🧩 Der Projektfokus liegt auf Smarthome-Komponenten von Shelly. Weitere Informationen zum Hersteller: [Shelly Homepage](https://www.shelly.com).

🔋 Zusaetzlich integriert das Projekt Victron-Komponenten wie SmartShunt und Solarregler. Weitere Informationen zum Hersteller: [Victron Energy Homepage](https://www.victronenergy.com).
🔌 Fuer die VE.Direct-Anbindung ueber ESP32-OTG-Host wird ein isolierter 4-Port-USB-Adapter eingesetzt: [Duppa Isolated 4 Port USB](https://www.duppa.net/product/isolated-4-port-usb/).

🖥️ Empfohlene Zielhardware: [Waveshare ESP32-S3 e-Paper 1.54 Herstellerseite](https://www.waveshare.com/esp32-s3-epaper-1.54.htm?srsltid=AfmBOoqwjPkPx7ijh-JVnJDGCPiQHWezCPckLVLmy2CfNyPFLn5faSFJ).

### Was das Projekt bietet

🔧 Lokale Runtime-Services: HTTP-Server, mDNS (`caravan.local`), MQTT-Broker, RPC-Proxy
🌐 Netzwerkmodi: `client_only` oder `extender` (AP+STA mit NAT, DHCP/NTP-Unterstuetzung)
📱 Setup-/Betriebsoberflaechen: vollstaendige Setup-Web-App unter `/setup`, reduzierte Recovery-UI unter `/emergency`, Dashboard fuer Betrieb und Diagnose
📦 Device-Management: Discovery, Klassifizierung, Inventar und Firmware-/Update-Status
⬆️ OTA-Updatepfad aus diesem Release-Repository inkl. API-gestuetzter Update-Pruefung
⚡ Browserbasierter Web-Flasher (GitHub Pages) fuer direktes Firmware-Update
📊 Victron/VE.Direct Integration: UART Single-Device und USB-OTG Multiport (FT4232H, bis 4 Ports) mit Live-Telemetrie; im OTG-Pfad mit isoliertem 4-Port-USB-Adapter (Duppa)
🎛️ Lokale Automations-/Telemetriebausteine fuer Energie- und Lastszenarien (inkl. Shore-Power-Pfad)

### Unterstuetzte Shelly-Produkte

- Shelly Plus 1
- Shelly Plus 1PM
- Shelly Plus i4
- Shelly Plus RGBW PM
- Shelly Plus Plug
- Shelly Plus Plug S
- Shelly Plus 2PM
- Shelly BLU Button1

Hinweis:

- Produktiv freigegeben fuer den beschriebenen Deploy-Pfad sind Shelly Gen2-Modelle plus Shelly BLU Button1.
- Shelly RGBW2 (Gen1) ist derzeit nicht fuer Auto-Deploy freigegeben.

- Keine Quellcode-Entwicklung in diesem Repository
- Keine Pull Requests fuer Code-Aenderungen in diesem Repository
- Quellcode und Entwicklung: siehe Source Repository (unten)

## Zielhardware (offiziell)

Diese Releases sind fuer folgende Zielplattform gebaut und getestet:

- Zielboard-Referenz: [Waveshare ESP32-S3 e-Paper 1.54 Herstellerseite](https://www.waveshare.com/esp32-s3-epaper-1.54.htm?srsltid=AfmBOoqwjPkPx7ijh-JVnJDGCPiQHWezCPckLVLmy2CfNyPFLn5faSFJ)
- Hersteller: Espressif Systems
- Hersteller-Typenbezeichnung: ESP32-S3-DevKitC-1
- Verwendete Variante im Projekt: ESP32-S3-DevKitC-1-N16R8 (16 MB Flash, 8 MB PSRAM)
- Board-Profil: esp32-s3-devkitc-1-n16
- PlatformIO Environment: esp32-s3-nat-8mb

Hinweis:

- Andere ESP32-Varianten koennen abweichen oder nicht kompatibel sein.

## Enthaltene Artefakte pro Release

- firmware.bin
- firmware.elf
- bootloader.bin
- partitions.bin
- spiffs.bin oder littlefs.bin
- caravan-sd-init-[tag].zip
- .sha256 und .md5 je Artefakt

## Integritaet pruefen

Linux/macOS (SHA256):

```bash
sha256sum -c firmware.bin.sha256
sha256sum -c spiffs.bin.sha256
```

Falls ein Hash-Check fehlschlaegt:

- Datei erneut herunterladen
- Nicht auf das Geraet flashen

## OTA Nutzung

Firmware kann ueber das CaravanControl-Geraet aus diesem Repo bezogen werden.

Beispiel Check:

```bash
curl -s "http://caravan.local/api/base/ota/check?repo=VolkmSte/Shelly_CaravanControl_Releases" | python3 -m json.tool
```

## Web Flasher (Browser)

Direktlink (GitHub Pages ist aktiviert):

- [GitHub Pages Web Flasher](https://volkmste.github.io/Shelly_CaravanControl_Releases/web-flash/)

Hinweise:

- Funktioniert mit Chrome/Edge Desktop (Web Serial)
- Auswahl von Kanal (`main`/`beta`) und konkreter Version direkt auf der Seite
- Schreibt aktuell `firmware.bin` auf Offset `0x10000` (Update-Pfad)
- Beim Flashen koennen alle Daten auf dem ESP verloren gehen; vorab Konfigurationen und relevante Daten sichern.

## Installationsanleitung

### Variante A: Browser Web Flasher (empfohlen fuer Updates)

Voraussetzungen:

- ESP32-S3 Zielgeraet per USB verbunden
- Chrome oder Edge auf Desktop
- Zugriff auf die Web-Flasher-Seite

Schritte:

1. Web-Flasher oeffnen.
2. Kanal waehlen: `main` (stable) oder `beta` (pre-release).
3. Gewuenschte Version auswaehlen.
4. Auf Install klicken und den seriellen Port bestaetigen.
5. Nach erfolgreichem Flash das Geraet neu starten.

Hinweis:

- Diese Methode schreibt `firmware.bin` auf `0x10000` und ist als Update-Pfad gedacht.
- Beim Flashen koennen alle Daten auf dem ESP verloren gehen; vorab Konfigurationen und relevante Daten sichern.

### Variante B: OTA-Update aus dem Geraet

Voraussetzungen:

- Geraet laeuft bereits mit kompatibler CaravanControl-Firmware
- Netzwerkzugriff auf das Geraet

Schritte:

1. Im Geraet die OTA-Pruefung gegen dieses Release-Repo ausfuehren.
2. Verfuegbares Release bestaetigen.
3. Download und Installation starten.
4. Neustart nach Abschluss durchfuehren.

Beispiel fuer den OTA-Check:

```bash
curl -s "http://caravan.local/api/base/ota/check?repo=VolkmSte/Shelly_CaravanControl_Releases" | python3 -m json.tool
```

## Rechtliche Hinweise und Haftungsausschluss

Wichtig:

- Nutzung auf eigenes Risiko.
- Es gibt keine Garantie fuer Funktion, Kompatibilitaet oder Verfuegbarkeit.
- Fehlerhaftes Flashen kann zu Datenverlust, Nichtstarten des Geraets oder Wiederherstellungsaufwand fuehren.
- Vor dem Update sollten relevante Konfigurationen gesichert werden.
- Nicht fuer sicherheitskritische Anwendungen vorgesehen.

Support und Verantwortung:

- Es handelt sich um ein Community-/Open-Source-Projekt ohne individuelle Gewaehrleistung.
- Bitte nutze fuer Fehlerberichte und Fragen das Source-Repository (Issues).

Datenschutz-Hinweis:

- Diese Release-Artefakte werden ueber GitHub bereitgestellt.
- Beim Aufruf der Seiten gelten die Datenschutz- und Nutzungsbedingungen von GitHub.

## Kanaele

- Stable: finale Releases ohne Pre-Release-Markierung
- Beta: Pre-Releases mit Beta/RC/Alpha-Markierung

## Source und rechtliche Verweise

Quellcode, Build-Skripte, Dokumentation und Issue-Tracking:

- [Source Repository](https://github.com/VolkmSte/Shelly_CaravanControl)

Lizenz und Drittanbieter-Lizenzen:

- [LICENSE](https://github.com/VolkmSte/Shelly_CaravanControl/blob/main/LICENSE)
- [THIRD_PARTY_LICENSES.md](./THIRD_PARTY_LICENSES.md)

Wichtig:

- Dieses Release-Repo verteilt Binaerdateien (ohne Quellcode).
- Dieses Release-Repo verteilt Binaerdateien. Quellcode, Lizenzen und Drittanbieter-Lizenzen: [Source Repository](https://github.com/VolkmSte/Shelly_CaravanControl), [LICENSE](https://github.com/VolkmSte/Shelly_CaravanControl/blob/main/LICENSE), [THIRD_PARTY_LICENSES](./THIRD_PARTY_LICENSES.md).
