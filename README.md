# DSIOT-Praktikum-BFH

## Table of contents
* [General info](#general-info)
* [Installation Tailscale and starting as a service](#installation-tailscale-and-starting-as-a-service)
* [Installing the mosquitto broker and starting as a service](#installing-the-mosquitto-broker-and-starting-as-a-service)

## General info
This project is simple Lorem ipsum dolor generator.


## Installation Tailscale and starting as a service
```
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```

## Installing the mosquitto broker and starting as a service
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

## Installing the Node-Red and starting as a service

## Installing InfluxDB and starting as a service

## Installing Grafana and starting as a service


