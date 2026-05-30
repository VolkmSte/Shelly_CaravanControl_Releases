# Third-Party Licenses

Dieses Projekt enthaelt Komponenten mit eigenen Lizenzen. Die Projektlizenz in [LICENSE](LICENSE)
gilt nur fuer den eigenen Quellcode des Projekts und hebt keine Drittanbieter-Lizenzen auf.

Hinweis fuer ein oeffentliches Repository: Oeffentlich einsehbarer Quellcode ist nicht automatisch
Open Source. Die in [LICENSE](LICENSE) definierten Rechte und Einschraenkungen bleiben gueltig,
zusaetzlich zu den Rechten und Pflichten aus Drittanbieter-Lizenzen.

## Firmware (PlatformIO)

- Arduino-ESP32 Core / framework-arduinoespressif32 (Version laut Build: 3.20017.241212+sha.dcc1105b)
  - Lizenz: LGPL-2.1
  - Upstream: [github.com/espressif/arduino-esp32](https://github.com/espressif/arduino-esp32)
- ESP-IDF / framework-espidf (Version laut Build: 4.4.7)
  - Lizenz: Apache-2.0
  - Upstream: [github.com/espressif/esp-idf](https://github.com/espressif/esp-idf)
- ESP-IDF USB Host Komponente (fuer Victron OTG Multiport)
  - Lizenz: Apache-2.0 (als Teil von ESP-IDF)
  - Upstream: [github.com/espressif/esp-idf/tree/v4.4.7/components/usb](https://github.com/espressif/esp-idf/tree/v4.4.7/components/usb)

- ESPAsyncWebServer (Version laut local libdeps: 3.6.0)
  - Lizenz: LGPL-3.0
  - Upstream: [github.com/mathieucarbou/ESPAsyncWebServer](https://github.com/mathieucarbou/ESPAsyncWebServer)
- AsyncTCP (Version laut local libdeps: 3.3.2)
  - Lizenz: LGPL-3.0
  - Upstream: [github.com/mathieucarbou/AsyncTCP](https://github.com/mathieucarbou/AsyncTCP)
- ArduinoJson (Version laut local libdeps: 7.4.3)
  - Lizenz: MIT
  - Upstream: [github.com/bblanchon/ArduinoJson](https://github.com/bblanchon/ArduinoJson)
- sMQTTBroker (Version laut local libdeps: 0.1.8)
  - Lizenz: MIT
  - Upstream: [github.com/terrorsl/sMQTTBroker](https://github.com/terrorsl/sMQTTBroker)
- QRCode Bibliothek (lokal vendorisiert unter `esp32-firmware/src/third_party/qrcode/`)
  - Lizenz: MIT
  - Upstream: [github.com/ricmoo/QRCode](https://github.com/ricmoo/QRCode)
  - Direkte Upstream-Quelldateien: [src/qrcode.c](https://github.com/ricmoo/QRCode/blob/master/src/qrcode.c), [src/qrcode.h](https://github.com/ricmoo/QRCode/blob/master/src/qrcode.h)
  - Hinweis: Die lokale Kopie wurde minimal fuer die ESP-IDF/PlatformIO-Toolchain angepasst (Entfernung von `#pragma mark`-Direktiven und Bereinigung einer `uint8_t`-Grenzpruefung in `qrcode_getModule`), funktional aber nicht erweitert.
  - Herkunftshinweis im Upstream: Bibliothek von Richard Moore, in Teilen aus Project Nayuki abgeleitet
- Waveshare ES8311/Audio-Out Referenzcode (lokal unter `esp32-firmware/src/third_party/waveshare_es8311/`)
  - Lizenz: Apache-2.0 (laut SPDX-Header in den übernommenen Dateien)
  - Upstream: [waveshareteam/ESP32-S3-ePaper-1.54G](https://github.com/waveshareteam/ESP32-S3-ePaper-1.54G)
  - Quelle im Upstream: [Example/Arduino_3.2.0/examples/07_Audio_out](https://github.com/waveshareteam/ESP32-S3-ePaper-1.54G/tree/main/Example/Arduino_3.2.0/examples/07_Audio_out)

Hinweis: Weitere Module wie `WiFi`, `HTTPClient`, `Update`, `ArduinoOTA`, `DNSServer`,
`ESPmDNS`, `Preferences` und `SPIFFS` werden ueber den Arduino-ESP32 Core bereitgestellt
und sind keine zusaetzlich separat eingebundenen Dritt-Repositories in diesem Projekt.

## Setup-App (Node/Vite)

Direkte Abhaengigkeiten (aus lokal installierten Paketen):

- vue: MIT
- vue-i18n: MIT
- @intlify/devtools-types: MIT
- @types/node: MIT
- @vitejs/plugin-vue: MIT
- vite: MIT
- vitest: MIT
- vue-tsc: MIT
- typescript: Apache-2.0

## Compliance-Hinweis

Bei Distribution von Firmware-Binaries sind die Bedingungen der verwendeten LGPL-Bibliotheken
(insbesondere ESPAsyncWebServer und AsyncTCP) einzuhalten. Dazu gehoeren insbesondere Hinweise,
Lizenztexte und die in LGPL vorgesehenen Moeglichkeiten fuer Relinking/Modified Versions.

Praktischer Mindeststandard fuer Releases:

- Drittanbieter-Lizenzhinweise im Repository halten (diese Datei).
- Volltexte der verwendeten LGPL/MIT/Apache-Lizenzen mitliefern (z. B. im Release-Asset oder Dokumentationspaket).
- In Release Notes und Produktdoku klar auf verwendete LGPL-Komponenten hinweisen.

Wenn diese Pflichten fuer das Produktmodell nicht gewuenscht sind, sollten LGPL-Bibliotheken durch
permissiv lizenzierte Alternativen ersetzt werden.

## Keine Rechtsberatung

Diese Datei ist eine technische Dokumentation und keine Rechtsberatung.
