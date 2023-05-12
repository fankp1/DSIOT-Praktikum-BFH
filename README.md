# DSIOT-Praktikum-BFH

## Inhaltsverzeichnis
* [Ziel des heutigen Praktikums](#Ziel-des-heutigen-Praktikums)
* [OS Image auf SD-Karte flashen](#OS-Image-auf-SD-Karte-flashen)
* [Installation Tailscale](#Installation-Tailscale)
* [Installation von dem Mosquitto Broker](#Installation-von-dem-Mosquitto-Broker)
* [Verbindung mit dem Raspberry Pi über SSH](#Verbindung-mit-dem-Raspberry-Pi-über-SSH)
* [Installation von Node-Red](#Installation-von-Node-Red)
* [Installation von InfluxDB](#Installation-von-InfluxDB)
* [Installation von Grafana](#Installation-von-Grafana)
* [Installation von MongoDB](#Installation-von-MongoDB)

## Ziel des heutigen Praktikums
In diesem Praktikum werden wir verschiedene Software-Komponenten auf einem Raspberry Pi installieren um eine Mini-Cloud aufzusetzten. Die Mini-Cloud beinhaltet einen lokalen MQTT-Broker, ein dokumentenorientiertes NoSQL-Datenbankmanagementsystem, eine Zeitreihendatenbank, ein grafisches Entwicklungswerkzeug sowie ein Visualsierungstool. Damit wir von überall auf der Welt auf unsere Mini-Cloud zugreifen können, verbinden wir das Raspberry Pi über Tailscale

## OS Image auf SD-Karte flashen
Damit das Raspberry Pi verwendet werden kann, wird ein Betriebssystem benötigt. Wir werden ein Linuz verwenden, welches extra für das Raspberry Pi entwickelt wurde.
* Rasbperry Pi Imager für gewünschtes Betriebssystem installieren (https://www.raspberrypi.com/software/)
* Gewünschtes OS auswählen (Vorschlag: Raspberry Pi OS 64bit)
* SD-Karte in den Laptop einstecken bzw. verbinden
* SD-Karte auswählen
* Über das Zahnrad kann dem Raspberry Pi bereits die WLAN Zugangsdaten mitgeteilt werden und SSH aktiviert werden
* Image auf SD-Karte schreiben

Nun kann die SD-Karte entfernt werden und mit dem Raspberry Pi verbunden werden. Sobald das Raspberry Pi mit Strom und dem Internet verbunden ist, können wir mit der Installation der Software-Pakete beginnen.

Die WLAN Zugangsdaten werden am Tag des Praktikum vor Ort verteilt.

## Verbindung mit dem Raspberry Pi über SSH
Um sich mit dem Raspberry Pi zu verbinden, gibt es verschiedene Möglichkeiten. Nachfolgend werden zwei Varianten aufgezeigt:

### Verbindung über Terminal (PowerShell oder Mac OS X Terminal):
Windows PowerShell:
* Durch das Klicken auf das Windows Logo bzw. Start Symbol, kann eine Eingabe getätigt werden.
* Eingabe von "PowerShell" um PowerShell zu öffnen

Mac OS X Terminal:
* Mittels "Command" + Leertaste die Spotlight Suche öffnen
* Terminal in das Textfeld eingeben

SSH-Verbindung herstellen:
ssh username@server

Anschliessend muss noch das Passwort von dem User eingegeben werden insofern ein Passwort gesetzt wurde.

### Verbindung über Termius:
* Terminus herunterlad und installieren
* Mac OS X: https://termius.com/free-ssh-client-for-mac-os
* Windows: https://termius.com/free-ssh-client-for-windows
* Linux: https://termius.com/free-ssh-client-for-linux

Anschliessend muss ein neuer Host hinzufügt werden. Dabei müssen die IP-Adresse, der Username, das Passwort sowie der Port (Standard: 22) angegeben werden.
## Installation Tailscale
```
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```

## Installation von dem Mosquitto Broker
```
sudo apt update
sudo apt upgrade
sudo apt install mosquitto 
sudo apt install mosquitto-clients
sudo systemctl enable mosquitto
sudo systemctl start mosquitto
```
Status von Mosquitto überprüfen:
```
sudo systemctl status mosquitto
mosquitto_sub -t test
mosquitto_pub -t test -m "Hallo Welt"
```

## Installation von Node-Red
```
bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)
sudo systemctl enable nodered.service
sudo systemctl start nodered.service
```
Status von Node-Red überprüfen:
```
sudo systemctl status nodered.service
```

## Installation von InfluxDB
```
sudo apt update && sudo apt upgrade -y
curl https://repos.influxdata.com/influxdb.key | gpg --dearmor | sudo tee /usr/share/keyrings/influxdb-archive-keyring.gpg >/dev/null
echo "deb [signed-by=/usr/share/keyrings/influxdb-archive-keyring.gpg] https://repos.influxdata.com/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/influxdb.list
sudo apt update
sudo apt install influxdb
sudo systemctl unmask influxdb
sudo systemctl enable influxdb
sudo systemctl start influxdb
```
Status von InfluxDB überprüfen:
```
sudo systemctl status influxdb
```

## Installation von Grafana
```
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
sudo apt-get update
sudo apt-get install -y grafana
sudo /bin/systemctl enable grafana-server
sudo /bin/systemctl start grafana-server
```
Status von Grafana überprüfen:
```
sudo systemctl status grafana-server
```

## Installation von MongoDB
Secure Key für die MongoDB herunterladen:
```
wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
```
Sicheren Speicherort für die Packages angeben:
```
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
```
Informationen für die Installation der MongoDB holen:
```
sudo apt-get update
```
MongoDB installieren:
```
sudo apt-get install -y mongodb-org
```

