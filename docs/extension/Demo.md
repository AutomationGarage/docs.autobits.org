---
id: Demo
title: Demo
sidebar_label: Demo
---

can generate *channels* that have *data points* with random values.

Generated *channels* are configurable and can be used for testing and demonstration purposes.

##### Demo Extension Configuration
```ini
autoStart = true
executionInterval = 2s
```

- `autoStart` - sets if this extension should start when application starts
- `executionInterval` - sets how frequently the *data points* are generated in milliseconds(ms), seconds(s), minutes(m), hours(h), days(d). A combination of time intervals can be used (e.g 1d 2h 20m 20s 200ms).
 
##### Channel Configuration Example
```ini
[Random Current 1]
lowerValue = 3.5
upperValue = 7.5
unit = A
numberOfDecimals = 1
```

- `[Random Current 1]` is the name of the generated *data channel*
- `lowerValue` - sets the lower value
- `upperValue` - sets the upper value
- `unit` - specifies the unit
- `numberOfDecimals` - *(optional)* defines the number of decimals that the data is rounded to. If omitted then *data points* are rounded to 2 decimals by default. Number of decimals must be between 0 and 28.

##### More examples
```ini
[Random Current 2]
lowerValue = 0
upperValue = 5
unit = A
```

Make sure that small numbers are rounded to high enough number of decimals:
```ini 
[Random Voltage 1]
lowerValue = 0.000000001
upperValue = 0.000000009
unit = V
numberOfDecimals = 11
```

```ini
[Random Voltage 2]
lowerValue = 50
upperValue = 70
unit = V
```

```ini
[Random Voltage 3]
lowerValue = 60
upperValue = 80
unit = V
numberOfDecimals = 1
```

To round the *data points* to a whole number(integer) set `numberOfDecimals` to `0`:
```ini
[Random Rotational Speed]
lowerValue = 5000
upperValue = 6000
unit = min^-1
numberOfDecimals = 0
```

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