---
id: control-arduino-via-serial-port
title: Control Arduino with AutoBits via Serial Port
sidebar_label: Control Arduino via Serial Port
---

How to add buttons to AutoBits dashboard to control an LED through Serial Port.

![Test.](/quickstart/arduino-quick-start-cover.jpg)

## 1. Connect an LED to an Arduino

Connect an LED with a 220 Ω resistor in series to pins 13 and GND.

![Wiring diagram](/quickstart/arduino-quickstart.png)

Wiring diagram: [https://www.arduino.cc/en/tutorial/blink](https://www.arduino.cc/en/tutorial/blink)

## 2. Upload sketch

The sketch will control the LED when it receives a command over Serial Port.

```c
void setup() {
  pinMode(13, OUTPUT);
  Serial.begin(9600);
}

String command;

void loop() {
  while (Serial.available()) {
    char incomingChar = (char)Serial.read();

    if (incomingChar != '\n') {
      command += incomingChar;
    }
    else
    {
      executeCommand(command);
      command = "";
    }
  }  
}

void executeCommand(String command) {
  if (command == "on") {
    digitalWrite(13, HIGH);
  }
  else if (command == "off") {
    digitalWrite(13, LOW);
  }
}
```

## 3. Add buttons to dashboard

When you install AutoBits and start it for the first time, you will see a demo dashboard.

* On the dashboard: Right Click -> Add Panel -> Button.

* Open panel settings (using gear icon) and rename the button to **On**.

* Repeat the steps to add **Off** button.

* Save the dashboard by clicking **Save Changes**.

* Click both buttons, so that AutoBits can learn about them.

![Adding buttons to dashboard](/quickstart/add-buttons-to-dashboard.gif)

Adding buttons to a dashboard.

## 4. Enable Serial Port extension

Define device name, port and baud rate to use to connect to your Arduino:

* Open **Configure Extensions** page.

* Select **Serial Port** extension from the list of extensions.

* Define the COM port to which the Arduino is connected. Set **baudRate** to match the baud rate from the sketch.

```ini
autoStart = false

[Arduino]
portName = COM4
baudRate = 9600
```

* Turn on the extension.

![Configuring Serial Port extension](/quickstart/enable-serial-port-extension.gif)

Configuring Serial Port extension.

## 5. Set up a reaction to a button click

Configure **Automator** extension to send commands to the Arduino when the buttons are pressed.

* Add the following configuration to **Automator** extension:

```ini
autoStart = true

[Turn LED on]
when = Web User Interface :: On :: Clicked
execute = Serial Port :: Send Message
deviceName = Arduino
message = on

[Turn LED off]
when = Web User Interface :: Off :: Clicked
execute = Serial Port :: Send Message
deviceName = Arduino
message = off
```

![Configuring Automator extension](/quickstart/configure-automator.png)

Configuring Automator extension.

## 6. Test

Open the dashboard and press the buttons. LED should turn on and off.

## Conclusion

This guide shows how to send commands to devices using Serial Port. AutoBits can talk to any device with a serial port.

An Arduino with an LED was used as an example. Consider adapting this example for controlling a relay module or sending different commands to an Arduino.
