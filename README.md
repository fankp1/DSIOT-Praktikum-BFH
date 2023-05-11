# DSIOT-Praktikum-BFH

## Inhaltsverzeichnis
* [General info](#general-info)
* [Installation Tailscale and starting as a service](#installation-tailscale-and-starting-as-a-service)
* [Installing the mosquitto broker and starting as a service](#installing-the-mosquitto-broker-and-starting-as-a-service)

## Ziel des heutigen Praktikums
This project is simple Lorem ipsum dolor generator.


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


