---
layout: default
---

# Netzero - Powerwall 2 Diagnostics

## Introduction

[Netzero](https://www.netzero.energy) provides access to diagnostic data for your Powerwall 2 system.  This data is not available in the Tesla app. The diagnostic data includes battery capacity and degradation, and string diagnostics (solar production broken down by strings of panel arrays).

## Credentials

Powerwall 2 diagnostics access requires the IP address and password for the Tesla Gateway or Powerwall+ system.

The IP address is usually pre-populated, but if not, it should be listed with your other home network devices at your Wi-Fi access point or home router.

The default password consists of the last five characters of the Gateway password, which is printed on a label behind the Gateway or Powerwall+ cover. If you ever change the default password, use that instead. For Tesla Gateway 1 systems, the password will be the last 5 characters of the serial number.  For details, see Tesla's documentation on [Connecting to Tesla Gateway and Powerwall+
](https://www.tesla.com/support/energy/powerwall/own/connecting-network).

## Access

Once you have the IP address and password, enter them in Netzero (Monitoring / Connect). Netzero will connect to the Gateway, collect diagnostic data, and display it in the Powerwall and Strings tabs.

## Diagnostic Data

### Powerwall Capacity

Like every lithium-ion battery, Powerwall will degrade over time and lose capacity. Netzero allows you to track the degradation over time. Refer to the [Tesla documentation](https://www.tesla.com/support/energy/powerwall/documents/documents) for warranty details on Powerwall 2.

## Questions or Issues

If you have any questions or issues, please submit them via [Netzero Issues](https://github.com/netzero-labs/netzero/issues).
