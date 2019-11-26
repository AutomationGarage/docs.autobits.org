---
title: Zigbee
sidebar_label: Zigbee
---

allows you to send and receive Zigbee commands.

To communicate with Zigbee devices, a USB packet sniffer (such as CC2531) is needed.

Example configuration:

```ini
portName = COM3
permitJoin = false
```

- `portName` - COM port, to which Zigbee coordinator is connected
- `permitJoin` - allow new devices to join Zigbee network

#### Sending Commands

This extension provides an *action* `Send Command`.

Using this action you can send commands to a Zigbee device from automation scenarios.

The *action* has the following parameters:

- `address` - IEEE address of destination device
- `cluster` - cluster name or id. Cluster names and ids are defined in Zigbee Cluster Library specification
- `command` - command name or id. Command names and ids are defined in Zigbee Cluster Library specification.
  
  Every command has it's own fields. For example, `Move to Level` - a command commonly used to adjust brightness has fields `level` and `transitionTime`. AutoBits will suggest fields after you configure cluster and command

- `payload` - *(optional)* command payload as raw bytes. Represented as a HEX string. Use this property only if you want to send custom payload. For standard commands use suggested command fields instead of raw `payload`. If command fields are configured, `payload` is ignored.

Example with custom payload:

```ini
payload = 011E0900
```
