---
layout: with_footer
---

# Netzero - Diagnosing Solar Production Issues

## Introduction

[Netzero](https://www.netzero.energy) provides access to diagnostic data for your solar system, including solar estimates and solar string diagnostics. This guide will help you identify and troubleshoot issues with solar production.

## Solar Estimates

The first step in diagnosing solar production issues is understanding the expected solar production. Many factors influence solar production:

1. **System Configuration**: Array size, roof orientation (azimuth), and roof pitch.
2. **Shading**: Nearby trees, buildings, chimneys, or other obstructions.
3. **Location**: Sun positioning and average weather conditions.
4. **Time of Year**: Seasonal variations in sun position and daylight hours.
5. **Weather Conditions**: Cloud cover, rain, snow, and extreme temperatures.

### Configuring Solar Estimates in Netzero

To get accurate solar estimates in Netzero, follow these steps:

1. Configure your city-level location in **Settings > Account**.
2. Set up your solar system details (array size, roof orientation, pitch, etc.) in **Settings > Solar Estimates**.
3. Once configured, an annual solar production estimate will be generated.
4. These estimates (depicted by orange dots) will appear on daily, monthly, and yearly solar charts.

Note: Estimates are based on the [PVWatts](https://pvwatts.nrel.gov/), utilizing historical weather data.

### Comparing Estimates with Actual Production

- Compare your actual production with the solar estimates.
- Perform the comparison on a clear day to avoid the impact of clouds.
- Use a longer time frame (several days or a month) for a more reliable assessment.
- If your actual production consistently underperforms, there might be an issue.

## String Diagnostics

If your solar production is lower than expected, analyzing the string data can help diagnose potential issues.
String data is available for Powerwall+ (Powerwall 2 with a built-in inverter) and Powerwall 3 systems.

### Understanding String Data

1. Retrieve string diagnostics on a clear day around solar noon. This is to make sure panels are at their
maximum power voltage. Take note of the voltage values for each string -- this data will be used to
estimate the size of the string. The current on the other hand is a measure of insolation (amount
of solar radiation); this value will depend on the position of the sun and will be highest around noon
in the summer.

2. Look up the specifications for your solar panels, specifically the **Maximum Power Voltage** (`Vmp at NMOT`).
For example, [Tesla's 400H](https://es-media-prod.s3.amazonaws.com/media/components/panels/spec-sheets/Tesla_T400H.pdf) panels have a `Vmp` of `35.25V`.

3. Estimate the Number of Panels per String:
   - Divide the string voltage by the `Vmp` of your panel type.
   - Example: A string voltage of `220V` would suggest approximately 6 Tesla 400H panels.

4. Verify Total System Size:
   - Sum up the panel counts across all strings.
   - If the total number of panels deviates significantly from the system size, an issue may exist.

### Common String Issues

If discrepancies exist in string voltage or panel counts, the following issues may be present:

- **Disconnected String**: A string is not properly connected to the inverter.
- **Incorrect Wiring**: A string has improper connections or missing panels.
- **Oversized or Undersized String**: The string does not match the expected design.
- **MCI (Mid-Circuit Interrupter) Unit Failure**: Hardware failure affecting string communication.

Solution: If you suspect a string issue, contact your installer to inspect and rectify the problem. You can also compare the string sizes against your installation design documents, though note that installers sometimes modify the design on installation day.
