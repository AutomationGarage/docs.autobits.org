---
title: Application Runner
sidebar_label: Application Runner
---

lets you start any application programmatically.

It provides *action* `Run Application`.

Using this *action*, you can start applications from automation scenarios or as a reaction to an *event*.

The *action* has parameters:

- `applicationPath` - path to an executable to start.
- `args` - *(optional)* if present, it's value is passed as an argument to the executable.
- `processOutput` - *(optional)* defines whether application output (standard output) has to be parsed to extract an *event* or a *data point*.

#### Processing output

To extract *events* and *data points* from application output specify parameter `processOutput`.

##### AutoBits standard format

AutoBits will automatically parse output, without extra configuration, if output is formatted in the following manner:

`[event source]::[event name]` - to publish an *event*.

`[channel name]::[value]::[unit]` - to publish a *data point*.

##### Parsing *data point*

To parse *data point* name, configure one of the following:

- `dataPointName` - a constant to use as a name for the *data point*
- `dataPointNameJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a name for the *data point*, in case output is JSON
- `dataPointNameRegExp` - a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the name for the *data point* from output text

To parse data point unit configure one of the following:

- `dataPointUnit` - a constant to use as a unit for the *data point*
- `dataPointUnitJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a unit for the *data point*, in case output is JSON
- `dataPointUnitRegExp`- a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the unit for the *data point* from output text

To parse data point value configure one of the following:

- `dataPointValueJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a value for the *data point*, in case output is JSON
- `dataPointValueRegExp` - a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the value for the *data point* from output text

##### Parsing *event*

To parse event source configure one of the following:

- `eventSource` - a constant to use as a source for the *data point*
- `eventSourceJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a source for the *event*, in case output is JSON
- `eventSourceRegExp` - a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the source for the *event* from output text

To parse event name configure one of the following:

- `eventName` - a constant to use as a name for the *event*
- `eventNameJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a name for the *event*, in case output is JSON
- `eventNameRegExp` - - a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the name for the *event* from output text
