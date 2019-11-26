---
title: Call REST API and parse response using AutoBits
sidebar_label: Call REST API and parse response
---

How to use AutoBits REST Service Client extension to call [OpenWeather](https://openweathermap.org/api) API to retrieve weather information.

## 1. Configure Automator extension to send HTTP requests

Create a scenario to make a request at a specific time and repeat the call with one-second interval:

```ini
autoStart = true

[Fetch Temperature in London]
at = 17:40
execute = REST Service Client :: Make Request
url = https://samples.openweathermap.org/data/2.5/weather?q=London,uk&appid=b6907d289e10d714a6e88b30761fae22
method = GET
processResponse = Parse Data Point
dataPointName = Temperature in London
dataPointUnit = °F
dataPointValueJsonPath = main.temp
repeat = 1s
```

![Configure Automator to send request OpenWeather api](/img/quickstart/rest-configure-automator-v2.png)
*Configure Automator to make requests to [OpenWeather](https://openweathermap.org/api) API.*

At **17:40** **REST Service Client** extension will make a **GET** request to [OpenWeather](https://openweathermap.org/api) API using the specified **URL**. It will repeat the call every second.

Setting **dataPointValueJsonPath** specifies JSON property to use as a data point value.

Consider this response from [OpenWeather](https://openweathermap.org/api) API for example:

```json
{
   "coord":{
      "lon":-0.13,
      "lat":51.51
   },
   "weather":[
      {
         "id":300,
         "main":"Drizzle",
         "description":"light intensity drizzle",
         "icon":"09d"
      }
   ],
   "base":"stations",
   "main":{
      "temp":280.32,
      "pressure":1012,
      "humidity":81,
      "temp_min":279.15,
      "temp_max":281.15
   },
   "visibility":10000,
   "wind":{
      "speed":4.1,
      "deg":80
   },
   "clouds":{
      "all":90
   },
   "dt":1485789600,
   "sys":{
      "type":1,
      "id":5091,
      "message":0.0103,
      "country":"GB",
      "sunrise":1485762037,
      "sunset":1485794875
   },
   "id":2643743,
   "name":"London",
   "cod":200
}
```

In this case, a data point **Temperature in London** with the value of **280.32 °F** will be generated.

*Note: OpenWeather sample API returns same temperature for every request.*

## 2. Test

Open a dashboard and create a panel to represent received data points:

* On the dashboard: *Right Click -> Add Panel -> Plot.*

* Open panel settings (using gear icon). Select the data channel **Temperature in London**.

* Save the dashboard by clicking **Save Changes**.

![Temperature in London on a plot](/img/quickstart/rest-dashboard.png)
*Temperature in London on a plot.*

## Conclusion

This guide shows how to make REST calls from automation scenarios.
