---
layout: with_footer
---

# Netzero - Powerwall Automation

## Introduction

[Netzero](https://www.netzero.energy) automations enable configuration changes for Powerwall systems based
on time schedule (time of day, day of week) or events (e.g. Powerwall state of charge, EV charging status, electricity price, home usage, etc.).


## Common Automations

Here are some commonly configured automations, and the goals they accomplish.

### EV charging without discharging the Powerwall

When in Self-Powered mode, charging an EV might result in depleting the Powerwall. Usually that's not what users want, because the EV battery is much larger than the Powerwall. Netzero automations can prevent that, using integrations with the Tesla Wall Connector, Tesla vehicles, or OCPP-compatible EV chargers ([learn more](https://www.netzero.energy/docs/ev_charger_settings)). For other EV chargers, there are also automations based on home usage (home usage is usually measurably higher when charging an EV).

Example with Tesla Wall Connector, Tesla vehicle, or OCCP-compatible EV charger:
```
When vehicle charging starts: Set backup reserve to the current state of charge (preserve Powerwall charge).
When vehicle charging stops: Set backup reserve to: 20%.
```

Example with a different EV or EV charger:
```
When home usage rises above 8 kW: Set backup reserve to the current state of charge (preserve Powerwall charge).
When home usage drops below 8 kW: Set backup reserve to: 20%.
```

By setting the Powerwall backup reserve to its current state of charge, we prevent the battery from discharging. Once EV charging is done, we can reset the backup reserve to its usual value (replace 20% with your desired backup reserve).


### Charging the Powerwall while EV charging (Intelligent Octopus Go)

NOTE: Netzero now has a direct [Intelligent Octopus Go integration](https://www.netzero.energy/docs/intelligent_octopus_go). This section is only useful if you have an Ohme EV charger, where that integration cannot be used.

Octopus Energy consumers on the Intelligent Octopus Go tariff plan get special EV charging slots with lower rates, not otherwise reflected in the daily rates. It may make sense to charge the Powerwall in addition to the EV, to benefit from the lower rates.

Example with Tesla Wall Connector, Tesla vehicle, or OCCP-compatible EV charger:
```
When vehicle charging starts: Set backup reserve to 100%.
When vehicle charging stops: Set backup reserve to: 20%.
```

Example with a different EV charger:
```
When home usage rises above 8 kW: Set backup reserve to 100%.
When home usage drops below 8 kW: Set backup reserve to: 20%.
```

When EV charging starts, the Powerwall backup reserve will be set to 100% and the Powerwall will start charging from the grid. The charging rate will be around 1.8kW per Powerwall. Once EV charging is done, we can reset the backup reserve to its usual value (replace 20% with your desired backup reserve).


### Combining Time-Based Control with Self-Powered mode

Tesla offers two different modes of operation: Self-Powered (using stored energy to power your home after the sun goes down) and Time-Based Control (using stored energy to maximize savings based on time-of-use utility plans). Sometimes users want the best of both worlds, e.g. the ability to export the battery to the grid during peak time (which Time-Based Control offers), while still avoiding grid imports in off-peak time (which Self-Powered mode offers). Automations allow switching between the two modes on a schedule.

Example:
```
Every day at 4:00 PM: Set operational mode to: Time-Based Control.
Every day at 9:00 PM: Set operational mode to: Self-Powered.
```

You can include additional configuration changes here if needed, e.g. Grid Charging and Energy Exports.

### Topping off the Powerwall

Tesla doesn't allow much control over charging the Powerwall from the grid. You have to be in Time-Based Control, have Grid Charging enabled, and even then it's up to the Time-Based Control algorithm to decide whether grid charging is needed. Some Netzero users prefer full control over when the battery is charged from the grid. Automations accomplish that by setting the backup reserve to 100% (which will top off the battery) and resetting it after the battery is charged.

Example:
```
Every day at 12:00 AM: Set backup reserve to: 100%.
Every day at 6:00 AM: Set backup reserve to: 20%.
```

Note: Replace 20% with your desired backup reserve. Because of Tesla limitations, the battery will charge at a lower rate compared to Time-Based Control charging, ~1.8kW per Powerwall instead of 5kW per Powerwall.


### Taking advantage of low electricity rates

User on a [dynamic utility rate plan](https://www.netzero.energy/docs/tariffs) may want to act on periods of low eletricity prices, e.g. charge an EV or charge the Powerwall when electricity price drops below a threshold.

Examples:

```
When electricity price is below $0.30: Start vehicle charging.
When electricity price is at or above $0.30: Stop vehicle charging.
```

```
When electricity price is below $0.30: Set backup reserve to 100%.
When electricity price is at or above $0.30: Set backup reserve to 20%.
```

Note: Replace 20% with your desired backup reserve.


### Notifications

The only action for these automations is a push notification or email, with no change to the system. Sometimes it's useful to get notified about the Powerwall state of charge and act on it (especially if the action cannot currently be automated). For example, plug the EV in when the Powerwall is full (to make sure Charge on Solar prioritizes the Powerwall over the EV), or reduce home electricity usage when the Powerwall is down to the backup reserve.

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
