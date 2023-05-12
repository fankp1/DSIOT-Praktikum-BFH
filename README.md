# DSIOT-Praktikum-BFH

## Inhaltsverzeichnis
* [General info](#general-info)
* [Installation Tailscale and starting as a service](#installation-tailscale-and-starting-as-a-service)
* [Installing the mosquitto broker and starting as a service](#installing-the-mosquitto-broker-and-starting-as-a-service)

## Ziel des heutigen Praktikums
In diesem Praktikum werden wir verschiedene Software-Komponenten auf einem Raspberry Pi installieren um eine Mini-Cloud aufzusetzten. Die Mini-Cloud beinhaltet einen lokalen MQTT-Broker, ein dokumentenorientiertes NoSQL-Datenbankmanagementsystem, eine Zeitreihendatenbank, ein grafisches Entwicklungswerkzeug sowie ein Visualsierungstool. Damit wir von überall auf der Welt auf unsere Mini-Cloud zugreifen können, verbinden wir das Raspberry Pi über Tailscale

## OS Image auf SD-Karte flashen
* Rasbperry Pi Imager für gewünschtes Betriebssystem installieren (https://www.raspberrypi.com/software/)
* Ipsum version: 2.33
* Ament library version: 999


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

## Installation von InfluxDB

## Installation von Grafana


