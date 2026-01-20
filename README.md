# Real-time-GPS-monitoring-using-Firebase-API
This Repository provides a subtle and direct way to integrate Real-time cloud monitoring of GPS navigation using Firebase cloud. Arduino IDE is used for interfacing ESP-32 to *NEO-6M GPS sensor*. To make things easy, ESP32 comes with Firebase and GPS libraries which is integrated together to achieve the desired functionality. It also includes Inter-board communication between STM32(Tx) and ESP32(Rx) using UART.

Before proceeding with interfacing the code it's always good to go through Datasheet and working of the sensor module. Refer the datasheet for NEO-6M and to understand it's working watch this video:

https://youtu.be/TK5xOWkdzMU

(credits: Blue Butterfly - https://youtube.com/@bluebutterfly2000?si=4yI33a0iRuR1IIC7)

**NOTE: Run the code under Open sky since GPS sensor requires connection to nearest satellite to fetch the coordinates**

## NEO-6M to ESP connections

ESP32 RX2 — connect to GPS TX

ESP32 TX2 — connect to GPS RX

ESP32 GND - NEO-6M GND

ESP32 5V - NEO-6M VCC

## CODE APPLICATION

*Firebase_GPS_sensor.ino* contains the interfacing code. Firebase provides a lightweight, scalable way to connect embedded systems to the cloud using simple REST APIs, making it ideal for IoT projects like GPS tracking or sensor monitoring. You can send data directly from microcontrollers (ESP32, Arduino, STM32, etc.) to Firebase services such as Firestore or Realtime Database. This canbe thus employed in IoT smart systems and for remote monitoring.

(You can also send Data from STM32 board to ESP32 using UART, since i've used that extra functionality i'll be briefing about the same)

**Our Application is to integrate ESP32, STM32, and a NEO-6M GPS module with Firebase Cloud to enable real-time monitoring and logging of GPS coordinates and STM32 sensor data.**

## TYPICAL WORKFLOW
1. ESP32 connects to Wi‑Fi using provided SSID and password.

2. Firebase host and authentication token are configured on ESP32.

3. GPS module (NEO‑6M) streams NMEA data via UART2 → parsed by TinyGPSPlus.

4. STM32 sends sensor/measurement data via UART0 → buffered in ESP32.

5. ESP32 checks GPS validity and extracts latitude/longitude if available.

6. ESP32 accumulates STM32 data until newline, then marks it as updated.

7. A JSON object is created with keys for latitude, longitude, and STM32 data.
/LSET_VOL → Latitude

/FARM_VOL → Longitude

/STM32_DATA → Sensor data string

9. Every 1000 ms, ESP32 uploads JSON to Firebase under /Sensor.

10. Firebase stores data in Realtime Database or Firestore for cloud access.

11. Mobile apps or dashboards read updates instantly from Firebase.

12. ESP32 prints debug logs and Firebase status messages on UART0 which can also be viewed on serial monitor for debugging.

## FIREBASE INTERFACE

![Firebase_GPS](https://github.com/user-attachments/assets/35053015-4b39-48c0-a463-81e519b4ee4b)
