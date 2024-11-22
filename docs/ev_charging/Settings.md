---
layout: default
---

# Netzero - EV Charger Settings

## Introduction

[Netzero](https://www.netzero.energy) automations enable configuration changes for Powerwall systems based
on EV charging status. For example, you can configure your Powerwall to preserve charge when EV charging
starts and avoid discharging the Powerwall into the (much larger) EV battery.

Based on your EV charging setup, there are different ways for Netzero to determine charging status: there
are integrations for **Tesla Wall Connectors**, **Tesla vehicles**, and **OCPP-compatible EV chargers**
(e.g. Wallbox or Zappi). If your charging setup is not currently supported, send us an email to
feedback@netzero.energy and we'll look at adding support.

To configure your EV charger, navigate to `Settings / Vehicle Charging`. Once the charger is configured,
a new tab will show up on top of the `New Automation` screen: `EV Charging`. This tab can be used to
configure automations based on starting or stopping EV charges.

Note: in the future, we're also planning on enabling automations that automatically start or stop
EV charging, for example based on electricity pricing or solar production.

## Tesla Wall Connector

If you have a Gen 3 Tesla Wall Connector (Wi-Fi enabled Wall Connector), that's a simple and
reliable way for Netzero to determine charging status.

If necessary, add the Wall Connector to you energy system in the Tesla app by selecting the product
drop-down in the top left and selecting `Add Product`. Once the Wall Connector is successfully added
to your energy system, you should see a car garage on the main energy screen in the Tesla app.

No further setup is needed in Netzero to access the Wall Connector data. You can confirm the status
on the `Settings / Vehicle Charging` screen.

### Notes

- Wall Connector cannot be controlled remotely currently, so Netzero will not be able to start or stop
  EV charging based on this integration (once this feature is available). Look at the Tesla vehicle
  or OCPP-compatible charger integration for that.

## Tesla Vehicle

If you have Tesla vehicles, you can configure access so Netzero can track charging status. Note: Netzero will
only access charging information; it will not access location or any other vehicle data that's not related to
charging.

If necessary, add permissions so Netzero can access the data. Navigate to the `Settings / Vehicle Charging`
screen and follow the app instructions to enable the **Vehicle Information** and
**Vehicle Charging Management** permissions. Once the permissions are added and refreshed in the app,
vehicle status will show up.

### Notes

- Because Netzero does not access location information, the Tesla vehicle integration is limited
  in how reliably it can determine home charging (as opposed to charging when on the go). Fast charging
  can be determined and will be excluded from automations. However when charing at a public Level 2
  charger, your automations might trigger. We'll improve the reliability of home charging detection
  in the future.

- This integration will allow Netzero to start or stop EV charging in the future.

## OCPP-compatible EV charger

Some EV chargers are OCPP (Open Charge Point Protocol) compatible. OCPP is an application protocol
for communication between EV chargers and providers (also known as central management systems). If
you have a compatible EV charger, you can now configure Netzero as the provider, which will share
the EV chargers status and allow remote control.

Some examples of compatible chargers are Wallbox and Zappi. If you have a compatible charger, you
will see an OCPP configuration option in the charger app. Configure it with:

```
Provider: wss://ocpp.netzero.energy
Charge point ID: ABCD-1234 (replace with the value shown in the Netzero app)
```

You do not need to specify a password.

### Notes

- We've tested the Wallbox integration extensively. If you have a different brand OCPP-compatible
  EV charger, let us know at feedback@netzero.energy if you run into any issues.

- This integration will allow Netzero to start or stop EV charging in the future.

## Questions or Issues

If you have any questions or issues, please submit them via [Netzero Issues](https://github.com/netzero-labs/netzero/issues).
