---
title: 1-Wire
sidebar_label: 1-Wire
---

allows AutoBits to communicate with external devices using <a href="https://en.wikipedia.org/wiki/1-Wire" title="Wikipedia article about 1-Wire" target="_blank">1-Wire</a> protocol.

Many sensors, including popular DS18B20 temperature sensor use 1-Wire protocol for communication.  

To communicate with 1-wire devices, an external USB-to-1-Wire adapter **DS9490R** is needed.

At the moment supported devices are:

- DS18B20 temperature sensor *(family code 28)*
- MAX31850 thermocouple amplifier *(family code 3B)*
- DS2413 dual-channel switch *(family code 3A)*

Example configuration:

```ini
executionInterval = 1s
adapter = DS9490
port = USB1
```

- `executionInterval` - specifies an interval for polling connected sensors in milliseconds(ms), seconds(s), minutes(m), hours(h), days(d). A combination of time intervals can be used (e.g 1d 2h 20m 20s 200ms).
- `adapter` - type of used adapter (currently only DS9490 is supported).
- `port` - USB port to which the adapter is connected.

If you have switch devices such as DS2413, you can control them using *action* `Switch`.

The action has the following parameters:

- `address` - address of the switch device (e.g 3A-D8-43-01-00-00-00-D2).
- `channelA` - specifies whether Channel A should be turned `On`, turned `Off` or whether to `Toggle` the current state.
- `channelB` - specifies whether Channel B should be turned `On`, turned `Off` or whether to `Toggle` the current state.
