---
layout: with_footer
---

# Netzero - EV Charging Automation

## Introduction

[Netzero](https://www.netzero.energy) automations enable starting or stopping EV charging. This requires a
Tesla vehicle or OCPP-compatible EV charger. See
[EV Charger Settings](https://www.netzero.energy/docs/ev_charger_settings) for how to configure
your Tesla vehicle or charger.


## Examples

Below are some suggested automations for EV charging:

- If you are on a dynamic pricing plan, you might want to only charge the EV when grid import prices
  are low:
  ```
  When electricity price is below $0.20, start charging.
  When electricity price is at or above $0.20, stop charging.
  ```

- You might want to only start charging the EV after the Powerwall is full:
  ```
  When Powerwall is charged up to 100%: Start vehicle charging.
  ```

Charging based on a schedule is also possible, but most EV chargers and EVs already support this feature.

## Notes

- Since Tesla charges for waking up the car or issuing commands, the automations
  are limited to 10 per user in a 24 hour period. This limit is across all start and stop
  automations. Once the allotted automations are exceeded, they will fail until enough time has
  passed.

  If the vehicle is not plugged in or is otherwise unable to start or stop charging at the time the
  automation runs, the command will be skipped and will not count toward the 10-command limit.

- There are no limits for charging with an OCPP-compatible EV charger. Note that Tesla Wall
  Connector is not OCPP-compatible.

- EV charging can only start if the vehicle is plugged in and ready to be charged.
  Similarly, the vehicle has to be actively charging for a stop automation to succeed.
