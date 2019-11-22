---
id: PIDController
title: PID Controller
sidebar_label: PID Controller
---

is an implementation of <a href="https://en.wikipedia.org/wiki/PID_controller" title="Wikipedia article about PID controller" target="_blank">proportional–integral–derivative</a> controller.

It can be used to reach and hold ***set point*** of some ***process variable***.

For example, heat-up an oven to ***set point =*** *50°C* and hold it at that temperature. *Temperature* is the ***process variable*** in this case.

To do it, the controller calculates correction, that should be applied to a system and assigns correction value to ***control variable***. 

In the case of oven temperature control, heater power should be adjusted proportionally to ***control variable*** value.

Example configuration that implements above-mentioned scenario:

```ini
[Keep oven temperature at 50°C]
proportionalGain = 0.1
integralGain = 0.001
derivativeGain = 1

controlVariableMin = 0.0
controlVariableMax = 1

setPointValue = 50

processVariableChannel = Oven Temperature
actionName = Pwm
dutyCycle = %controlVariable%
frequency = 1
```

- `proportionalGain`, `integralGain` and  `derivativeGain` are the *gains* of PID.
- `controlVariableMin` and `controlVariableMax` are used to limit the range, in which ***control variable*** can change. In this case ***control variable*** can take values anywhere from `0` to `1`.
- `setPointValue` - is the desired temperature.
- `processVariableChannel` is set to *channel* `Oven Temperature`, which contains near-real-time data from a temperature sensor.
- *action* `Pwm` is executed every time new value of ***control variable*** is calculated. (Note: *Action* `Pwm` is implemented by AutoBits Solid State Relay module. PWM stands for Pulse Width Modulation.)
	- `dutyCycle` is a parameter of `Pwm` *action*. ***Control variable*** of PID is used as an input.
	- `frequency` is another parameter of `Pwm` *action*. In this case, PWM frequency is set to 1Hz.