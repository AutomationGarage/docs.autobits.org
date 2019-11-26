---
id: measure-temperature-using-ds18b20-sensor
title: Measure temperature with AutoBits using DS18B20 sensor
sidebar_label: Measure temperature using DS18B20 sensor
---

How to connect DS18B20 temperature sensor using 1-Wire bus and display the measurements on a dashboard.

## 1. Connect the sensor to a computer

Use DS9490R 1-Wire to USB adapter. Wire the sensor in the following way:

![Wiring diagram](/img/quickstart/wiring-diagram.png)
*Wiring diagram*

## 2. Enable 1-Wire extension

Define adapter, port and measurement interval:

* Open **Configure Extensions** page.
* Select **1-Wire** extension from the list of extensions.
* Set **adapter** to **DS9490** and **port** to **USB1**. Setting **executionInterval** specifies measurement interval.

```ini
autoStart = true
executionInterval = 1s

adapter = DS9490
port = USB1
```

* Turn on the extension.

![Configuring 1-Wire extension.](/img/quickstart/configure-1-wire-v3.png)
*Configuring 1-Wire extension.*

## 3. Add a plot to a dashboard

* On the dashboard: *Right Click -> Add Panel -> Plot*.
* Open panel settings (using gear icon). Select the data channel of the sensor.

![Configuring 1-Wire extension.](/img/quickstart/add-1-wire-to-dashboard.png)
*Selecting Data Channel to show on the plot.*

* Save the dashboard by clicking **Save Changes**.

## Conclusion

This guide shows how to use 1-Wire sensors. DS18B20 was used as an example.

AutoBits supports 1-Wire device families 0x28, 0x3B, 0x3A (DS18B20 temperature sensor, MAX31850 thermocouple amplifier, DS2413 dual-channel switch).
