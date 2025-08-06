---
layout: default
---

# Grid Charging Issue

As of August 5, 2025, there is an ongoing issue on Tesla's side with Grid Charging configuration.

Any attempt to change the Grid Charging setting to On or Off will fail. This affects Netzero automations
as well as manual configuration changes in both the Tesla and Netzero apps.
*Note: You may need to restart the Tesla app to see the Grid Charging value reset.*

We have notified Tesla of this issue and will share updates as we receive them.

## How This Affects Netzero

Automations that include Grid Charging actions will fail with a
**"Failed to apply configuration changes"** error. Other actions in the automation will still run successfully.

Note that Grid Charging only affects Powerwall charging in Time-Based Control mode. If you are charging
the Powerwall by increasing the backup reserve to 100%, Grid Charging does not need to be enabled —
the Powerwall will always charge up to the backup reserve if needed. This means you can avoid automation
failures by removing the Grid Charging action.

If your goal is to enable Grid Charging in Time-Based Control (which charges the Powerwall faster),
you can keep the automation as-is. Hopefully, Tesla will resolve the issue soon.

## Questions or Issues

If you have questions, comments, or issues, please contact us at [feedback@netzero.energy](mailto:feedback@netzero.energy).

**[Netzero Documentation](https://docs.netzero.energy)**
