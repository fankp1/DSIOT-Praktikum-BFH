# DSIOT-Praktikum-BFH

## Inhaltsverzeichnis
* [Ziel des heutigen Praktikums](#Ziel-des-heutigen-Praktikums)
* [OS Image auf SD-Karte flashen](#OS Image auf SD-Karte flashen)
* [Installation Tailscale](#Installation-Tailscale)
* [Installation von dem Mosquitto Broker](#Installation-von-dem-Mosquitto-Broker)
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
## Installation von InfluxDB

## Installation von Grafana

## Installation von MongoDB


