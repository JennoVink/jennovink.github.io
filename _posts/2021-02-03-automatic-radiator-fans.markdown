---
layout: post
title:  "Automatic radiator fans"
date:   2021-02-03 13:00:00
description: "Creating my own radiator fans to heat up the living room more quickly - my approach"
image: /img/radiator-fans-diagram.png
published: true
tags: HobbyProject DotNet Core
---

Creating my own radiator fans to heat up the living room more quickly

## The idea

I was inspired by [this idea](https://www.conrad.nl/info/guides/zelfbouwprojecten/cv-met-ventilatoren) to make my own radiator fans. The concept is simple: install fans that blow extra air trough the radiator to increase the speed in which the radiator can release its heat. The radiator fans are simple [usb fans](https://nl.aliexpress.com/item/4000129511164.html) connected to [a hub](https://nl.aliexpress.com/item/4000618337325.html). This hub is connected to an [Ikea TRÅDFRI smart socket](https://www.ikea.com/nl/en/p/tradfri-wireless-control-outlet-90356166/) which can be turned on by software I wrote.

## Software

Although this sounds more as a hardware project, there is an interesting software component: turing on the fans if the radiator is warm (and turning it off when needed). I have a google nest thermostat which I can access via [an API](https://developers.google.com/nest/device-access). The only thing left is to write software that retrieves from the thermostat if it's on, and if so: turn on the smart socket (which communicates via Zigbee). 


## Summarizing
![Overview of the individual components in this project](/img/radiator-fans-diagram.png "Overview of the individual components in this project")

## .NET CORE application

The .NET core application (see image above) uses oAuth2 to authenticate itself to the [Google device access API](https://developers.google.com/nest/device-access/traits). For me, this was the first serious introduction to oAuth2. I quickly had a basic application running (with help of [the get started guide](https://developers.google.com/nest/device-access/get-started)) that could read values from the API.

A request + response could look like this:
```bash
curl -X GET 'https://smartdevicemanagement.googleapis.com/v1/enterprises/project-id/devices/{device-id-here}' \
    -H 'Content-Type: application/json' \
    -H 'Authorization: Bearer access-token-here'
```
-- example response: --
```json
      "type": "sdm.devices.types.THERMOSTAT",
      "assignee": "enterprises/{some long id}",
      "traits": {
        "sdm.devices.traits.Info": {
          "customName": ""
        },
        "sdm.devices.traits.Humidity": {
          "ambientHumidityPercent": 64
        },
        "sdm.devices.traits.Connectivity": {
          "status": "ONLINE"
        },
        "sdm.devices.traits.Fan": {},
        "sdm.devices.traits.ThermostatMode": {
          "mode": "HEAT",
          "availableModes": [
            "HEAT",
            "OFF"
          ]
        },
        "sdm.devices.traits.ThermostatEco": {
          "availableModes": [
            "OFF",
            "MANUAL_ECO"
          ],
          "mode": "OFF",
          "heatCelsius": 18.18419,
          "coolCelsius": 24.44443
        },
        "sdm.devices.traits.ThermostatHvac": {
          "status": "OFF" <----- this value is "ON" when the thermostat is heating.
        },
        "sdm.devices.traits.Settings": {
          "temperatureScale": "CELSIUS"
        },
        "sdm.devices.traits.ThermostatTemperatureSetpoint": {
          "heatCelsius": 18.2243 <--- this value is logged to a csv for further data analysis.
        },
        "sdm.devices.traits.Temperature": {
          "ambientTemperatureCelsius": 18.71999 <--- this value is also logged to csv.
        }
      },
      "parentRelations": [
        {
          "parent": "enterprises/{some long id}",
          "displayName": "Woonkamer"
        }
      ]
    }
  ]
}
```

### Quick data analysis
As you can see, the target- and current temperature are logged to a csv file for data analysis later on. Below, an example of today. The sudden drops are because of a programmable 'clock program' in which the temperature can be ajusted based on the current time.

![Excel graph showing a small timeframe with the target- and current temperature.](/img/temperature-graph.png "Quick data analysis of the temperature with a small timeframe")

## Back to the software!
After reading the values from the API, the next thing that had to be implemented is communication with the smart socket. This was quite doable after installing a [library](https://github.com/tomidix/CSharpTradFriLibrary) and entering the 'secret' that is located at the backside of the IKEA tradfri hub. 
If the thermostat isn't heating anymore, I configured that the fans stay on for another 20 minutes (assuming that there is a lot of remaining heat in the system) via a simple timer.

## Looking back
In my opinion, it's very satisfying that you have an idea in your head and it's possible to realize it on my own. Installing .NET CORE on a raspberry pi and running my application was fun in my opinion. Maybe I've inspired you to do such a project yourself.

