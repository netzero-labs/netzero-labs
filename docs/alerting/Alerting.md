---
layout: default
---

# Netzero - Alerting

## Introduction

[Netzero](https://www.netzero.energy) will notify you when there is an issue with your solar production, Powerwall operation, or Powerwall health. The currently available alerts are:
1. Very low or no solar production in the last 24 hours.
2. Very low or no solar production for an individual solar string.
3. Powerwall capacity degradation above 30%.
4. One in a set of Powerwalls is not charging and discharging.

Note: all but the first alert require Gateway/Powerwall+ access in Diagnostics.

## Configuration

To enable alerts, you have to enable push notifications in Settings. In addition to enabling alert notifications, push notifications are required to enable the app to periodically collect the diagnostic information required for alerts. You can optionally also enable email notifications in Settings.

To improve alerting, it is also recommended to:
1. Configure Gateway/Powerwall+ access in Diagnostics. This will enable solar string and Powerwall alerts.
2. Configure your city-level location in Settings. This enables access to weather information, used to better tune solar production alerts.

## Questions or Issues

For any questions or issues, please submit them here: [Netzero Issues](https://github.com/netzero-labs/netzero/issues).
