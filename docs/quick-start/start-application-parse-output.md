---
id: start-application-parse-output
title: Start an application programmatically using AutoBits
sidebar_label: Start an application programmatically
---

How to run PowerShell script and parse its output to monitor RAM used by a process.

## 1. Create a PowerShell script to retrieve stats of a process

Create a file GetProcessRAM.ps1 and put the following in:

```powershell
$usedMemory = ((Get-Counter "\Process($args)\Working Set - Private").CounterSamples | Select-Object -ExpandProperty CookedValue) / 1mb
Write-Output "RAM used by $args :: $($usedMemory) :: M_B"
```

This PowerShell script retrieves RAM used by a process and writes the value to the standard output.

## 2. Configure Automator extension to run the script

Create a scenario to execute PowerShell at a specific time and repeat the execution with one-second interval. Pass path to the script and name of a process as arguments.

```ini
autoStart = true

[Poll AutoBits RAM usage]
at = 21:18
execute = Application Runner :: Run Application
applicationPath = powershell
args = "C:\GetProcessRAM.ps1" "AutoBits"
processOutput = Parse Data Point
createNoWindow = true
repeat = 1s
```

In this example, we are going to get RAM used by AutoBits itself.

![Configure Automator extension to run the script](/quickstart/run-application-powershell-v2.png)
*Configure Automator extension to run the script.*

## 3. Test

* On the dashboard: *Right Click -> Add Panel -> Plot*.

* Open panel settings (using gear icon). Select the data channel **RAM used by AutoBits**.

* Save the dashboard by clicking **Save Changes**.

![RAM used by AutoBits on a plot](/quickstart/run-application-used-ram.png)
*RAM used by AutoBits on a plot.*

## Conclusion

This guide shows how to start an application from automation scenario and extract data points from its output.
