---
id: GSMCommunication
title: GSM Communication
sidebar_label: GSM Communication
---

lets you send and receive SMS messages using SIMCom SIM7000 series LTE/GPRS module.

It provides *action* `Send SMS`.

Using this *action*, you can send SMS messages to mobile phones from automation scenarios or as a reaction to an *event*.

The *action* has parameters:

- `number` - phone number of the recipient. Use international number format (e.g. +358403268838)
- `message` - text of the message

All required drivers for SIM7000 module should be installed separately.

Sim card PIN code must be disabled.

Configuration example:
```ini
portName = COM5
baudRate = 115200
```
- `portName` - COM port, at which SIMCom module expects AT commands. You can find the port name in Device Manager, under the section "Ports (COM & LPT)." The port is called "SimTech HS-USB AT Port 9001."
- `baudRate` - speed of serial communication. By default, the `baudRate` should be set to 115200. 

It is possible to receive SMS messages to AutoBits.

AutoBits will automatically extract *events* and *data points* from incoming SMS messages if they are formatted in the following way:

`[event source]::[event name]` - for an event.

`[channel name]::[value]::[unit]` - for a data point.