---
id: ComputerHardwareMonitor
title: Computer Hardware Monitor
sidebar_label: Computer Hardware Monitor
---

lets you monitor temperature sensors, fan speeds, voltages, load and clock rates of computer hardware.
 
It supports most motherboards, Intel and AMD CPUs, AMD and Nvidia GPUs, HDDs and SSDs with S.M.A.R.T.

It also lets you monitor and control computer sound volume.

Properties:
```ini
executionInterval = 1s
soundVolumeControlInput = 
```

`executionInterval` - sets how often data is collected from sensors in milliseconds(ms), seconds(s), minutes(m), hours(h), days(d). A combination of time intervals can be used (e.g 1d 2h 20m 20s 200ms).

`soundVolumeControlInput` - *(optional)* it can be used to control system sound volume. Set value of this property to a *channel*, with *data point* values changing between 0 and 100. Every new *data point* value will then change system volume to whatever value it is. E.g., *data point* with value 75 will set system volume to 75%

This extension can acquire more data about your hardware if you run the app as Admin. Without Administrator rights, most hardware sensors are not accessible.

Supported Hardware:
- CPU core sensors 
    - Intel Core 2, Core i3/i5/i7, Atom, Sandy Bridge, Ivy Bridge, Haswell, Broadwell, Silvermont, Skylake, Kaby Lake, Airmont
    - AMD K8 (0Fh family), K10 (10h, 11h family), Llano (12h family), Fusion (14h family), Bulldozer (15h family), Jaguar (16h family)
- Motherboard sensors 
    - ITE IT8620E, IT8628E, IT8705F, IT8712F, IT8716F, IT8718F, IT8720F, IT8721F, IT8726F, IT8728F, IT8771E, IT8772E
    - Fintek F71808E, F71858, F71862, F71868AD, F71869, F71869A, F71882, F71889ED, F71889AD, F71889F
    - Nuvoton NCT6102D, NCT6106D, NCT6771F, NCT6772F, NCT6775F, NCT6776F, NCT6779D, NCT6791D
    - Winbond W83627DHG, W83627DHG-P, W83627EHF, W83627HF, W83627THF, W83667HG, W83667HG-B, W83687THF
- GPU sensors 
    - Nvidia
    - AMD 
- Hard drives 
    - S.M.A.R.T. temperature sensors
    - SSD wear level, host reads/writes