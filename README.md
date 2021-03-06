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
* [Set Whitelist (aka. authorize new RFID Tag)](./docs/api/Whitelist/post.md):`POST /Whitelist` 
* [Delete from Whitelist (aka. uznauthorize RFID Tag)](./docs/api/Whitelist/delete.md):`DELETE /Whitelist` 


---
* [Set EnergyManager parameters](./docs/api/HomeManager/post.md): `POST /HomeManager`

### API Adapter for Nodered

For convenient Usage in for Instance InfluxDB I've included a Nodered flow, that transforms the clumsy stuff from the Amtron API to something useable.

* Get merged device and Status Information in a flat JSON Oject: `GET /amtron/status?wbip=<WallboxIP>&devkey=<PIN1>`

* Get Chargesessions enriched with Whitelist Name in a flat JSON Oject: `GET /amtron/transactions?wbip=<WallboxIP>&devkey=<PIN1>&pin=<PIN2>"`


### Telegraf Config

Use Telegraf and InfluxDB to conveniently pull the Data off your NodeRED API Adapter and get it into a proper Timeseries Database. I have included a telegraf configuration.

### Grafana Dashboard

Finally, import the Dashboard to Grafana to get a proper visualisation of your Chargesessions. This looks like:

![AmtronGrafana](https://github.com/lephisto/amtron/raw/master/screenshots/Amtron_Grafana_Dashboard.png)

Find the Dashboard Template in the Grafana Folder.