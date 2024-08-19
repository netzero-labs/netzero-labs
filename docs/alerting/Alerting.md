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
1. **Configure Gateway/Powerwall+ access** in Diagnostics. This is necessary to activate solar string and Powerwall-specific alerts.
2. **Set your city-level location** in the Settings. This allows the app to use weather information to fine-tune solar production alerts.

## Questions or Issues

If you have any questions or encounter any issues, please submit them via [Netzero Issues](https://github.com/netzero-labs/netzero/issues).
