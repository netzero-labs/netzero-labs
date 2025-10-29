---
layout: with_footer
---

# Energy Device Integration

The [Netzero app](https://www.netzero.energy) integrates with a wide range of energy devices,
including EV chargers, EVs, and heating/cooling systems. These integrations enable automation,
Charge on Solar, and tracking EV charging as part of your home usage chart.

Supported devices:

1. **EV chargers**
   - Vendors: Charge Amps, ChargePoint, Easee, EO, EVBox, Garo, go-e, Heidelberg, Hypervolt, KEBA, myenergi, Ohme, Pod Point, Schneider Electric, Wallbox, Zaptec.
   - Common capabilities: charging state, charging management (Start/Stop), Charge on Solar (for supported EV chargers), and charging data in Home charts.
   - Example automations:
     1. `When vehicle charging starts: Set backup reserve to the current state of charge (preserve Powerwall charge).`
     2. `When vehicle charging stops: Set backup reserve to 20%.`
     3. `When electricity price drops below $0.10: Start vehicle charging.`
     4. `When electricity price rises to or above $0.10: Stop vehicle charging.`
   - Full details: [Charger capabilities](https://developers.enode.com/api/capabilities/charger).

2. **EVs**
   - Vendors: Audi, Cupra, Fiat, Jaguar, Land Rover, Lexus, Mercedes, MINI, Nissan, Porsche, Renault, Rivian, SEAT, Škoda, Toyota, Volkswagen, Volvo, XPENG.
   - Common capabilities: charging state, charging management (Start/Stop), and charging data in Home charts.
   - Example automations: similar as the automations listed above for EV chargers.
   - Full details: [Vehicle capabilities](https://developers.enode.com/api/capabilities/vehicle).

3. **Heating/cooling devices**
   - Vendors: ADAX, Bosch, Daikin, Ecobee, Fujitsu, Function, Honeywell TCC, Mill, Mitsubishi, Netatmo, NIBE, Panasonic, Resideo, Sensibo, Tado, Toshiba.
   - Common capabilities: set permanent hold (e.g., pre-heat or pre-cool the home) and resume schedule.
   - Example automations:
     1. `When the system goes off-grid: Set heating/cooling to OFF.`
     2. `When the system is back on grid: Follow heating/cooling unit schedule.`
     3. `When electricity price drops below $0.10: Set permanent hold (heat setpoint at 72F/22C).`
     4. `When electricity price rises to or above $0.10: Follow HVAC device schedule.`
   - Full details: [HVAC capabilities](https://developers.enode.com/api/capabilities/hvac).

**Notes:**
- A Pro subscription or active trial is required to connect and automate energy devices.
- Netzero also supports Tesla vehicles, Tesla Wall Connectors, and OCPP-compatible EV chargers. See [EV Charger Settings](https://docs.netzero.energy/docs/ev_charging/Settings) for details.

## Connecting Devices

To connect your EV or EV charger, go to **Settings > EV Charging**.
For heating/cooling devices, go to **Settings > Heating and Cooling**.

Tap **Connect**, select your device manufacturer, sign in with your system credentials, view your compatible devices, and connect them.

Once connected, you will see device status on the **EV Charging** and **Heating and Cooling** settings screens.
If your EV charger supports setting the max charge rate, a **Charge on Solar** option will appear.

You will also see new automation options to:
- Trigger actions based on EV charging status.
- Control EV charging (if supported by the charger).
- Set permanent hold/resume schedule (if supported by the heating/cooling device).

If supported, EV and charger integrations also display charging data on the Home usage chart.
