---
layout: default
---

# Tesla Powerwall Backup Reserve Update

## Backup Reserve Changes

On July 19 2025, Tesla changed the [Powerwall backup reserve](https://www.tesla.com/support/energy/powerwall/mobile-app/backup-reserve)
settings. Values between 81% and 99% are no longer supported. Only reserves set at 80% or below,
or exactly 100%, remain valid.

This change impacts both the Tesla and Netzero apps. Any configuration set between 81% and 99% will
now automatically reset to 80%. This adjustment also affects certain Netzero automations.

## Tesla App Update

Tesla's change took effect on July 19, but it became evident starting with Tesla app version
4.47.0. As this update is rolling out gradually, you may need to manually update your Tesla app
from your device’s app store.

Tesla cites Powerwall lifespan and performance reasons for restricting higher backup reserve values.

## Impact on Netzero Automations

Netzero automations setting the backup reserve between 81% and 99% will now default to 80%.
Automations configured at 80% or below, or exactly 100%, remain unaffected.

Automations designed to preserve Powerwall charge by matching the backup reserve to the current
state of charge will also be impacted. If the Powerwall's state of charge is between 81-99%, the
reserve will adjust to 80%, potentially discharging up to 19% capacity before stabilizing.
Automations triggered at or below 80%, or at 100%, continue to function normally.

**Note:**

* You may want to update your existing automations to reflect the new allowed backup reserve range.
  Future Netzero updates will include adjustments to the backup reserve slider options; we may also
  modify existing automations to make them compliant.

* For "preserve Powerwall charge" automations, we're exploring alternative ways to make sure
  Powerwall doesn't discharge down to 80%.

* From July 19-22, automations set between 81-99% were marked as failed. Understanding this
change, we no longer flag these automations as failed, although their behavior has changed.


## Questions or Issues

If you have questions, comments, or issues, please contact us at [feedback@netzero.energy](mailto:feedback@netzero.energy).

**[Netzero Documentation](https://docs.netzero.energy)**
