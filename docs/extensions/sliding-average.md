---
title: Sliding Average
sidebar_label: Sliding Average
---

computes an average of last **n** *data points* from a *channel*.

To compute sliding average for a *channel*, add configuration like this:
```ini
[My sliding average]
inputChannel = 
windowSize = 5
outputChannelName = 
```
- `[My sliding average]` - indicates beginning of configuration section
- `inputChannel` - *channel* to process
- `windowSize` - number of *data points* to include in calculation of moving average
- `outputChannelName` - this name will be used for newly generated *channel*, containing results of calculation

Configuration supports multiple sections like this.