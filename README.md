# ColdChain Monitor

Real-Time Temperature & Humidity Monitoring System for Cold Storage and Pharma Warehouses

A low-cost embedded system built with an **ESP8266 NodeMCU**, a **DHT22 sensor** and a **16x2 I2C LCD**. It reads temperature and humidity again and again and shows the live values on the LCD.

Hardware project for B.E. Computer Science and Engineering (Data Science), St. John College of Engineering & Management, University of Mumbai (2026-2027).

---

## Demo

### Photos

![Hardware setup](images/hardware-setup.jpg)

![LCD showing readings](images/lcd-output.jpg)

### Video

Watch the working demo here: [Demo Video](PASTE-VIDEO-LINK-HERE)

---

## Why this project?

Cold rooms and pharma warehouses must keep temperature and humidity under control. Manual checks leave gaps between readings, and a change can go unnoticed. ColdChain Monitor checks the conditions repeatedly and shows them right on the device.

## Features

- Measures temperature (°C) and relative humidity (%RH)
- Reads sensor values at regular intervals
- Checks if the reading is valid, otherwise shows an error and retries
- Shows live readings on a 16x2 LCD
- ESP8266 supports Wi-Fi, so remote monitoring can be added later

## Hardware Used

| Component | Purpose |
|---|---|
| ESP8266 NodeMCU 1.0 (ESP-12E) | Microcontroller (reads and processes data) |
| DHT22 sensor | Measures temperature and humidity |
| 16x2 LCD with I2C module | Displays the readings |
| Breadboard + jumper wires | Connections |
| USB cable | Power and programming |

## Circuit Connections

| Module | Pin | NodeMCU Pin |
|---|---|---|
| DHT22 | VCC | 3V3 |
| DHT22 | GND | GND |
| DHT22 | DATA | D5 |
| LCD (I2C) | VCC | Vin (5V) |
| LCD (I2C) | GND | GND |
| LCD (I2C) | SDA | D2 |
| LCD (I2C) | SCL | D1 |

> Check these against your actual wiring before uploading. The I2C address used is `0x27`.

## How It Works

```
START -> Initialize ESP8266, sensor and LCD -> Read temperature and humidity
      -> Valid? -- Yes -> Format values and update LCD
                -- No  -> Show error and retry
      -> Wait for sampling interval -> Repeat
```

Input (DHT22) -> Process (ESP8266) -> Output (LCD)

## Software Setup

1. Install the **Arduino IDE**.
2. Add the ESP8266 board package (Boards Manager -> `esp8266`).
3. Install these libraries (Library Manager):
   - `DHT sensor library` (Adafruit)
   - `Adafruit Unified Sensor`
   - `LiquidCrystal I2C`
4. Select board: **NodeMCU 1.0 (ESP-12E Module)** and the correct COM port.
5. Open `tempandhum.ino` and click **Upload**.

## Repository Structure

```
ColdChain-Monitor/
├── tempandhum.ino      # Arduino code
├── images/             # Photos used in this README
├── docs/               # Synopsis / project report (PDF)
└── README.md
```

## Limitations

- This is an educational prototype, not a certified pharmaceutical monitoring system.
- Calibration against a reference instrument has not been done yet.
- Data logging, alerts and remote dashboard are not implemented yet.

## Future Scope

- Upper and lower threshold limits with buzzer or notification alerts
- Send readings over Wi-Fi to a dashboard
- Store time-stamped readings for history and charts
- Multiple sensor nodes for different locations
- Proper enclosure and calibration

## Team

- Riya Suresh Bali
- Atharv Vikas Patil
- Sakshi Chandrashekhar Shimgekar
- Aishwarya Sanjay Yadav

**Guide:** Mr. Sachin Sase, Faculty Coordinator, Dept. of CSE (Data Science), SJCEM

## License

For academic and educational use.
