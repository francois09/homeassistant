# NO MORE USED

This repo is replaced by [HA_blueprints](https://github.com/francois09/HA_blueprints) for the public part, and [HA_config](https://github.com/francois09/HA_config) for the private config part.

# homeassistant

This repository contains blueprints for managing heater system, and parts of configuration yaml files

## Principle

1. Each room is autonomous, and have helpers for their properties
2. Each room should have a climate valve, and a T° sensor
3. A global blueprint is in charge of collecting rooms needs to decide to start heater/climate

## How it works

Based on triggers, each room will compute the T° setpoint, and if necessary activate a helper
saying it needs heating.

Another automation will decide to start or stop the heating system if rooms need it or no.

### Heater start/stop global script

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ffrancois09%2Fhomeassistant%2Fblueprints%2Fheater_one_need.yaml)

This blueprint is the global on/off heating system. It collects every heater requests from rooms, and decide if home heater should be started or not.

### Heater request compute

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Ffrancois09%2Fhomeassistant%2Fmain%2Fblueprints%2Fheater_request_compute.yaml)

This blueprint compute the boolean (switch) helper of the room, based on Climate valve setpoint, and room T°. If heating is requested, it aslo fake the local_temperature_calibration to ensure valve is correctly opened. In my case, T° sensor is far from Climate, and close to my preffered location in the room.

### Heater setpoint compute

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Ffrancois09%2Fhomeassistant%2Fmain%2Fblueprints%2Fheater_setpoint_compute.yaml)

This blueprint compute the correct setpoint based on the room schedule and the potential manual setting, to determine and send it to the Climate valve.

### Heater switch mode

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Ffrancois09%2Fhomeassistant%2Fmain%2Fblueprints%2Fheater_switch_mode.yaml)

This blueprint take into account a manual change on the Climate valve, or the Auto setting to modify setpoint.
