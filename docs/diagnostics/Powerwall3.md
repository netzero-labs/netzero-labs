---
layout: with_footer
---

# Netzero - Powerwall 3 Diagnostics

## Introduction

[Netzero](https://www.netzero.energy) provides access to diagnostic data for your Powerwall 3 system that is not available in the Tesla app. This data includes battery capacity and degradation, as well as solar string production (solar output broken down by individual strings of panels). These diagnostics can help you monitor system health, track performance over time, and identify potential production issues.

## Credentials

To access Powerwall 3 diagnostics, you need the Wi-Fi network name and password for the “leader” Powerwall 3 battery. In systems with multiple batteries, the installer designates one unit as the leader.

The Wi-Fi credentials are printed on a QR code located behind the cover of the leader Powerwall 3. Since the cover should only be removed during installation or servicing, it’s best to photograph the QR code when the cover is off. If that’s not possible, you can contact Tesla Support to request the Wi-Fi network name and password.

The Wi-Fi name will begin with **TeslaPW** and can also be discovered by standing next to the leader battery with your phone and checking the list of available networks.

## Access

Once you have the TeslaPW Wi-Fi name and password, open Netzero on your mobile device and go to **Monitoring > Connect**. You can either enter the credentials manually or scan the QR code if you have it available.

When you connect, Netzero will temporarily join the Powerwall’s built-in Wi-Fi network, retrieve the diagnostic data, and then automatically reconnect to your home Wi-Fi. The retrieved data will appear in the **Powerwall** and **Strings** tabs.

On iOS, Netzero requires permission to connect to the **Local Network**. If you previously denied this permission, you can re-enable it in your device’s settings: **Settings > Apps > Netzero > Local Network**.

**Note:** Diagnostic access is only available from the mobile app (iPhone or Android). Due to web browser security restrictions, it is not available in the Netzero web app.

## Diagnostic Data

### Powerwall Capacity

Like all lithium-ion batteries, the Powerwall’s usable capacity declines gradually over time. Netzero allows you to track this degradation so you can compare it against expectations or warranty terms. For details on Powerwall 3’s warranty coverage, see [Tesla’s documentation](https://www.tesla.com/support/energy/powerwall/documents/documents).

### String-Level Data

String-level data shows the current, voltage, and power for each string of solar panels connected to your inverters. This allows you to pinpoint underperforming strings and investigate potential production issues.

For guidance on how to interpret string-level readings, see [Diagnosing Solar Production Issues](https://www.netzero.energy/docs/diagnostics/solar_production).

**Notes:**

- The UK and Australian versions of the Powerwall 3 have 3 MPPT (Maximum Power Point Tracking) ports, while the US version has 6 MPPT ports.
- Despite having only 3 MPPT ports, the 3-MPPT versions still report data for 6 strings in the diagnostics view. We believe this is because each MPPT port is internally split into two parallel ports. This design would also explain the higher maximum current per MPPT on the 3-port models (26 A vs 13 A on the US 6-port version).
- In this configuration, the Tesla One app may display incorrect totals, while Netzero’s values correctly add up to the actual solar production.
- To determine the output of each of the 3 strings on a 3-MPPT system, sum the readings for the paired ports: **1+2**, **3+4**, and **5+6**.

## Troubleshooting

If the connection fails or no diagnostic data appears:

1. Check permissions on your phone: **device Settings > Apps > Netzero**. Permissions will vary between
   iOS and Android, but the required ones are: **Location** (location is not used by Netzero, but
   Wi-Fi access requires this permission), **Local Network** / **Nearby devices**, and **Camera** (when using QR codes).

2. Make sure you are on your home Wi-Fi network before connecting to the TeslaPW Wi-Fi network.
   The TeslaPW network does not have internet access, so phones will sometimes switch to cellular data
   and interfere with the connection. You can temporarily turn on **Airplane Mode** to avoid that problem.

3. **Verify Wi-Fi credentials**
   - Try connecting to the TeslaPW network directly through your phone’s Wi-Fi settings.
   - If successful, return to Netzero and attempt the connection again.
   - If unsuccessful, try [turning the system off and on again](https://energylibrary.tesla.com/docs/Public/EnergyStorage/Powerwall/3/OwnerManual/en-us/GUID-D239D3CE-AED7-41EA-88C0-13566FDF966C.html).
   - If the problem persists, contact Tesla Support to confirm the correct credentials.

4. **Test with the Tesla One app**
   - In some cases we've seen that a connection with the Tesla One app has to be established first (only once). You can find the Tesla One app here:
       [iOS](https://apps.apple.com/us/app/tesla-one/id1625770308) | [Android](https://play.google.com/store/apps/details?id=com.tesla.teslapros).
   - Sign in as an **External Partner** using your Tesla credentials.
   - Go to **More > Tesla Device Setup**, select **Manually Enter**, and provide the Wi-Fi network details.
   - If this also fails, try [turning the system off and on again](https://energylibrary.tesla.com/docs/Public/EnergyStorage/Powerwall/3/OwnerManual/en-us/GUID-D239D3CE-AED7-41EA-88C0-13566FDF966C.html) before retrying.
