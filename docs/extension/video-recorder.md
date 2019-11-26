---
title: Video Recorder
sidebar_label: Video Recorder
---

lets you record video clips from video streams.

It provides *action* `Record Clip`.

Using this *action*, you can start recording from automation scenarios or as a reaction to an *event*.

The *action* has parameters:
- `videoStream` - video stream to record.
- `duration` - duration of the recording in milliseconds(ms), seconds(s), minutes(m), hours(h), days(d). A combination of time intervals can be used (e.g 1d 2h 20m 20s 200ms).
- `path` - *(optional)* path to a folder where the video clip is created. Default path is `%ProgramData%/Automation Garage/AutoBits`