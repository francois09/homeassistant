# homeassistant

This repository contains for now only blueprints for managing heater system

## Principle

1. Each room is autonomous, and have helpers for their properties
2. Each room should have a climate valve, and a T° sensor

## How it works

Based on triggers, each room will compute the T° setpoint, and if necessary activate a helper
saying it needs heating.

Another automation (not included here for now), will decide to start or stop the heating system
if rooms need it or no.
