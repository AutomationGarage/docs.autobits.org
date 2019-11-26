---
id: publish-receive-mqtt-messages
title: Publish and receive MQTT messages using AutoBits
sidebar_label: Publish and receive MQTT messages
---

How to send, receive and parse MQTT messages using MQTT Broker and Automator extensions.

## 1. Enable MQTT extension

Optionally, configure **username** and **password** to authenticate MQTT clients:

```ini
autoStart = true

username = autobits
password = test
```

![Configure and enable MQTT Broker extension](/img/quickstart/configure-mqtt.png)
*Configure and enable MQTT Broker extension.*

## 2. Add a button to a dashboard

When you install AutoBits and start it for the first time, you will see a demo dashboard.

* On the dashboard: *Right Click -> Add Panel -> Button*.

* Open panel settings (using gear icon) and rename the button to **Send MQTT Message**.

* Save the dashboard by clicking **Save Changes**.

* Click on the button, so that AutoBits can learn about it.

![Add 'Send MQTT Message' button to the dashboard](/img/quickstart/add-buttton-send-mqtt-message.png)
*Add "Send MQTT Message" button to the dashboard.*

## 3. Configure Automator extension to publish MQTT message

Create a scenario to send a message when the button is clicked:

```ini
autoStart = true

[Send Test MQTT Message]
when = Web User Interface :: Send MQTT Message :: Clicked
execute = MQTT Broker :: Publish MQTT Message
topic = testTopic
payload = testMessage
```

![Configure Automator extension to send MQTT message](/img/quickstart/configure-automator-send-mqtt.png)
*Configure Automator extension to send MQTT message.*

## 4. Send test message

You can use any MQTT client to test if messages are sent. In this example, [MyMQTT](https://play.google.com/store/apps/details?id=at.tripwire.mqtt.client) Android application was used.

* Connect to MQTT broker using IP address, username and password (if they were specified in configuration)

* Subscribe to **testTopic**

* Click the button on the dashboard

* MQTT client should receive the message

![Connect to MQTT broker](/img/quickstart/my-mqtt-1.jpg)  |  ![Subscribe to "testTopic"](/img/quickstart/my-mqtt-2.jpg) | ![View the message](/img/quickstart/my-mqtt-3.jpg)
:------------------------------:|:-------------------------------:|:---------------------------------------------:
*Connect to MQTT broker*          | *Subscribe to "testTopic"*       | *View the message*

## 5. Receive and parse MQTT messages

AutoBits can receive MQTT messages and parse them as a **dataPoint** or **event**. To do that, messages have to be sent to topics **/dataPoint** or **/event** respectively.

MQTT messages should be formatted in the following manner:

* **[channel]::[value]::[unit]** - when publishing a data point.

* **[event source]::[event name]** - when publishing an event.

In this example [MyMQTT](https://play.google.com/store/apps/details?id=at.tripwire.mqtt.client) client is used to send messages to AutoBits:

![Connect to MQTT broker](/img/quickstart/receive-mqtt-message-1.jpg)  |  ![Subscribe to 'testTopic'](/img/quickstart/receive-mqtt-message-2.jpg)
:------------------------------:|:-------------------------------:
*Publish data point.*          | *Publish event.*

## 6. Receive test message

Add a panel to a dashboard to show data points published by MQTT client:

* On the dashboard: *Right Click -> Add Panel -> Plot*.

* Open panel settings (using gear icon). Select the data channel published by the MQTT client.

* Save the dashboard by clicking **Save Changes**.

![View data points and events sent from MQTT client.](/img/quickstart/mqtt-receive-messages-dashboard.png)
*View data points and events sent from MQTT client.*

## Conclusion

This guide shows how to send MQTT messages from and to AutoBits. It can be useful to communicate with devices that support MQTT protocol.
