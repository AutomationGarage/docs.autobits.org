---
title: MQTT Broker
sidebar_label: MQTT Broker
---

lets you receive and publish <a href="https://mqtt.org" title="Official MQTT website" target="_blank">MQTT</a> messages.

#### Listen to MQTT messages

Publish messages to topics `event` and `dataPoint` to get data into AutoBits. Format the messages in the following way:

`[event source]::[event name]` - when publishing an *event*.

`[channel name]::[value]::[unit]` - when publishing a *data point*.

##### Custom topics and messages

If you prefer using custom topics, extract a *data point* or an *event* from MQTT message like this:

```ini
[Kitchen Temperature]
topic = kitchen
processMessage = Parse Data Point
dataPointName = Kitchen Temperature
dataPointUnit = °C
dataPointValueJsonPath = kitchen.temperature
```

This configuration tells AutoBits to expect *data points* published with topic `kitchen`.

- `topic` - name of the topic
- `processMessage` - specifies whether received message should be parsed into *data point*
- `dataPointName` - a constant name of the generated *data point*
- `unit` - a constant unit of the generated *data point*
- `dataPointValueJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a value for the *data point*, in case message is JSON

To receive *events* on topic `kitchen/light`:

```ini
[Kitchen Light On]
topic = kitchen/light/on
processMessage = Parse Event
eventSource = Kitchen Light
eventName = On
```

- `processMessage` - specifies whether received message should be parsed into *event*
- `eventSource` - a constant source of the *event*
- `eventName` - a constant name of the *event*

#### Authentication

To authenticate MQTT clients configure username and password:

```ini
username = test
password = 1234
```

Authentication is optional.

#### Sending MQTT messages

This extension provides an *action* `Publish MQTT Message`, that can be used to send MQTT messages from automation scenarios or as a reaction to an *event*.

The *action* has the following parameters:

- `topic` - topic to which the message will be published
- `payload` - payload of the message
- `qosLevel` - quality of service level. Possible values are `0`, `1`, `2`

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