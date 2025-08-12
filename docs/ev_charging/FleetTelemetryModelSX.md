---
layout: with_footer
---

# Fleet Telemetry for Pre-2021 Model S/X

## Overview

[Netzero](https://www.netzero.energy) uses EV charging data from Tesla’s Fleet Telemetry to run
vehicle charging automations and retrieve charging data. With vehicle firmware version 2025.20,
Tesla has added Fleet Telemetry support for Model S and Model X vehicles built before 2021 that
have the Intel Atom computer (also known as MCU2).

Fleet Telemetry provides access to Tesla’s updated data stream for EV charging. This enables:

- Fewer vehicle wake-ups when retrieving data.
- Faster and more reliable execution of charging automations.
- Charging data included in Netzero’s energy charts.

**Note:** MCU2 is standard in most Model S/X vehicles built after March 2018.
Vehicles built on or before March 2018 typically have the older MCU1 system.
MCU1 does not support Fleet Telemetry unless upgraded to Tesla’s newer infotainment hardware.

## How to Enable

1. Ensure your Tesla is updated to firmware version **2025.20 or later**.
2. In the vehicle’s **Safety** screen, enable:
   **Allow Third-Party App Data Streaming**.
3. In Netzero, go to **Settings > Vehicle Charging**.
4. If you have not granted Netzero permissions for **Vehicle Information** and **Charging
   Management**, follow the prompts to do so.
5. Once permissions are granted, select **Pair Vehicle**.
6. You may need to wait for the vehicle to come online before the status updates.

After the in-car option is enabled and the vehicle is paired, Fleet Telemetry data will begin
streaming automatically.
