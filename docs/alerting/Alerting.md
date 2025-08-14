---
layout: with_footer
---

# Netzero - Health Monitoring

## Introduction

[Netzero](https://www.netzero.energy) provides notifications about issues with your solar production, Powerwall operation, or Powerwall health. Current alerts include:
1. **Very low or no solar production** in the last 24 hours.
2. **Very low or no solar production** for an individual solar string of panels (group of panels connected in series).
3. **Powerwall capacity degradation** exceeding 30%.
4. **One or more Powerwalls not charging or discharging**.
5. **Grid outage or system off-grid**.
6. **Powerwall firmware version updated**.

**Note:** Alerts 2, 3, and 4 require Gateway/Powerwall+ access enabled in the Diagnostics section.

## Configuration

Enable push notifications in Settings so the app can send alerts and collect diagnostic data. You can also enable email notifications.

For better monitoring:
1. **Configure Gateway/Powerwall+ access** in Diagnostics to activate solar string and Powerwall-specific alerts. [Learn more](https://www.netzero.energy/docs/diagnostics/powerwall2).
2. **Set your city-level location** in Settings so the app can use weather data to fine-tune solar production alerts.

## Powerwall 3

Tesla's changes make Powerwall 3 diagnostics harder than Powerwall 2. Netzero can retrieve Powerwall 3 diagnostics manually. [Learn more](https://www.netzero.energy/docs/diagnostics/powerwall3).

## Troubleshooting

If you get an alert, confirm the issue using Netzero or the Tesla app's Solar and Powerwall charts and compare recent days.

If the issue persists, try turning the system off and on again. For details, see Tesla's documentation: [Troubleshooting Your System](https://www.tesla.com/support/energy/solar-panels/after-installation/troubleshooting-your-system).

For Powerwall issues, make sure the side switches are on and breakers are closed. Follow the troubleshooting guide above. If power cycling does not resolve the issue, contact your installer or Tesla support.
