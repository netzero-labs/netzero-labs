---
layout: with_footer
---

# Netzero – Backup Mode

**Update Aug 14, 2025** - New guidelines for using Backup mode. Earlier versions suggested setting backup reserve to 100% when using backup mode.
This is no longer required, and configuring Grid Charging is now the preferred way to use the new mode. You may want to update your
existing automations.

## Overview

[Netzero](https://www.netzero.energy) supports **Backup Mode**, a Powerwall operational mode that charges the battery from the grid at a faster rate — around **3.3 kW per battery** (see *Charging Rates* below). Backup Mode can also be used to preserve Powerwall charge.

**Important notes:**

* **Not supported in the Tesla app.** When enabled via Netzero, the Tesla app will show no operational mode selected. You can still use the Tesla app to switch back to Self-Powered or Time-Based Control. In Netzero, all modes are supported and displayed correctly.
* Backup Mode can be set as an automation action (**Set operational mode**) or manually from **Automation > Configuration** (useful for testing).


## Using Backup Mode

### 1. Faster Charging from the Grid

Previously, grid charging required setting the backup reserve to 100% and resetting it later via automations, charging at about **1.8 kW per battery**.

To charge faster — about **3.3 kW per battery** — use Backup Mode. **Grid Charging** must be enabled.
Example automation:

```
Every day at 12:00 AM: Set operational mode to Backup; Set grid charging to Enabled.
Every day at 6:00 AM: Set operational mode to Self-Powered.
```

**Note:** To stop charging, switch the mode back to your normal setting (Self-Powered or Time-Based Control). You may also disable Grid Charging if desired.


### 2. Preserving Powerwall Charge

Backup Mode can also prevent discharge. This is similar to the **Preserve Battery Charge** automation (which sets the backup reserve to the current state of charge), but [Tesla’s recent changes](https://docs.netzero.energy/docs/tesla/BackupReserveUpdate) prevent that method from working between 81–99% state of charge.

Backup Mode has no such limitation. To preserve charge, enable Backup Mode with Grid Charging **disabled**.
Example automation:

```
When vehicle charging starts: Set operational mode to Backup; Set grid charging to Disabled.
When vehicle charging stops: Set operational mode to Self-Powered.
```

**Note:** Remember to reset the operational mode to your normal setting, and Grid Charging if needed.


## Charging Rates by Mode

| Mode                        | Grid Charging? | Typical Rate per Battery | Notes |
|-----------------------------|----------------|--------------------------|-------|
| **Time-Based Control**      | Required       | ~5 kW                    | Fastest charging; Tesla controls when charging occurs during off-peak hours. |
| **Backup Mode (Netzero)**   | Required       | ~3.3 kW                  | Charges from solar (if available) and grid to 100%. |
| **Self-Powered**            | Optional       | ~1.8 kW                  | Setting backup reserve to 100% (or any value above the current state of charge) forces charging from solar and grid. |

**Multiple Batteries:** Charging rates scale with the number of Powerwalls (e.g., ~6.6 kW for two in Backup Mode), but:

* Utility import limits may reduce the rate.
* Powerwall 3 expansion packs charge slower than full Powerwall 3 units — see the [Powerwall 3 Datasheet](https://energylibrary.tesla.com/docs/Public/EnergyStorage/Powerwall/3/Datasheet/en-us/Powerwall-3-Datasheet.pdf).

Other grid-charging methods exist (e.g., manual Storm Watch or VPP events), but these cannot be automated in Netzero.
