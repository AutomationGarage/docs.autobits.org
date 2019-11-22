---
id: ANSIx3.28SerialCommunication
title: ANSI x3.28 Serial Communication
sidebar_label: ANSI x3.28 Serial Communication
---

allows AutoBits to communicate with external devices using ANSI X3.28 - 2.5 - A4 protocol.

This protocol is used by some industrial motor drivers and driver accessories. It allows sending commands to the drivers and reading status information.

Usually, the communication with an external device is made via RS422/485 serial link.  

These properties describe the communication link:

```ini
portName = COM4
baudRate = 4800
parity = even
handshake = none
address = 01
```

- `portName` - COM port, to which the external device is connected. You can find the port name in Device Manager, under the section "Ports (COM & LPT)".
- `baudRate` - speed of serial communication.
- `parity` - parity setting of serial connection. Possible values are `none`, `even`, `mark`, `odd` or `space`. If not specified, `none` is used by default.
- `handshake` - handshake setting of serial connection. Possible values are `none`, `RTS/CTS`, `XON/XOFF` or `RTS/CTS and XON/XOFF`. If not specified, `none` is used by default.
- `address` - address of the device.

To write information to external device use *action* `Set Parameter`.

The action has the following parameters:

- `parameter` - id of the setting that will be changed.
- `value` - new setting value.

To read information from the device, use *action* `Get Parameter`.

The only parameter `parameter` is an id of the setting to read.

To poll parameters at a constant interval:

```ini
[Parameter 1234]
executionInterval = 1s
parameter = 1234
```

- `executionInterval` - specifies an interval for polling in milliseconds(ms), seconds(s), minutes(m), hours(h), days(d). A combination of time intervals can be used (e.g 1d 2h 20m 20s 200ms).
- `parameter` - id of the parameter to read.

Name of the generated *data channel* will be taken from section name (`Parameter 1234` in this case.)
