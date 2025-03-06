---
layout: with_footer
---

# Netzero - Powerwall 3 Diagnostics

## Introduction

[Netzero](https://www.netzero.energy) provides access to diagnostic data for your Powerwall 3 system. This data is not available in the Tesla app. The diagnostic data includes battery capacity and degradation, and solar string production (solar production broken down by strings of solar panels).

## Credentials

Powerwall 3 diagnostics access requires the Wi-Fi network and password for the "leader" Powerwall 3 battery. In a system with multiple batteries, installers will designate one of them as the leader. The Wi-Fi network name and password are printed on a QR code that is behind the cover of the leader Powerwall 3. Since this cover should only be removed during installation or servicing, it's recommended to photograph the QR code when the cover is off. If that's not an option, you can contact Tesla Support to get the Wi-Fi name and password.

The Wi-Fi name will start with TeslaPW and can also be retrieved by standing next to the leader Powerwall 3 with your phone and observing the list of available Wi-Fi networks.

## Access

Once you have the TeslaPW Wi-Fi network name and password, enter them in Netzero (Monitoring > Connect). Alternatively, you can scan the QR code if you have access to it. Netzero will connect to the built-in Wi-Fi network, collect diagnostic data, and reconnect to your home Wi-Fi network. The diagnostic data will be displayed in the Powerwall and Strings tabs.

## Diagnostic Data

### Powerwall Capacity

Like every lithium-ion battery, Powerwall will degrade over time and lose capacity. Netzero allows you to track the degradation over time. Refer to the [Tesla documentation](https://www.tesla.com/support/energy/powerwall/documents/documents) for warranty details on Powerwall 3.

### String-level Data

String-level data shows current, voltage, and power for each string of arrays connected to your inverters. This can be useful for investigating production issues and finding issues with individual strings of solar panels.

See [Diagnosing Solar Production Issues](https://www.netzero.energy/docs/diagnostics/solar_production) for help with interpreting string-level data.

#### Notes

- The UK and Australian versions of the Powerwall 3 have 3 ports for connecting solar strings (also known as Maximum Power Point Tracking or MPPT ports), while the US version has 6 ports. Despite the 3 MPPT ports, you will see values for 6 strings in string diagnostics. We believe this is because the 3-MPPT port versions actually have 6 ports under the hood, where each of the 3 ports is paralleled into two ports. This implementation would also explain why the 3-MPPT version has a higher maximum current per MPPT (26A vs 13A for the 6-MPPT US version). The Tesla One app shows incorrect data in this case, while the power values in Netzero add up to the correct total solar production.
