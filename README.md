# esp-sockets

Barebones WebSocket relay for the ESP32 + p5.js class.

## What you need

**Laptop (the relay)**
- Node.js 18 or newer (https://nodejs.org)
- Run these in the project folder:

      npm install
      npm start

  `npm install` pulls in the two packages the server uses: `express` and `ws`.

**ESP32 (XIAO ESP32-C6 + MPU6050)**
- Arduino IDE 2.x
- Board package: "esp32" by Espressif Systems, version 3.0 or newer (needed for the C6).
  Select board "XIAO_ESP32C6".
- Libraries (Library Manager):
  - "WebSockets" by Markus Sattler
  - "Adafruit MPU6050" (also installs Adafruit Unified Sensor and Adafruit BusIO when prompted)
- In `esp32/esp32_mpu_socket/esp32_mpu_socket.ino`, set `WIFI_SSID`, `WIFI_PASS`, and
  `SERVER_HOST` (your laptop's LAN IP) before uploading.

**Browser**
- Nothing to install. WebSockets are built in, and p5.js is loaded by `public/index.html`.

## Running it

Open http://localhost:3000 in two tabs. Click in one, the other shows the message.

Students on the same WiFi open http://<your-lan-ip>:3000 instead.
Find the LAN IP with `ipconfig getifaddr en0`.

To use from editor.p5js.org (https), expose the relay with a tunnel:

    cloudflared tunnel --url http://localhost:3000

and connect with wss://<the-printed-url>.

Note: school or public WiFi often blocks small IoT devices. Connect the ESP32 and laptop
to a repeater router or a phone hotspot instead.
