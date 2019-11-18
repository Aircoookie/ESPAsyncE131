# ESPAsyncE131 - Asynchronous E.131 (sACN) library for Arduino ESP8266 and ESP32

Experimental Aircoookie fork of [ESPAsyncE131](https://github.com/forkineye/ESPAsyncE131) by forkineye.
This version is used in the newest WLED builds. It removes the RingBuffer to save memory and instead offers a callback function on incoming packets.

This library is to simplify the validation and handling of E1.31 sACN (DMX over Ethernet) traffic on Arduino ESP8266 and ESP32 based platforms.  It supports both Unicast and Multicast configurations, exposing the full E1.31 packet to the user.  If you require support for traditional Arduino devices or polling modes, please refer to the [E131](https://github.com/forkineye/E131) library from which this project was derived from.

## Requirements

Development is always done against the latest git pulls for the ESP8266 and ESP32 cores.  If you are experiencing issues with your current Arduino core, consider updating it.

### ESP8266 Platforms

- [Adruino for ESP8266](https://github.com/esp8266/Arduino) - Arduino core for ESP8266
- [ESPAsyncUDP](https://github.com/me-no-dev/ESPAsyncUDP) - Asynchronous UDP Library

### ESP32 Platforms

- [Arduino for ESP32](https://github.com/espressif/arduino-esp32) - Arduino core for ESP32

## API / Usage

### Constructor

- ```ESPAsyncE131(uint8_t buffers = 1)```: Creates a new ESPAsyncE131 instance and allocates a ring buffer with X buffer slots.  You'll want at least 1 buffer for each Universe that may reach your device.

### Member Functions and Exposed Data Structures

- ```bool begin(e131_listen_t type, uint16_t universe = 1)```: This should be called from within ```setup()``` or whenever you need to re-configure your E1.31 listener.  Valid ```type```s are ```E131_UNICAST``` and ```E131_MULTICAST```.  ```universe``` is optional and only used for Multicast configuration.  Returns true if successful.

### Resources

- Latest code: <http://github.com/forkineye/ESPAsyncE131>
- Other Stuff: <http://forkineye.com>