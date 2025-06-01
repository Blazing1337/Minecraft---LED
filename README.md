Minecraft-Effektsteuerung mit Node-RED
Node-RED Logo

Ein Node-RED Flow zur Steuerung von Minecraft-Effekten über eine benutzerfreundliche Dashboard-Oberfläche.

📖 Übersicht
Dieses Projekt ermöglicht es, Spielern auf einem Minecraft-Server Effekte (wie Speed, Jump Boost, Invisibility) mit variabler Dauer und Stärke über Node-RED zuzuweisen. Zusätzlich visualisiert eine LED-Leiste den ausgewählten Effekt.

🔌 Funktionsweise
Spielerdaten abrufen: Der Flow holt die aktuelle Spielerliste vom Minecraft-Server.

Effekt konfigurieren:

Effekt-Typ aus Dropdown auswählen.

Dauer und Stärke per Slider anpassen.

Befehl senden: Der generierte /effect give-Befehl wird via RCON an den Server gesendet.

LED-Feedback: Eine RGB-LED-Stripe (16 LEDs) zeigt die Farbe des ausgewählten Effekts an.

🛠 Installation
Voraussetzungen
Minecraft-Server mit aktiviertem RCON (Port: 25575).

Node-RED (lokal oder auf einem Server installiert).

MQTT-Broker (z.B. Mosquitto) für die LED-Ansteuerung.

Hardware: RGB-LED-Stripe (z.B. WS2812B) mit Controller (z.B. ESP8266).

Schritte
Flow importieren:

Kopiere den Flow-JSON-Code und importiere ihn in Node-RED über Menu → Import → Clipboard.

Konfiguration anpassen:

RCON-Verbindung: Host, Port und Passwort in serverconfig-Node eintragen.

MQTT-Broker: Daten im mqtt-broker-Node hinterlegen.

Dashboard aufrufen:

Öffne die Node-RED-UI unter http://<deine-ip>:1880/ui.

🖥️ Hardware
Komponente	Beschreibung
Minecraft-Server	Beliebig (PaperMC, Spigot, etc.)
Node-RED Host	Raspberry Pi, Server, oder lokaler PC
LED-Stripe	WS2812B (16 LEDs)
Controller	ESP8266 (mit WLED oder ähnlich)
📸 Screenshots
(Füge hier Bilder des Node-RED-Flows und des Dashboards ein!)

❓ Hilfe
RCON-Probleme? Prüfe die Server-server.properties (Einstellung enable-rcon=true).

LEDs reagieren nicht? Stelle sicher, dass der MQTT-Broker erreichbar ist.
