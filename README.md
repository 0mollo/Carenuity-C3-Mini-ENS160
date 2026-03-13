# Carenuity-C3-Mini-ENS160 Air Quality Sensor

![image alt](https://github.com/0mollo/Carenuity-C3-Mini-ENS160/blob/main/ENS160%20Top%20View.png) ![image alt]()

Carenuity ENS160 air quality sensor piggyback board for ESP32-C3 Mini measuring VOC, eCO₂ and AQI via I²C


VOC • eCO₂ • AQI Sensor  
Carenuity Sensor Module Architecture (SMA)


## Overview

The **Carenuity ENS160 Sensor Module** is an air-quality monitoring piggyback board designed for the **ESP32-C3 Mini platform**.

It integrates the **ScioSense ENS160 digital gas sensor**, which provides measurements for:

- Total Volatile Organic Compounds (TVOC)
- Equivalent Carbon Dioxide (eCO₂)
- Air Quality Index (AQI)

The board is built to plug directly into the **Carenuity C3-Mini ecosystem headers**, enabling rapid integration into IoT devices and environmental monitoring systems.

Version: **V1.3**


## Sensor Features

- VOC detection
- eCO₂ estimation
- AQI calculation
- I²C communication
- Interrupt output
- Configurable I²C address
- Low power consumption

## Sensor Module Pins

| Pin | Description |
|----|-------------|
| VCC | 3.3V power |
| GND | Ground |
| SDA | I²C data |
| SCL | I²C clock |
| CS  | Interface select |
| ADD | Address select |
| INT | Interrupt |


## ESP32-C3 Mini Connection Example

| ENS160 | ESP32-C3 Mini |
|------|------|
| SDA | GPIO8 |
| SCL | GPIO10 |
| VCC | 3V3 |
| GND | GND |

## Applications

- Indoor air monitoring
- Smart buildings
- HVAC automation
- Environmental IoT nodes
- Smart home systems

Example code:

```cpp
#include <Wire.h>
#include <ScioSense_ENS160.h>

ScioSense_ENS160 ens160;

void setup()
{
    Serial.begin(115200);
    Wire.begin();

    ens160.begin();
}

void loop()
{
    ens160.measure();

    Serial.print("AQI: ");
    Serial.println(ens160.getAQI());

    Serial.print("TVOC: ");
    Serial.println(ens160.getTVOC());

    Serial.print("eCO2: ");
    Serial.println(ens160.getECO2());

    delay(2000);
}





