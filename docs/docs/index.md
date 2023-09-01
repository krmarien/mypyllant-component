---
title: Home
---

# myPyllant Library & Home Assistant Component

[![GitHub Release](https://img.shields.io/github/release/signalkraft/mypyllant-component.svg)](https://github.com/signalkraft/mypyllant-component/releases)
[![License](https://img.shields.io/github/license/signalkraft/mypyllant-component.svg)](LICENSE)
![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/signalkraft/mypyllant-component/build-test.yaml)

![myPyllant](https://raw.githubusercontent.com/signalkraft/myPyllant/main/logo.png){ align=right }

Home Assistant component that interfaces with the myVAILLANT API 
(and branded versions of it, such as the MiGo Link app from Saunier Duval & Bulex).
Uses the [myPyllant library](https://github.com/signalkraft/mypyllant).

## Installation

!!! note

    1. The developers are not affiliated with Vaillant, we take no responsibility for anything that happens to your devices because of this library
    1. This integration is not compatible with systems that use sensoAPP and multiMATIC

### HACS

1. [Install HACS](https://hacs.xyz/docs/setup/download)
2. Search for the myVAILLANT integration in HACS and install it
3. Restart Home Assistant
4. [Add myVaillant integration](https://my.home-assistant.io/redirect/config_flow_start/?domain=mypyllant)
5. Sign in with the email & password you used in the myVAILLANT app (or MiGo app for Saunier Duval)

### Manual

1. Download [the latest release](https://github.com/signalkraft/mypyllant-component/releases)
2. Extract the `custom_components` folder to your Home Assistant's config folder, the resulting folder structure should be `config/custom_components/mypyllant`
3. Restart Home Assistant
4. [Add myVaillant integration](https://my.home-assistant.io/redirect/config_flow_start/?domain=mypyllant), or go to Settings > Integrations and add myVAILLANT
5. Sign in with the email & password you used in the myVAILLANT app (or MiGo app for Saunier Duval)

## Tested Setups

* Vaillant aroTHERM plus heatpump + sensoCOMFORT VRC 720 + sensoNET VR 921
* Vaillant ECOTEC PLUS boiler + VR940F + sensoCOMFORT
* Vaillant ECOTEC PLUS boiler + VRT380f + sensoNET
* Vaillant ECOTEC PLUS VCW20/1 boiler + sensoCOMFORT VRC 720 + sensoNET VR 921
* Saunier Duval DUOMAX F30 90 + MISET Radio + MiLink V3
* Bulex Thema Condens F30/35 + Red 5 + MiPro Sense + MiLink v3

## Features

![Screenshot](https://raw.githubusercontent.com/signalkraft/mypyllant-component/main/screenshot.png)

* Supports climate & hot water controls, as well as sensor information
* Control operating modes, target temperature, and presets such as holiday more or quick veto
* Track sensor information of devices, such as temperature, humidity, operating mode, energy usage, or energy efficiency
* See diagnostic information, such as the current heating curve, flow temperature, or water pressure
* Custom services to set holiday mode or quick veto temperature overrides, and their duration

## Options

### Seconds between scans

Wait interval between updating (most) sensors. The energy data and efficiency sensors have a fixed hourly interval.

### Delay before refreshing data after updates

How long to wait between making a request (i.e. setting target temperature) and refreshing data.
The Vaillant takes some time to return the updated values.

### Default duration in hours for quick veto

When setting the temperature with the climate controls, the integration uses the "quick veto" feature of the myVAILLANT app.

With this option you can set for how long the temperature should stay set, before returning to the default value.

### Country

The country you registered your myVAILLANT account in. The list of options is limited to known supported countries.

### Brand

Brand of your HVAC equipment and app, pick Saunier Duval if you use the MiGo Link app.

## Supported Brands & Countries

!!! note "Missing a Country?"

    If a country is missing, please [open an issue](https://github.com/signalkraft/mypyllant-component/issues/new)
    or [contribute a new country to the myPyllant library](3-contributing.md#supporting-new-countries).

- Vaillant
    - Albania
    - Austria
    - Belgium
    - Bulgaria
    - Croatia
    - Czechia
    - Denmark
    - Estonia
    - Finland
    - France
    - Georgia
    - Germany
    - Greece
    - Hungary
    - Italy
    - Latvia
    - Lithuania
    - Luxembourg
    - Netherlands
    - Norway
    - Poland
    - Portugal
    - Romania
    - Serbia
    - Slovakia
    - Slovenia
    - Spain
    - Sweden
    - Switzerland
    - Ukraine
    - United Kingdom
    - Uzbekistan
- Saunier Duval
    - Austria
    - Czechia
    - Finland
    - France
    - Greece
    - Hungary
    - Italy
    - Lithuania
    - Poland
    - Portugal
    - Romania
    - Slovakia
    - Spain
- Bulex
    - Does not support country selection, just leave the option empty

## Known Issues

### Lack of Test Data for Different Systems

Your HVAC system might differ from the ones in [Tested Setups](#tested-setups) above.
If you don't see any entities, or get an error during setup, please check [Debugging](3-contributing.md#debugging) and create an issue.
With debugging enabled, there's a chance to find the culprit in the data returned by the myVAILLANT API and fix it.