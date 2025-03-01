---
layout: with_footer
---

# Netzero - Intelligent Octopus Go Integration

## Introduction
[Netzero](https://www.netzero.energy) works with the [Intelligent Octopus Go](https://octopus.energy/smart/intelligent-octopus-go/) EV tariff from
Octopus Energy. By providing your Octopus Energy API Key and Account Number, you can configure your Powerwall to automatically charge while smart
charging is scheduled outside of the off-peak window.

This prevents discharging your Powerwall while your EV is charging. It also maximizes your use of cheaper
electricity (7p / kWh), even outside of the night rate between 23:30 - 05:30.

## Setup

- Make sure you are on an Intelligent Octopus Go tariff, and have a compatible EV or charger linked with the account.
- In Netzero, go to **Settings > Utility Rate Plan**.
- Enter your Octopus API Key. You can copy the API key from your [Octopus account](). The key will start with **sk_live**.
- Enter your Octopus Energy Account Number. This will be shown on your bills, emails, or app. It will look like: **A-12A34A99**.
- Switch on **Enable Intelligent Octopus Go automation**.

## How it works

Netzero will periodically check for scheduled charging slots. Whenever a slot is scheduled outside
of the off-peak window (23:30 - 5:30), Powerwall will be configured with a 100% backup reserve. This
will result in charging the Powerwall at a rate of approximately 1.8 kW per unit. Netzero will store
the previously configured backup reserve, and restore the backup reserve once the scheduled slot is complete.

## Notes

- If the 100% backup reserve is overridden with a different value while the EV is charging
(either manually or with another automation), Netzero will **not** restore the backup reserve to
the previously configured value. This is to avoid overriding any manual changes.
