# Monitoring
To monitor parameters in the RAS is paramount for controlling and keeping the water quality good.

## Sensor packages

### Seneye
[Seneye](https://www.seneye.com/) is a consumer-grade sensor with USB connection to a computer running proprietary software. You can use C++ / Python interface to the USB device, but the slide needs to be changed and activated every 30 days, and the driver interface is not fully .

### Custom (Arduino etc)
You can roll your own sensor using an embedded microcontroller, ethernet device and your sensor of choice.

Examples:
- Arduino Uno + Ethernet + Sensor
- ESP8266 Wifi module + Sensor

#### DS18B20 1-wire temperature sensor
A nice package, comes as TO92 and also with waterproof cable for immersion. Provides 9 to 12 bits of Celsius temperature between -55 to 125 degree Celsius with +- 0.5 degree Celsius from -10 to 85 degree Celsius.


[arduino tutorial with ds18b20](https://create.arduino.cc/projecthub/TheGadgetBoy/ds18b20-digital-temperature-sensor-and-arduino-9cc806)
[datasheet for DS18B20](https://datasheets.maximintegrated.com/en/ds/DS18B20.pdf)
[ds18b20 no resistor needed](https://wp.josh.com/2014/06/23/no-external-pull-up-needed-for-ds18b20-temp-sensor/)

## Data transmission

### MQTT (Data distribution network)
MQTT is a lightweight publish-subscribe network implementation, consisting of a broker which clients can subscribe or publish messages to. MQTT clients can be run on embedded devices with internet access, but the transport layer is TCP and application layer is HTTP, so there is a bit of overhead.

Good usecases are non-timecritical measurements to be distributed to many recipients, especially for human consumption. There are no built-in "loss of connection" in MQTT, so I would not use it for tight control loops where a loss of data can lead to disaster.

Examples:
- HiveMQ
- Mosquitto
- Eclipse Paho MQTT

![MQTT](img/mqtt.png?raw=true "MQTT")

### Node-RED (Flow programming)
Node-RED is one of several flow programming systems, giving you an easy way to both visualize and modify data as it is being transmitted.

![node-red](img/node-red.png?raw=true "node-red")

## Data storage

### Other databases



## Data visualization

### Clarify
[Clarify](https://www.clarify.us/) is a product by Searis AS, displays data in custom timelines, making it easy for people to collaborate and comment using both phone app and web interface.

Uses [JSON-RPC 2.0](https://www.jsonrpc.org/specification) and can be used from [Node-red](https://nodered.org/) or stand-alone client.

### Grafana Cloud Dashboard
[Grafana Cloud Dashboard](https://grafana.com/products/cloud/features/#cloud-dashboards-grafana) can be used to visualize timelines.