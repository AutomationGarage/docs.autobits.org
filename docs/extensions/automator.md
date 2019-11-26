---
title: Automator
sidebar_label: Automator
---

lets you create simple automation scenarios.

##### Execute an action as a reaction to an event:

```ini
[Start 'notepad.exe' when Button 1 is clicked]
when = Web User Interface :: Button 1 :: Clicked
execute = Application Runner :: Run Application
applicationPath = C:/Windows/System32/notepad.exe
```

- `when` - defines an *event*, that will trigger the *action*. `Web User Interface :: Button 1 :: Clicked` is the *event* in this case.
- `execute` - defines an *action*. `Run Application` is the name of the *action* in this case.
- `applicationPath` - is a *parameter* of *action* `Run Application`.

##### Schedule something to happen at a specific time:

```ini
[Start 'notepad.exe' every day at 18:00]
at = 18:00
execute = Application Runner :: Run Application
applicationPath = C:/Windows/System32/notepad.exe
repeat = every day
```

- `at` - defines the time, at which the *action* will be executed. Time format is `HH:mm` or `HH:mm dd.MM.yyyy`.
- `repeat` - *(optional)* can be used to continue executing an action repeatedly. It sets the repetition interval in milliseconds(ms), seconds(s), minutes(m), hours(h), days(d). A combination of time intervals can be used (e.g 1d 2h 20m 20s 200ms). Alternatively, it can be set to `every day` or `every weekday` or comma-separated list of days of the week: `Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday`.

If you are familiar with <a href="https://en.wikipedia.org/wiki/Cron" title="Wikipedia article about Cron" target="_blank">Cron</a>, you can use <a href="https://en.wikipedia.org/wiki/Cron#CRON_expression" title="Wikipedia article about Cron. Section 'CRON expression'" target="_blank">CRON expression</a> to define an execution schedule:

```ini
at = 0 0 18 1/1 * ? * 
```

If you use CRON expression to define a schedule, parameter `repeat` is not needed, because CRON expression contains instructions for repeats.

<a href="http://www.cronmaker.com" title="CronMaker website" target="_blank">CronMaker</a> online utility can help you with CRON expressions.

##### Execute an action if a condition is fulfilled:

```ini
[Send an email if CPU Load is more than 70%]
if = Computer Hardware Monitor :: CPU Total Load :: % > 70
execute = Email Sender :: Send Email
to = test@example.com
subject = Too high CPU Load
message = CPU Load is %value%
resetAfter = 10m
resetIf = Computer Hardware Monitor :: CPU Total Load :: % < 50
resetAt = 18:00
resetWhen = AutoBits Application :: App :: Started
```

- `if` - describes a condition that has to be met for the *action* to be executed. In this case, it is *CPU Load* being more than 70%.

Without a reset condition, AutoBits will execute the *action* for every `CPU Total Load` *data point*, that meets the condition(i.e., trigger resets immediately). To prevent trigger reset, optional reset conditions are used:

- `to`, `subject`, `message` - are *parameters* of *action* `Send Email`.
- `resetAfter` - *(optional)* prevents subsequent execution of an *action* for a specified time in milliseconds(ms), seconds(s), minutes(m), hours(h), days(d). A combination of time intervals can be used (e.g 1d 2h 20m 20s 200ms).
- `resetIf` - *(optional)* prevents subsequent execution of an *action* until a specified condition is fulfilled.
- `resetAt` - *(optional)* prevents subsequent execution of an *action* until a specified time. Time format is `HH:mm` or `HH:mm dd.MM.yyyy`
- `resetWhen` - *(optional)* prevents subsequent execution of an *action* until a specified *event* happens.

Variable `%value%` holds the *data point* value, that triggered the `if = ` condition. Use the variable to pass the triggering value as (a part of) *action* argument. In the example above:

```ini
message = CPU Load is %value%
```

##### Execute multiple actions:

If you need to execute multiple actions, a *scenario* can be split into *steps*:

 ```ini
[Start Notepad]
execute = Application Runner :: Run Application
applicationPath = C:/Windows/System32/notepad.exe

[Start Calculator]
execute = Application Runner :: Run Application
applicationPath = calc
delayBefore = 1s

[Run Notepad and Calculator]
when = Web User Interface :: Button :: Clicked
executeStep1 = Start Notepad
executeStep2 = Start Calculator
```

- `[Start Notepad]` and `[Start Calculator]` are *steps*, each executing an *action*.
- `[Run Notepad and Calculator]` is a *scenario* that executes both steps.
- optional parameter `delayBefore` delays execution of a step. In the example above, step `[Start Calculator]` is delayed by 1 second. Delay can be set in milliseconds(ms), seconds(s), minutes(m), hours(h), days(d). A combination of time intervals can be used (e.g 1d 2h 20m 20s 200ms).