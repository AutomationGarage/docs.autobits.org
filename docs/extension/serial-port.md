---
title: Serial Port
sidebar_label: Serial Port
---

lets you communicate with external devices using Serial Port.

Making use of Serial Port is the easiest way to send data between a computer and a microcontroller.

Serial Ports are often used in industrial equipment, scientific instruments, and consumer products: GPS receivers, Bar code scanners, Uninterruptible power supplies, etc.

#### Configuration example

```ini
[Arduino]
portName = COM3
baudRate = 57600
```

In the example above, `[Arduino]` is the name of the device, that is connected to Serial Port. AutoBits uses this name when it is sending commands through Serial Port.

- `portName` - COM port, to which the external device is connected. You can find the port name in Device Manager, under the section "Ports (COM & LPT)."
- `baudRate` - speed of serial communication.
- `parity` *(optional)* - parity setting of serial connection. Possible values are `none`, `even`, `mark`, `odd` or `space`. If not specified, `none` is used by default.
- `handshake` *(optional)* - handshake setting of serial connection. Possible values are `none`, `RTS/CTS`, `XON/XOFF` or `RTS/CTS and XON/XOFF`. If not specified, `none` is used by default.
- `processOutput` *(optional)* - defines whether device output has to be parsed to extract an *event* or a *data point*.

#### Processing device output

By specifying parameter `processOutput` you can parse device output to a *data point*, *event* or both.

##### AutoBits standard format

AutoBits will automatically parse device output, without extra configuration, if it is formatted in the following manner:

`[event source]::[event name]` - to publish an *event*.

`[channel name]::[value]::[unit]` - to publish a *data point*.

##### Parsing *data point*

To parse *data point* name, configure one of the following:

- `dataPointName` - a constant to use as a name for the *data point*
- `dataPointNameJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a name for the *data point*, in case device output is JSON
- `dataPointNameRegExp` - a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the name for the *data point* from device output text

To parse data point unit configure one of the following:

- `dataPointUnit` - a constant to use as a unit for the *data point*
- `dataPointUnitJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a unit for the *data point*, in case device output is JSON
- `dataPointUnitRegExp`- a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the unit for the *data point* from device output text

To parse data point value configure one of the following:

- `dataPointValueJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a value for the *data point*, in case device output is JSON
- `dataPointValueRegExp` - a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the value for the *data point* from device output text

##### Parsing *event*

To parse event source configure one of the following:

- `eventSource` - a constant to use as a source for the *data point*
- `eventSourceJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a source for the *event*, in case device output is JSON
- `eventSourceRegExp` - a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the source for the *event* from device output text

To parse event name configure one of the following:

- `eventName` - a constant to use as a name for the *event*
- `eventNameJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a name for the *event*, in case device output is JSON
- `eventNameRegExp` - - a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the name for the *event* from device output text

The line must be terminated by `\n` - Line Feed Character (ASCII 0x0A)

This extension provides an *action* `Send Message`, that can be used to send data to an external device via Serial Port from automation scenarios or as a reaction to an *event*.

The *action* has the following parameters:

- `deviceName` - a name that you gave to the device when configuring the extension. (In the example above, the name of the device is `Arduino`.)
- `message` - text of the message

##### Notes

To physically connect an external device to a computer you can use the built-in Serial Port connector. Computers without built-in Serial Port connector can be connected via USB-to-Serial converters. Such adapters exist for all most popular Serial Protocols: RS-232, RS-485/422, 5v TTL, 3.3v TTL, etc. 

Many microcontroller development boards like Arduino have at least one Serial Port (also known as a UART or USART). Thanks to built-in USB and on-board USB-to-Serial converter, these boards can be connected directly to a computer via USB. 

#### Units

When specifying a *unit* for a *data channel*, use the unit name or it's symbol.

<details>
<summary>SI Units</summary>
<br/>

| Unit     | Symbol |
|:---------|:------:|
| Meter    | m      |
| Gram     | g      |
| Kilogram | kg     |
| Second   | s      |
| Ampere   | A      |
| Kelvin   | K      |
| Mole     | mol    |
| Candela  | cd     |

<br/>
</details>

<details>
<summary>SI Derived Units</summary>
<br/>

| Unit           | Symbol |
|:---------------|:------:|
| Hertz          | Hz     |
| Radian         | rad    |
| Steradian      | sr     |
| Newton         | N      |
| Pascal         | Pa     |
| Joule          | J      |
| Watt           | W      |
| Coulomb        | C      |
| Volt           | V      |
| Farad          | F      |
| Ohm            | Ω      |
| Siemens        | S      |
| Weber          | Wb     |
| Tesla          | T      |
| Henry          | H      |
| Degree Celsius | °C     |
| Lumen          | lm     |
| Lux            | lx     |
| Becquerel      | Bq     |
| Gray           | Gy     |
| Sievert        | Sv     |
| Katal          | kat    |

<br/>
</details>

<details>
<summary>SI Sanctioned Units</summary>
<br/>

| Unit              | Symbol |
|:------------------|:------:|
| Minute            | min    |
| Hour              | h      |
| Day               | d      |
| Degree            | °      |
| Arcminute         | ′      |
| Arcsecond         | ″      |
| Hectare           | ha     |
| Litre             | l      |
| Tonne             | t      |
| Astronomical Unit | au     |
| Neper             | Np     |
| Decibel           | dB     |
| Electronvolt      | eV     |
| Dalton            | Da     |

<br/>
</details>

<details>
<summary>SI Non-Sanctioned Units</summary>
<br/>

| Unit                  | Symbol |
|:----------------------|:------:|
| Angstrom              | Å      |
| Are                   | a      |
| Barn                  | barn   |
| Bar                   | bar    |
| Millibar              | mbar   |
| Atmosphere            | atm    |
| Barye                 | Ba     |
| Millimetre of Mercury | mmHg   |
| Torr                  | Torr   |

<br/>
</details>

<details>
<summary>English Common Units</summary>
<br/>

| Unit          | Symbol        |
|:--------------|:-------------:|
| Point         | p             |
| Pica          | P/            |
| Inch          | in            |
| Foot          | ft            |
| Yard          | yd            |
| Mile          | mi            |
| Fathom        | ftm           |
| Cable         | cable         |
| Nautical Mile | nautical mile |
| Acre          | ac            |
| Grain         | gr            |
| Dram          | dr            |
| Ounce         | oz            |
| Pound         | lb            |

<br/>
</details>

<details>
<summary>Us Customary Units</summary>
<br/>

| Unit               | Symbol             |
|:-------------------|:------------------:|
| Survey Link        | Us survey li       |
| Survey Foot        | Us survey ft       |
| Survey Rod         | Us survey rd       |
| Survey Mile        | Us survey mi       |
| Survey Chain       | Us survey ch       |
| Survey Furlong     | Us survey fur      |
| Survey League      | Us survey lea      |
| Square Survey Foot  | Us survey sq ft   |
| Square Survey Chain | Us survey sq ch   |
| Survey Acre        | Us survey ac       |
| Survey Section     | Us survey section  |
| Survey Township    | Us survey twp      |
| Us Minim           | Us ♏︎              |
| Us Fluid Dram      | Us fl dr           |
| Teaspoon           | tsp                |
| Tablespoon         | Tbsp               |
| Us Fluid Ounce     | Us fl oz           |
| Shot               | jig                |
| Us Gill            | Us gi              |
| Cup                | cp                 |
| Us Pint            | Us pt              |
| Us Quart           | Us qt              |
| Us Gallon          | Us gal             |
| Liquid Barrel      | bbl(liquid)        |
| Oil Barrel         | bbl(oil)           |
| Hogshead           | hogshead           |
| Dry Pint           | pt(dry)            |
| Dry Quart          | qt(dry)            |
| Dry Gallon         | gal(dry)           |
| Peck               | pk                 |
| Bushel             | bu                 |
| Dry Barrel         | bbl(dry)           |
| Us Hundredweight   | Us cwt             |
| Long Hundredweight | long hundredweight |
| Short Ton          | Us short ton       |
| Long Ton           | Us long ton        |
| Penny Weight       | dwt                |
| Troy Ounce         | oz t               |
| Troy Pound         | lb t               |

<br/>
</details>

<details>
<summary>Imperial Units</summary>
<br/>

| Unit                      | Symbol    |
|:--------------------------|:---------:|
| Thou                      | th        |
| Chain                     | imp ch    |
| Furlong                   | imp fur   |
| League                    | imp lea   |
| Link                      | imp li    |
| Rod                       | imp rd    |
| Perch                     | perch     |
| Rood                      | rood      |
| Imperial Fluid Ounce      | imp fl oz |
| Imperial Gill             | imp gi    |
| Imperial Pint             | imp pt    |
| Imperial Quart            | imp qt    |
| Imperial Gallon           | imp gal   |
| Imperial Minim            | imp ♏︎    |
| Fluid Scruple             | imp fl s  |
| Imperial Fluid Dram       | imp fl dr |
| Stone                     | st        |
| Quarter                   | qr        |
| Imperial Hundredweight    | imp cwt   |
| Ton                       | imp t     |
| Slug                      | slug      |

<br/>
</details>

<details>
<summary>Units, Not in a System</summary>
<br/>

| Unit              | Symbol |
|:------------------|:------:|
| Degree Fahrenheit | °F     |
| Degree Rankine    | °Ra    |
| Percent           | %      |
| One               |        |

<br/>
</details>

<details>
<summary>Units of Information</summary>
<br/>

| Unit          | Symbol |
|:--------------|:------:|
| Bit           | bit    |
| Byte          | B		 |

<br/>
</details>