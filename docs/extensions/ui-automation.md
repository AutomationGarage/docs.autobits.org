---
title: UI Automation
sidebar_label: UI Automation
---

lets you automate interactions with any application.

It allows AutoBits to interact with graphical UIs by emulating user actions. 

***Note:*** *This extension is an early technical preview. Documentation will be updated in coming releases.*

Using *action* `Run UI Automation Task`, you can interact with applications from automation scenarios.

The *action* has parameters:

- `task` - UI interaction task. The task has following format: `[process name | pid]::[UI element name | automation Id]::[interaction]`.
- `text` - (should be specified only for interaction **Text**). Specifies the text that will be inserted into a text input element.

`automation Id` can be discovered with `inspect.exe`

Supported interactions are:

- `Invoke`
- `ExpandOrCollapse`
- `Toggle`
- `Text`
- `Range`
- `Select`
- `DoubleClick`
- `Click`