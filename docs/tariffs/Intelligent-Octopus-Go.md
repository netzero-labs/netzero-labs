---
layout: with_footer
---

# Netzero - Intelligent Octopus Go Integration

## Introduction
[Netzero](https://www.netzero.energy) integrates with the [Intelligent Octopus Go](https://octopus.energy/smart/intelligent-octopus-go/) EV tariff from Octopus Energy. By providing your Octopus API key and account number, you can configure your Powerwall to charge during smart charging slots outside the off-peak window.

This prevents discharging your Powerwall while your EV charges and maximizes use of cheaper electricity (7p / kWh), even outside the 23:30–05:30 night rate.

## Setup

- Ensure you are on an Intelligent Octopus Go tariff and have a compatible EV or charger. **Ohme chargers** are not currently supported (see note below).
- In Netzero, go to **Settings > Utility Rate Plan**.
- Enter your Octopus API key from your [Octopus account](https://octopus.energy/dashboard/new/accounts/personal-details/api-access); it starts with **sk_live**.
- Enter your Octopus Energy account number from bills, emails, or the Octopus app, e.g. **A-12A34A99**.
- Switch on **Automate Intelligent Octopus Go**.
- Optionally enable **Preserve charge instead of charging up** to keep the Powerwall's charge during a scheduled slot without charging it.

## How it works

Netzero periodically checks for scheduled charging slots. When a slot falls outside the off-peak window (23:30–05:30), it sets the Powerwall backup reserve to 100% so the battery charges. Netzero stores and restores the previous backup reserve after the slot ends.

## Notes

- If you have existing automations for smart charging slots (e.g., "When vehicle charging starts: Set backup reserve to 100%"), pause or remove them to avoid conflicts. API-based integration is more reliable.
- If a charging slot ends during the off-peak window (23:30–05:30), the backup reserve remains at 100% through the window and resets at 05:30 unless another slot is scheduled.
- If you override the 100% backup reserve while the EV charges, Netzero **will not** restore the previous reserve to avoid overriding manual changes.
- **Ohme chargers** are unsupported because the Octopus API lacks their smart charging schedule. This limitation is outside our control. Consider using [home usage automations](https://docs.netzero.energy/docs/tesla/Automation#charging-the-powerwall-while-ev-charging-intelligent-octopus-go) instead.
- The Powerwall's charging rate varies: about 5 kW per Powerwall in Time-Based Control and 1.8 kW in Self-Powered mode. Utility limits may also affect the rate.
