---
layout: with_footer
---

# Netzero - Powerwall Automation

## Introduction

[Netzero](https://www.netzero.energy) automations control Powerwall settings, EV charging, and
heating or cooling devices. They can run on a schedule or respond to live events such as the battery
state of charge, energy flow, EV charging status, weather forecast, grid status, or electricity price.

## Automation Triggers

Automations can trigger based on time or events. The following triggers are available:

1. Time of day (optionally restricted to specific days of the week).
2. At sunrise or sunset, with an optional time offset of up to 4 hours before or after the event. Note: this feature requires your city location to be set in **Settings > Account**.
3. Powerwall state of charge: charged up to, or discharged down to a user-defined threshold.
4. Vehicle charging starts or stops.
5. Energy flow-based automations: when home usage, solar generation, grid import, or grid export rise above or drop below a threshold.
6. Electricity price-based automations: when import or export price is above or below a threshold.
7. Grid status-based automations: when the system goes off-grid or is back on grid.
8. Weather forecast-based automations: when the weather forecast is sunny, partly sunny, or cloudy.

Event triggers can optionally include a time restriction, to only run during specific time windows.

Notes:
- Event automations use so-called "edge triggers" (also known as "threshold crossing triggers"). They run when
  something changes -- not just when a condition is true, but when it becomes true. For example,
  "When Powerwall is charged up to 70%" will only trigger at the moment the Powerwall exceeds
  that state of charge. This has two important implications:
     - If the Powerwall is always above that threshold (e.g. due to a higher backup reserve setting),
       the automation will never run.
     - If the event has a time restriction (e.g. between 1-2pm), and Powerwall is charged up to 70%
       outside of that time frame, the automation will not run.
  
  The advantage of edge triggers is that it is easy to understand exactly when an automation will run, and how many times it will run. It is also
  less likely for one automation to conflict with another (since there is no state associated with automations).

- The vehicle charging automations are only available if you have a [supported EV charger or EV](https://docs.netzero.energy/docs/ev_charging/Settings).
  Similarly for heating and cooling devices.

## Automation Actions

The following actions are available:

- Set Powerwall backup reserve to a user-defined value.
- Set Powerwall backup reserve to the current state of charge. This will preserve the Powerwall's charge
  (prevent it from discharging), for example, when charging an EV.
- Set operational mode to **Self-Powered**, **Time-Based Control**, or **[Backup Mode](https://docs.netzero.energy/docs/tesla/BackupMode)**
- Set energy exports to **Solar only**, **Everything (solar and battery)** or **No exports**.
  Note: the **No exports** mode requires inverter support, and is only available for Powerwall+ and
  Powerwall 3.
- Set grid charging to Enabled or Disabled.
- Start or stop vehicle charging (requires a supported EV charger or EV).
- Send a notification only, with no other actions. Note: this action is only shown if no other actions
  are selected, since all actions notify by default.

Automations can optionally be configured to run only once. This can be used for one-off automations
or to test an automation. After such an automation runs, it will be automatically paused to prevent
future runs.

## Common Automations

Here are some commonly configured automations, and the goals they accomplish.

### EV charging without discharging the Powerwall

When in Self-Powered mode or during peak pricing in Time-Based Control mode, charging an EV might result in depleting the Powerwall. Usually that's not what users want, because the EV battery is much larger than the Powerwall. Netzero automations can prevent that, using integrations with EV or EV charger ([learn more](https://docs.netzero.energy/docs/ev_charging/Settings)). If the EV or EV charger is not supported, there are also automations based on home usage (home usage is usually measurably higher when charging an EV).

Example with a supported EV charger or EV:
```
When vehicle charging starts: Set backup reserve to the current state of charge (preserve Powerwall charge).
When vehicle charging stops: Set backup reserve to: 20%.
```

Example without a supported EV or EV charger (replace `8 kW` as needed, based on your charging rate):
```
When home usage rises above 8 kW: Set backup reserve to the current state of charge (preserve Powerwall charge).
When home usage drops below 8 kW: Set backup reserve to: 20%.
```

By setting the Powerwall backup reserve to its current state of charge, we prevent the battery from discharging. Once EV charging is done, we can reset the backup reserve to its usual value (replace 20% with your desired backup reserve).


### Charging the Powerwall while EV charging (Intelligent Octopus Go)

NOTE: Netzero now has a direct [Intelligent Octopus Go integration](https://www.netzero.energy/docs/intelligent_octopus_go). This section is only useful if you have an Ohme EV charger, where that integration cannot be used.

Octopus Energy consumers on the Intelligent Octopus Go tariff plan get special EV charging slots with lower rates, not otherwise reflected in the daily rates. It may make sense to charge the Powerwall in addition to the EV, to benefit from the lower rates.

Example with a supported EV charger or EV:
```
When vehicle charging starts: Set backup reserve to 100%.
When vehicle charging stops: Set backup reserve to: 20%.
```

Example without a supported EV or EV charger (replace `8 kW` as needed, based on your charging rate):
```
When home usage rises above 8 kW: Set backup reserve to 100%.
When home usage drops below 8 kW: Set backup reserve to: 20%.
```

When EV charging starts, the Powerwall backup reserve will be set to 100%, and the Powerwall will start charging from the grid. The charging rate will be around 1.8kW per Powerwall. Once EV charging is done, we can reset the backup reserve to its usual value (replace 20% with your desired backup reserve).


### Combining Time-Based Control with Self-Powered mode

Tesla offers two different modes of operation: Self-Powered (using stored energy to power your home after the sun goes down) and Time-Based Control (using stored energy to maximize savings based on time-of-use utility plans). Sometimes users want the best of both worlds, e.g. the ability to export the battery to the grid during peak times (which Time-Based Control offers), while still avoiding grid imports in off-peak times (which Self-Powered mode offers). Automations allow switching between the two modes on a schedule.

Example:
```
Every day at 4:00 PM: Set operational mode to: Time-Based Control.
Every day at 9:00 PM: Set operational mode to: Self-Powered.
```

You can include additional configuration changes here if needed, e.g. Grid Charging and Energy Exports.

### Topping off the Powerwall

Tesla doesn't provide much control over charging the Powerwall from the grid. You have to be in Time-Based Control, have Grid Charging enabled, and even then it's up to the Time-Based Control algorithm to decide whether grid charging is needed. Some Netzero users prefer full control over when the battery is charged from the grid. Automations accomplish that by setting the backup reserve to 100% (which will top off the battery) and resetting it after the battery is charged.

Example:
```
Every day at 12:00 AM: Set backup reserve to: 100%.
Every day at 6:00 AM: Set backup reserve to: 20%.
```

Note: Replace 20% with your desired backup reserve. Because of Tesla's limitations, the battery will charge at a lower rate compared to Time-Based Control charging, ~1.8kW per Powerwall instead of 5kW per Powerwall. See [Backup Mode](https://docs.netzero.energy/docs/tesla/BackupMode) for an alternate automation with faster charging.


### Taking advantage of low electricity rates

Users on a [dynamic utility rate plan](https://www.netzero.energy/docs/tariffs) may want to act during periods of low electricity prices, e.g. charge an EV or charge the Powerwall when the electricity price drops below a threshold.

Examples:

```
When electricity price is below $0.10: Start vehicle charging.
When electricity price is at or above $0.10: Stop vehicle charging.
```

```
When electricity price is below $0.10: Set backup reserve to 100%.
When electricity price is at or above $0.10: Set backup reserve to 20%.
```

Note: Replace the price thresholds and backup reserve with your desired settings.


### Notifications

The only action for these automations is a push notification or email, with no change to the system. Sometimes it's useful to get notified about the Powerwall state of charge and act on it (especially if the action cannot currently be automated). For example, plug in the EV in when the Powerwall is full, or reduce home electricity usage when the Powerwall is down to the backup reserve.

Examples:
```
When Powerwall is charged up to 100%: Send notification.
When Powerwall is discharged down to backup reserve: Send notification.
```


## Frequently Asked Questions

1. **Does the Netzero app have to be running for automations to run?**

   No, the automations run on the Netzero cloud and do not require the app to run. You can enable notifications (app notifications or email) to keep track of automation runs or failures.

2. **Why did my scheduled automation not run?**

   Check the "Past Runs" Automation tab for any failures. In rare cases, a command that Netzero successfully sends to Tesla might get lost on the way from Tesla to your Powerwall (e.g. if the gateway is
   in a bad state or updating firmware at the time). If this happens repeatedly, try resetting your gateway and contact us if the issue persists.
