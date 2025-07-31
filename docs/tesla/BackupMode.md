---
layout: with_footer
---

# Netzero - Backup Mode

## Backup Mode Operation

[Netzero](https://www.netzero.energy) supports **Backup Mode**, an experimental Powerwall operational
mode that charges the battery from the grid at a faster rate—around **3.3 kW per battery** (see below for
details on charging rates).

**Important notes:**

* **Backup Mode is not supported by the Tesla app.** When enabled via Netzero, the Tesla app will
show no operational mode selected. You can, however, use the Tesla app to switch back to
Self-Powered or Time-Based Control. In Netzero, all modes are supported and correctly displayed.

* **Backup Mode is experimental** while we assess reliability and compatibility. We'll update its
status based on user feedback.

* **Backup reserve is always set to 100% in Backup Mode.** Changing the reserve has no effect. In
this mode, the Powerwall will not discharge and will reserve 100% of its capacity for outages.

* **Backup Mode is intended for charging only.** If your goal is simply to reserve 100% of battery
capacity for outages, set the backup reserve to 100% in another mode instead.

* The mode can be selected as an automations action (under **Set operational mode**) or from the
  **Automation > Configuration** screen (for testing).

## How to Use Backup Mode

Previously, charging the Powerwall from the grid involved setting the backup reserve to 100% and
resetting it later using automations. This method charged the Powerwall at about **1.8 kW per battery**.

To charge faster—around **3.3 kW per battery**—use Backup Mode:

```
Every day at 12:00 AM: Set operational mode to Backup.
Every day at 6:00 AM: Set backup reserve to 20%; Set operational mode to Self-Powered.
```

**Important:**

* After charging, reset the backup reserve (since Backup Mode locks it at 100%).
* Reset the operational mode to Self-Powered or Time-Based Control after charging completes.

## Powerwall Charging Rates Overview

Powerwalls charge from the grid at different rates, depending on the method:

* **Time-Based Control mode:**

  * May charge from the grid during off-peak hours (not guaranteed—Tesla controls this).
  * Charging rate: **\~5 kW per battery** (fastest).
  * Requires Grid Charging to be enabled.

* **Self-Powered mode:**

  * Setting backup reserve to 100% will force charging from solar (if available) and grid.
  * Charging rate: **\~1.8 kW per battery**.

* **Backup Mode (Netzero only):**

  * Charges from solar (if available) and grid to 100%.
  * Charging rate: **\~3.3 kW per battery**.

**Multiple Batteries:**
Charging rates scale with the number of Powerwalls (e.g. 6.6 kW for two batteries in Backup Mode), but:

* Utility import limits may reduce the rate.
* Powerwall 3 expansion packs charge slower than full Powerwall 3 systems. Refer to the
  [Powerwall 3 Datasheet](https://energylibrary.tesla.com/docs/Public/EnergyStorage/Powerwall/3/Datasheet/en-us/Powerwall-3-Datasheet.pdf) for details.

There are other ways of charging Powerwall from the grid, such as manual Storm Watch events or
VPP events. Since those cannot be automated, they are not relevant here.
