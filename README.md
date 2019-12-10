# Inofficial AMTRON API documentation

## Introduction

This repo contains a reverse-engineered documentation for the REST Api of a Mennekes Amtron 
EV-Charger equipped with Networking.

The information provided here was validated against a Amtron Premium. However, the Status Section should work with Amtron Xtra (or other Wallboxes without Authorisation), too.

**It may not be applicable to other Amtron chargers.**

## Amtron API

### General Information

* The **DevKey required for each request** can be found in the documents you received with your Wallbox.
In the document it is called **APP-Pin**.
* Every request has to have the header param `Accept: application/json`.
* Every path shown below has a base url of `http://amtron-ip:25000/MHCP/1.0`
* Useful information can be found at the bottom of every page under **Notes**.
* Amtron Wallboxes dont like to be stressed with requests. Dont overdo it.

### Documentation

* [Get Device Information](./docs/api/DevInfo/get.md): `GET /DevInfo`
* [Set Device Information](./docs/api/DevInfo/post.md): `POST /DevInfo`
---
* [Get Charging Information](./docs/api/ChargeData/get.md): `GET /ChargeData`
* [Set Charging Information](./docs/api/ChargeData/post.md): `POST /ChargeData`
---
* [Get Statictics](./docs/api/Statistics/get.md): `GET /Statistics`
---
* [Get Transaction List](./docs/api/ChargeRecords/get.md): `GET /ChargeRecords`
---
* [Get Whitelist (aka. locally stored RFID Tags)](./docs/api/Whitelist/get.md): `GET /Whitelist`
---
* [Set EnergyManager parameters](./docs/api/HomeManager/post.md): `POST /HomeManager`

### API Adapter for Nodered

For convenient Usage in for Instance InfluxDB I've included a Nodered flow, that transforms the clumsy stuff from the Amtron API to something useable.

### Telegraf Config

Use InfluxDB + Telegraf to Pull the Data off your NodeRED API Adapter

### Grafana Dashboard

Import the Dashboard to Grafana to get a proper Visualisation of your Chargesessions. This looks like:

![AmtronGrafana](https://github.com/lephisto/amtron/raw/master/screenshots/Amtron_Grafana_Dashboard.png)