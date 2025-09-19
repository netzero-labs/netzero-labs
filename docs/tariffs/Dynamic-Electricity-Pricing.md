---
layout: with_footer
---

# Netzero - Dynamic Electricity Pricing

## Introduction
[Netzero](https://www.netzero.energy) enables dynamic electricity pricing (also known as dynamic
tariffs, day-ahead pricing, or wholesale pricing). These utility plans have pricing that reflects
the variation in wholesale electricity costs due to changes in supply and demand. The prices change
frequently (as frequently as every 5 minutes) and are usually forecast for the next 24 hours.

Powerwall uses the utility rate plan to optimize its Time-Based Control. Netzero adds the
ability to automatically update dynamic tariffs (based on the published prices),
thus ensuring optimal Time-Based Control.

By shifting usage based on dynamic pricing (e.g. reducing usage during expensive peaks),
users can save on electricity costs. A Powerwall system in combination with accurate rate plans is
a great way to achieve that goal!

## Supported Plans

Netzero currently supports the following plans:
- [Agile Octopus](https://octopus.energy/smart/agile/) (Octopus Energy, UK)
- [Tibber](https://tibber.com/en) (Sweden, Norway, Germany & the Netherlands)
- [ENTSO-E](https://newtransparency.entsoe.eu/market/energyPrices) (European network covering wholesale pricing for most countries in Europe)
- [Amber Electric](https://www.amber.com.au/) (Australia)
- [ComEd Hourly Pricing](https://hourlypricing.comed.com/) (ComEd, Illinois, US)

If you are in a region with a supported provider, you will see a "Utility Rate Plan" option in the
main menu.

## Agile Octopus Configuration

If you're currently on an Agile Octopus plan, configure your region, import and export
tariff, and check the "Automatically update rate plan" checkbox. This will result in a few changes:
- Your prior tariff configuration will be overridden. In the future, the app will allow
  restoring the original plan; for now, make sure to separately store your existing rate plan if
  you created it manually and might need it in the future.
- Your new tariff configuration will reflect the current pricing schedule. You can confirm the
  pricing using the [Agile Dashboard](https://agile.octopushome.net/dashboard).
- As new tariffs are announced (usually around 4pm), the tariff configuration will be
  automatically updated. You do not need to keep the app open for that.

Note that the Tesla app's Utility Rate Plan section doesn't display dynamic tariffs properly. It might
show some incorrect dips in pricing during the day. This is just a display issue -- you can instead
look at the Buy and Sell charts, shown by scrolling down under the Grid chart. These charts are
available both in the Tesla app and Netzero, and will display correct pricing.

Note: for plans with fixed outgoing (sell) prices, the sell prices are adjusted to never exceed buy
prices. This results in better Powerwall behavior (more charging and discharging when required),
due to a limitation in Tesla's Time-Based Control algorithm.

## Tibber and Amber Electric Configuration

Tibber and Amber Electric plans can be configured by providing your API token from the provider. Follow the instructions in the app.

## ComEd Hourly Pricing

ComEd Hourly Pricing does not require any configuration, just turning on automatic updates.
[PJM day-ahead prices](https://www.gridstatus.io/graph/lmp?iso=pjm&location=COMED) will be used for
the forecast, and the [ComEd Current Hour Average](https://hourlypricing.comed.com/hp-api/#section-Current-Hour-Average-API)
will be used to update the real-time price for the current hour.

## Notes

- Tesla allows a limited number of slots for configuring tariffs, which can only be set for a
  24-hour period. As a result, slots corresponding to times that have already passed today are
  filled with tomorrow’s prices, while future slots for today will contain the correct prices.
  For example, if checking pricing at noon, prices from noon to midnight will reflect today’s prices,
  while prices from midnight to 11:59 AM will reflect tomorrow’s prices. This approach gives the
  Powerwall a broader view of future pricing, enabling better decisions for charging and discharging.

## Disabling Automatic Updates

If you wish to stop updating your dynamic tariffs, uncheck the "Automatically update rate plan"
checkbox under "Utility Rate Plan". Make sure to also configure a new fixed rate plan with the
Tesla app: **Settings > Utility Rate Plan > Change Rate Plan** (at the bottom).
