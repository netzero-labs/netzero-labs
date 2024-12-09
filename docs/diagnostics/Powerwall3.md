---
layout: default
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

## Questions or Issues

If you have any questions or issues, please submit them via [Netzero Issues](https://github.com/netzero-labs/netzero/issues).
