---
id: RESTServiceClient
title: REST Service Client
sidebar_label: REST Service Client
---

lets you call REST web services and extract *data points* from responses.

It provides an *action* - `Make Request`.

Using this *action*, you can make HTTP requests from automation scenarios.

The *action* has parameters:

- `url` - URL to call
- `method` - *(optional)* HTTP method to use (GET, POST, PUT and DELETE are supported). If omitted, HTTP GET is used
- `body` - *(optional)* payload of the request
- `contentType` - *(optional)* **Content-Type** header
- `headers` - *(optional)* any other headers you wish to include. Has to be provided in the following format: `header-name : header value, another-header-name : another-header-value`
- `processResponse` - *(optional)* defines whether response has to be parsed to extract an *event* or a *data point*

#### Processing response

By specifying parameter `processResponse` you can parse response to a *data point*, *event* or both.

##### AutoBits standard format

AutoBits will automatically parse response, without extra configuration, if it is formatted in the following manner:

`[event source]::[event name]` - to publish an *event*.

`[channel name]::[value]::[unit]` - to publish a *data point*.

##### Parsing *data point*

To parse *data point* name, configure one of the following:

- `dataPointName` - a constant to use as a name for the *data point*
- `dataPointNameJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a name for the *data point*, in case response is JSON
- `dataPointNameRegExp` - a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the name for the *data point* from response text

To parse data point unit configure one of the following:

- `dataPointUnit` - a constant to use as a unit for the *data point*
- `dataPointUnitJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a unit for the *data point*, in case response is JSON
- `dataPointUnitRegExp`- a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the unit for the *data point* from response text

To parse data point value configure one of the following:

- `dataPointValueJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a value for the *data point*, in case response is JSON
- `dataPointValueRegExp` - a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the value for the *data point* from response text

##### Parsing *event*

To parse event source configure one of the following:

- `eventSource` - a constant to use as a source for the *data point*
- `eventSourceJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a source for the *event*, in case response is JSON
- `eventSourceRegExp` - a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the source for the *event* from response text

To parse event name configure one of the following:

- `eventName` - a constant to use as a name for the *event*
- `eventNameJsonPath` - a <a href="https://goessner.net/articles/JsonPath/" title="About JSONPath" target="_blank">JSONPath</a> expression to use when selecting JSON token to use as a name for the *event*, in case response is JSON
- `eventNameRegExp` - - a <a href="https://en.wikipedia.org/wiki/Regular_expression" title="Wikipedia article about Regular expressions" target="_blank">regular expression</a> to use for extracting the name for the *event* from response text
