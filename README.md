# simple-http-mqtt-proxy
A simple HTTP->MQTT proxy written in NodeJS

# Why?
Currently for the most part there are two common ways to connect to a [MQTT](https://wikipedia.org/wiki/MQTT) server: directly using a TCP-based MQTT connection, and through a WebSockets connection (if supported by the MQTT server).
While this is likely to cover 80% of the common use cases, this proxy intends to cover two that don't necessarily fit as well within that setup.
* The client is microcontroller-based, battery powered, and is primarily publish oriented.
  * The client in this scenario needs to have as brief of a connect-transmit cycle as possible in order to return to a power-saving deep sleep mode, where the additional MQTT setup time would incur a [measurable drop in battery life over time](https://www.bakke.online/index.php/2017/05/22/reducing-wifi-power-consumption-on-esp8266-part-3/).
* The client is browser-based, has simple publish / subscription requirements, and the WebSockets option is not available due to lack of MQTT server support, firewall restriction, or missing client WebSocket support.

