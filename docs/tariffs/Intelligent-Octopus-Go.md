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

- Make sure you are on an Intelligent Octopus Go tariff, and have a compatible EV or charger linked with the account. Note that Ohme is not currently supported (see note below).
- In Netzero, go to **Settings > Utility Rate Plan**.
- Enter your Octopus API Key. You can copy the API key from your [Octopus account](https://octopus.energy/dashboard/new/accounts/personal-details/api-access). The key will start with **sk_live**.
- Enter your Octopus Energy Account Number. This will be shown on your bills, emails, and Octopus app. It will look like: **A-12A34A99**.
- Switch on **Automate Intelligent Octopus Go**.

## How it works

Netzero will periodically check for scheduled charging slots. Whenever a slot is scheduled outside
of the off-peak window (23:30 - 5:30), Powerwall will be configured with a 100% backup reserve. This
will result in charging the Powerwall at a rate of approximately 1.8 kW per unit (this is controlled
by Tesla and cannot be changed). Netzero will store the previously configured backup reserve, and
restore the backup reserve once the scheduled slot is complete.

## Notes

- If you have previously configured automations for smart charging slots
  (e.g. "When vehicle charging starts: Set backup reserve to 100%"), pause or remove those automations
  so they don't interfere with this integration. The integration based on Octopus API Keys will be
  more reliable.
- If a scheduled charging slot ends during the off-peak window (23:30 - 5:30), the Powerwall backup
  reserve will remain at 100% (since the lower prices persist throughout this period). The backup
  reserve will reset at 5:30, assuming there are no additional charging slots during that time.
- If the 100% backup reserve is overridden with a different value while the EV is charging
  (either manually or with another automation), Netzero will **not** restore the backup reserve to
  the previously configured value. This is to avoid overriding any manual changes.
- Ohme chargers are not currently supported, since the smart charge schedule is not accurately represented
  in the Octopus API.
