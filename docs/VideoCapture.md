---
id: VideoCapture
title: Video Capture
sidebar_label: Video Capture
---

lets you capture video stream from a webcam or a network video stream from an IP camera.

You can add the captured streams to a dashboard for video monitoring.

To capture video from a webcam:
```ini
[Webcam]
videoSource = Web Camera
```
- `videoSource` - specifies the source of a video stream: `Web Camera`, `Network Stream` from an IP camera or `Screen Capture`.

You can capture video from multiple sources simultaneously:

```ini
[Built-in webcam]
videoSource = Web Camera
camera = FaceTime HD Camera

[External webcam]
videoSource = Web Camera
camera = Logitech BRIO

[IP camera]
videoSource = Network Stream
url = 
```
- `camera` - *(optional)* lets you choose a specific webcam. You might want to do it if you have more than one webcam.
- `resolution` - *(optional)* lets you limit capture resolution. Doing so might be useful when many webcams are connected via a slow USB hub.

In case `videoSource` is a `Network Stream`, a parameter `url` must point to the address of a video stream.

*Tip: You can use an app for your phone to turn it into an IP camera.*

If you use one of such apps to stream video from your phone, AutoBits can capture it just as any other IP camera stream.
To capture the streams, the configuration might look like this:

```ini
[iPhone IP camera]
videoSource = Network Stream
url = http://192.168.1.232/live

[Android IP camera]
videoSource = Network Stream
url = http://192.168.1.174:8080/video
```