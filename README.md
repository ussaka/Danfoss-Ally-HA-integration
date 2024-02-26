# Danfoss Ally Home Assistant automations & scripts
Danfoss Ally eTRV automatons and scripts for Home Assistant with Zigbee2MQTT. Tested to work with firmware v1.28(00.28.0008 00.28)

# Time updater automation
![version](https://img.shields.io/badge/version-1.0.1-blue?style=plastic)

Danfoss Ally has no knowledge of the current time. Zigbee coordinator must send the current time to it. Recommended time update interval is weekly.

### Installation
**1. Create helpers**
- Schedule
    - Run weekly
- Date and/or time x2
    - Use date and time
    - Set DST start and end times

[![Open your Home Assistant instance and show your helper entities.](https://my.home-assistant.io/badges/helpers.svg)](https://my.home-assistant.io/redirect/helpers/)

**2. Import blueprint and create the automation**

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fussaka%2FDanfoss-Ally-HA-integration%2Fblob%2Fmain%2Fautomations%2Fdanfoss_ally_time_updater.yaml)

# Weekly schedule script
![version](https://img.shields.io/badge/version-1.0.0-blue?style=plastic)

### Note!
- The weekly schedule is lost after power cycle or OTA or error state.
- HA DST start helper will convert set time to the new local time. E.g. 31/03/2024 03:00 --> 31/03/2024 04:00. For now fix by setting the time minute before DST start time e.g. 02:59.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fussaka%2FDanfoss-Ally-HA-integration%2Fblob%2Fmain%2Fscripts%2Fdanfoss_ally_set_schedule.yaml)

# External temperature sensor automation
[Blueprint](https://community.home-assistant.io/t/zigbee2mqtt-danfoss-ally-send-external-temperature-to-trv-version-2/627564/8)

### Radiator covered = false
Automatically adjust eTRV's own temperature with offset. The external temperature needs to be send at least every 3 hours but no more often than every 30 minutes @ every 0,1K change.

### Radiator covered = true
Rely only for the external temperature. The external temperature needs to be send at least every 30 minutes but no more often than every 5 minutes @ every 0,1K change.