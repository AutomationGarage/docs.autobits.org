---
title: Control lights with AutoBits using Zigbee
sidebar_label: Control lights using Zigbee
---

How to use AutoBits Zigbee extension to control IKEA Trådfri light bulb via CC2531 USB Zigbee packet sniffer.

![Configure Zigbee extension](/img/quickstart/CC2531.jpg)
*CC2531 USB Zigbee packet sniffer*

## 1. Configure Zigbee extension

Connect CC2531 USB Zigbee packet sniffer to the computer and configure device COM port in Zigbee extension.

If your light bulb is not paired with the packet sniffer yet, set **permitJoin** to **true**.

```ini
autoStart = true

permitJoin = false
portName = COM5
```

![Configure Zigbee extension](/img/quickstart/zigbee-configure-extension.png)
*Configure packet sniffer COM port.*

## 2. Pair the device (optional)

In case this is the first time you are using your light bulb with this packet sniffer you need to pair the bulb to the sniffer. To pair the light bulb, follow the instructions that come with the light bulb. Once you have paired the device, a notification will appear.

*Note: When pairing, make sure that **permitJoin** setting is set to true. Once you paired the device, set **permitJoin** back to false for security and stability reasons.*

## 3. Configure Automator Extension

In this example, we will create an automation scenario to toggle the light bulb at a specific time:

```ini
[Turn on the light at 08:00]
at = 08:00
repeat = every day
execute = Zigbee :: Send Command
device = 14B457FFFE6CB112
cluster = On/Off
command = Toggle Command
```

![Configure Automator extension](/img/quickstart/zigbee-configure-automator.png)
*Create an automation scenario.*

At **08:00**, **Toggle** command from **On/Off** ZCL cluster will be sent to the device with address **14B457FFFE6CB112**.

*Note: Make use of config editor auto-suggest feature to simplify configuration process.*

## 4. Test

At the specified time the state of the lamp will toggle. Make sure that your light switch is on.

## Conclusion

This quick start guide highlights how Zigbee and Automator extensions can be used to control Zigbee enabled devices. There is a variety of devices that can be controlled in this manner.
