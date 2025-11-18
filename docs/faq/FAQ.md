---
layout: with_footer
---

# Frequently Asked Questions

1. [How can I configure Powerwall to export to the grid?](#1-how-can-i-configure-powerwall-to-export-to-the-grid)
2. [Why is my Powerwall charging or discharging when I don't expect it to?](#2-why-is-my-powerwall-charging-or-discharging-when-i-dont-expect-it-to)
3. [Intelligent Octopus Go: Why is my Powerwall charging from the grid or discharging to the EV?](#3-intelligent-octopus-go-why-is-my-powerwall-charging-from-the-grid-or-discharging-to-the-ev)
4. [Where can I suggest features or changes for Netzero?](#4-where-can-i-suggest-features-or-changes-for-netzero)
5. [Why is my Powerwall 2 or Powerwall 3 diagnostics connection failing?](#5-why-is-my-powerwall-2-or-powerwall-3-diagnostics-connection-failing)
6. [Why is the Utility Rate Plan shown in the Tesla app wrong?](#6-why-is-the-utility-rate-plan-shown-in-the-tesla-app-wrong)
7. [How do I edit or remove an existing automation?](#7-how-do-i-edit-or-remove-an-existing-automation)
8. [Can you add support for my EV, EV charger, or heating/cooling unit?](#8-can-you-add-support-for-my-ev-ev-charger-or-heatingcooling-unit)
9. [Why does my Netzero app not work or allow me to sign in?](#9-why-does-my-netzero-app-not-work-or-allow-me-to-sign-in)
10. [How do I subscribe to Netzero for advanced features?](#10-how-do-i-subscribe-to-netzero-for-advanced-features)
11. [Which automations should I configure for my system?](#11-which-automations-should-i-configure-for-my-system)

## 1. How can I configure Powerwall to export to the grid?

Powerwall export behavior cannot be forced by Netzero. Exporting is determined entirely by Tesla's Time-Based Control algorithm. That algorithm decides whether exporting is beneficial based on your utility rate plan, predicted home usage, and predicted solar production.

Netzero can configure the relevant settings for exporting, such as:

* Enabling **Time-Based Control** mode.
* Setting **Energy Exports** to **Everything (solar and battery)**.
* Setting a **low backup reserve**.

However, these settings alone do not guarantee export. The final decision remains with Tesla.

Common reasons why Powerwall does not export:

* **Preserving capacity may be more valuable**. Powerwall often avoids exporting if holding charge for later peak prices produces greater savings. Tesla also restricts configurations so that export prices can never exceed import prices for any period.
* **Exporting may be installer-restricted**. If you do not see the Energy Exports: Everything option in the Tesla app, your installer or utility may have disabled battery export. Confirm with the installer or Tesla Support.

## 2. Why is my Powerwall charging or discharging when I don't expect it to?

Netzero cannot directly control real-time charging or discharging. It can only set configuration parameters such as the operational mode, backup reserve, and export settings. Powerwall behavior itself is decided by Tesla.

Useful Tesla references:

* [Time-Based Control User Guide](https://www.tesla.com/support/energy/powerwall/mobile-app/time-based-control-user-guide)
* [Self-Powered Mode](https://www.tesla.com/support/energy/powerwall/mobile-app/self-powered)

Common explanations for unexpected behavior:

* **Misconfigured settings**. Double-check operational mode, backup reserve, and export settings in Netzero and in the Tesla app.
* **Powerwall 3 Calibration Mode**. Powerwall 3 sometimes enters a calibration cycle that rapidly discharges and recharges the battery, even below the backup reserve. It typically completes within 24 hours. If the behavior persists, contact Tesla Support.
* **System restart needed**. If behavior remains unclear, power-cycle the system:

  * [Powerwall 3: Turning the System Off](https://energylibrary.tesla.com/docs/Public/EnergyStorage/Powerwall/3/OwnerManual/en-us/GUID-D239D3CE-AED7-41EA-88C0-13566FDF966C.html)
  * [Powerwall 2: Power Cycle Instructions](https://energylibrary.tesla.com/docs/Public/EnergyStorage/Powerwall/+/InstallManual/BackupGateway/2/en-us/GUID-F7D582A7-09D4-4231-83EB-4535B7DE1018.html)

## 3. Intelligent Octopus Go: Why is my Powerwall charging from the grid or discharging to the EV?

When the [Intelligent Octopus Go integration](https://docs.netzero.energy/docs/tariffs/Intelligent-Octopus-Go) is enabled, Netzero uses Octopus-scheduled charging windows to preserve or charge the Powerwall.

Important notes:

* Only the **Octopus API key** and **account number** are required in Netzero. EV or charger integration is optional and not used for charging windows. The utility rate plan does not need to be managed by Netzero either.
* To receive notifications when Intelligent Octopus sessions begin or end, enable email or push notifications in **Settings > Notifications**, and ensure **Automations notify only when failing** is disabled.

## 4. Where can I suggest features or changes for Netzero?

Use the public GitHub issue tracker to submit feature requests:

* [Netzero Issues](https://github.com/netzero-labs/netzero/issues)

This allows other users to discuss and upvote ideas, and helps us track them efficiently.

## 5. Why is my Powerwall 2 or Powerwall 3 diagnostics connection failing?

Troubleshooting guides are available:

* [Powerwall 3 Troubleshooting](https://docs.netzero.energy/docs/diagnostics/Powerwall3#troubleshooting)
* [Powerwall 2 Troubleshooting](https://docs.netzero.energy/docs/diagnostics/Powerwall2#troubleshooting)

## 6. Why is the Utility Rate Plan shown in the Tesla app wrong?

This is a known visual bug in the Tesla app's Utility Rate Plan screen which may show unrealistic dips in pricing. The actual price data used by Tesla and Netzero is correct and is shown accurately in the detailed price charts under the Grid chart.

The display issue does not impact Powerwall behavior or Netzero automations.

## 7. How do I edit or remove an existing automation?

Swipe left on any automation in the schedule to edit, pause, mute, or delete an automation.

## 8. Can you add support for my EV, EV charger, or heating/cooling unit?

Netzero uses an API partner to integrate energy devices. Supported manufacturer and model availability depends on programmatic access, reliability, and vendor support.

The list of supported devices is regularly updated:

* [Energy Device Integration](https://docs.netzero.energy/docs/integrations/EnodeIntegration)

## 9. Why does my Netzero app not work or allow me to sign in?

Common fixes:

* **Reinstall the app** to fix broken states or corrupted session data.
* **Grant missing Tesla permissions** by visiting:
  [https://accounts.tesla.com/account-settings/security?tab=tpty-apps](https://accounts.tesla.com/account-settings/security?tab=tpty-apps)
  Select Netzero and ensure all required permissions are enabled.

## 10. How do I subscribe to Netzero for advanced features?

Subscriptions are available only through the iOS or Android app. Even if you primarily use the web app, you must:

1. Log in on a mobile device.
2. Subscribe via the App Store or Play Store.

Ensure you are signed in to the correct store account on your phone.

## 11. Which automations should I configure for my system?

Automation choices depend on your goals and utility rate structure. See the documentation for more examples:

* [Powerwall Automation](https://docs.netzero.energy/docs/tesla/Automation)
