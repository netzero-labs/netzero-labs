---
layout: with_footer
---

# Netzero - Charge on Solar with OCPP EV Charger

## Introduction

[Netzero](https://www.netzero.energy) can control your OCPP-compatible EV charger to charge your
vehicle on excess solar energy. This is similar to Tesla's [Charge on Solar](https://www.tesla.com/support/tesla-app/charge-on-solar)
feature, but with support for any OCPP-compatible EV charger and any vehicle (Tesla's feature only works
with Tesla vehicles).


## Configuration

1. See [EV Charger Settings](https://www.netzero.energy/docs/ev_charger_settings) for how to configure
   your OCPP-compatible charger.

2. Once your EV charger is configured, you will see a new **Enable Charge on Solar** switch in the
   **Vehicle Charging** screen.

3. You can configure the minimum Powerwall state of charge before **Charge on Solar** is enabled.
   If you set this to 100%, charging will only start once the Powerwall is full. If you set
   it to 0%, charging will start the moment there is sufficient excess solar energy available.

4. Also configure the maximum EV charger output current. Consult your EV charger's configuration or
   your electrician for the correct value.


## Notes

- For **Charge on Solar** to be activated, your system has to be in Self-Powered mode, or in
  Time-Based Control mode with Powerwall at 100% state of charge. This is to avoid interfering
  with Time-Based Control prioritization.

- There needs to be at least 1680W (7A at 240V) of excess solar power available for charging to start.
  If there isn't sufficient solar power available, charging will pause and resume once there is
  more power available. For some vehicles this can cause the charging session to stop and fail to
  resume, so there is also an option to continue charging at the lowest rate when there is not enough
  solar power.

- **Charge on Solar** will only activate during daylight hours (between sunrise and sunset). If
  you plug in your vehicle outside of daylight hours, it will proceed to charge at your configured rate. If you prefer to
  only charge with **Charge on Solar**, manually stop charging after plugging in the vehicle (using the
  Netzero app). We may add an option to make this automatic, while allowing scheduled charging from
  the grid.

- Home EV chargers are not aware of the EV state of charge, so unlike Tesla's Charge on Solar, this
  feature cannot support a combined grid and solar charging slider.
