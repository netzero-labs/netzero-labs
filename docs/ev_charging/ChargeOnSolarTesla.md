---
layout: with_footer
---

# Netzero - Charge on Solar with Powerwall Priority

## Introduction

[Netzero](https://www.netzero.energy) enhances Tesla’s
[Charge on Solar](https://www.tesla.com/support/tesla-app/charge-on-solar)
feature by allowing you to prioritize Powerwall charging before your Tesla vehicle is charged from
excess solar energy.

In Self-Powered mode, Tesla’s Charge on Solar will only begin charging the Powerwall after the
vehicle has reached its charging limit. There is no native way to prioritize the Powerwall.
Netzero resolves this by automatically pausing Charge on Solar when vehicle charging begins,
waiting until the Powerwall reaches a user-defined state of charge, and then resuming
Charge on Solar afterward.

## Configuration

1. First, pair the Tesla vehicles you want to control using Charge on Solar.
   See [EV Charger Settings](https://www.netzero.energy/docs/ev_charger_settings) for instructions
   on pairing your Tesla vehicle with Netzero.

2. Once your Tesla vehicle is paired, you will see a new **Charge on Solar - Powerwall Priority**
   section under **Vehicle Charging**.

3. Enable the **Prioritize Powerwall charging** option and set the minimum Powerwall state of
   charge that must be reached before vehicle charging begins.

## Notes

- If the Powerwall is already at or above the configured state of charge when Charge on Solar
  activates, the automation will not run.

- If the Powerwall never reaches the configured state of charge, Charge on Solar will not be
  resumed. If your vehicle remains plugged in, it may resume charging the following day after the
  Powerwall is sufficiently charged.

- If the vehicle is below the “any source” charging threshold and not charging from excess solar,
  this automation will have no effect.
