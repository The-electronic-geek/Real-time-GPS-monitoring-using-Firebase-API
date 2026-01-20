# Real-time-GPS-monitoring-using-Firebase-API
This Repository provides a subtle and direct way to integrate Real-time cloud monitoring of GPS navigation using Firebase cloud. Arduino IDE is used for interfacing ESP-32 to *NEO-6M GPS sensor*. To make things easy, ESP32 comes with Firebase and GPS libraries which is integrated together to achieve the desired functionality.

Before proceeding with interfacing the code it's always good to go through Datasheet and working of the sensor module. Refer the datasheet for NEO-6M and to understand it's working watch this video:

https://youtu.be/TK5xOWkdzMU

(credits: Blue Butterfly - https://youtube.com/@bluebutterfly2000?si=4yI33a0iRuR1IIC7)

## NEO-6M to ESP connections

ESP32 RX2 — connect to GPS TX

ESP32 TX2 — connect to GPS RX

ESP32 GND - NEO-6M GND

ESP32 5V - NEO-6M VCC

