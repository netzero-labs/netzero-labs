---
layout: default
---

# Netzero - Health Monitoring

## Introduction

[Netzero](https://www.netzero.energy) provides notifications to keep you informed about issues with your solar production, Powerwall operation, or Powerwall health. The currently available alerts include:
1. **Very low or no solar production** in the last 24 hours.
2. **Very low or no solar production** for an individual solar string of panels (group of panels connected in series).
3. **Powerwall capacity degradation** exceeding 30%.
4. **One or more Powerwalls not charging or discharging** within a set.

**Note:** Alerts 2, 3, and 4 require Gateway/Powerwall+ access enabled in the Diagnostics section.

## Configuration

To enable health monitoring, ensure that push notifications are activated in the Settings. Push notifications are necessary not only for alert notifications but also to allow the app to periodically collect the diagnostic data required for monitoring. You can also enable email notifications in the Settings.

For improved monitoring, it is recommended to:
1. **Configure Gateway/Powerwall+ access** in Diagnostics. This is necessary to activate solar string and Powerwall-specific alerts. [Learn more](https://www.netzero.energy/docs/diagnostics/powerwall2).
2. **Set your city-level location** in the Settings. This allows the app to use weather information to fine-tune solar production alerts.

## Powerwall 3

Due to changes Tesla made with Powerwall 3, diagnostics access is not as easy as for Powerwall 2. Netzero can retrieve Powerwall 3 diagnostics, but it needs to be done manually and requires access to the QR code behind the cover. [Learn more](https://www.netzero.energy/docs/diagnostics/powerwall3).

You can still enable notifications for the "Very low or no solar production" alert.


## Troubleshooting

If you get an alert notification, first confirm that solar production or Powerwall operation are affected. You can use Netzero or the Tesla app and look at the Solar and Powerwall charts. Compare the last few days of operation.

Once you confirm the issue, the first step for solar production issues is to turn the system off and on again.  For details, see Tesla's documentation: [Troubleshooting Your System](https://www.tesla.com/support/energy/solar-panels/after-installation/troubleshooting-your-system).

For Powerwall issues, make sure the side switches are on, and breakers are not open. Then follow the troubleshooting guide above. If power-cycling the system does not resolve the issue, contact your installer or Tesla support.
