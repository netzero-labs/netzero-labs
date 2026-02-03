---
layout: with_footer
---

# Updates

- **Update Aug 7, 2025 8:35 PM UTC**: The Grid Charging issue is resolved. We are monitoring it and waiting for confirmation from Tesla.

- **Update Aug 7, 2025 7:20 AM UTC**: Tesla informed us the Grid Charging change was not intentional, and they are investigating the cause.

# Grid Charging Issue

As of August 6, 2025, there is an ongoing issue on Tesla's side with **Grid Charging** configuration.

Any attempt to change the Grid Charging setting from Off to On will fail. This affects Netzero automations
as well as manual configuration changes in both the Tesla and Netzero apps.
Note: You may need to stop and restart the Tesla app to see the Grid Charging value reset.

We have notified Tesla of this issue and will share updates as we receive them.


## How This Affects Netzero

Automations that include a Grid Charging action will fail with a
**"Failed to apply configuration changes"** error. Any other actions as part of the automation
will still run successfully.

Note that Grid Charging only affects Powerwall charging in Time-Based Control mode. If you are charging
the Powerwall by increasing the backup reserve to 100%, Grid Charging does not need to be enabled —
the Powerwall will always charge up to the backup reserve if needed. This means you can avoid automation
failures by removing the Grid Charging action.

If your goal is to enable Grid Charging in Time-Based Control (which charges the Powerwall faster),
you can keep the automation as-is. Hopefully, Tesla will resolve the issue soon.

You may also consider the experimental [Backup Mode](https://www.netzero.energy/docs/backup_mode),
which charges the Powerwall at a faster rate than Self-Powered mode.
