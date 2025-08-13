---
layout: with_footer
---

# Netzero - Powerwall 2 Diagnostics

## Introduction

[Netzero](https://www.netzero.energy) provides access to diagnostic data for your Powerwall 2 system. This data is not available in the Tesla app. The diagnostic data includes battery capacity and degradation, and solar string production (solar production broken down by strings of solar panels) for Tesla-branded inverters.

**Note**: [Tesla Gateway 1](https://service.tesla.com/docs/Public/Energy/Powerwall/Powerwall-2-Owners-Manual-NA-EN/GUID-9ACA2015-05B4-41A0-B8BC-1D9AD658B307.html) owners need to [configure a password](#configuring-a-password-for-tesla-gateway-1) before diagnostics can be accessed.

## Credentials

Powerwall 2 diagnostics access requires the IP address and password for the Tesla Gateway or Powerwall+.

The IP address is usually pre-populated in Netzero, but if not, it should be listed with your other home network devices at your Wi-Fi access point or home router.

The default password consists of the **last five characters** (letters or numbers) of the Gateway password, which is printed on a label behind the Gateway door or Powerwall+ cover. For Tesla Gateway 2 systems, the label will say "Password" and the full password is ten characters, of which you will only use the last five (note: this label is different from the label that contains the part number and serial number). For Tesla Gateway 1 systems, see the section below for configuring a password. For details, see Tesla's documentation on [Connecting to Tesla Gateway and Powerwall+
](https://www.tesla.com/support/energy/powerwall/own/connecting-network).

## Access

Once you have the IP address and password, enter them in Netzero (`Monitoring > Connect`). Netzero will connect to the Gateway, collect diagnostic data, and display it in the Powerwall and Strings tabs.

**Note:** on iOS, Netzero will ask for permission to connect to the Local Network. The permission needs to be granted for the connection to succeed. If you rejected the permission, you can re-enable it from your device's Settings menu: **Settings > Apps > Netzero > Local Network**.

Optionally, you may also scan the QR code behind the Gateway door. This will automatically retrieve the correct IP address and password, and can additionally get string diagnostics for all Powerwall+ inverters. However, it requires connecting to the built-in Wi-Fi network,
which means standing next to the gateway and is less reliable.

**Note:** Diagnostics access is only available from a mobile device (iPhone or Android). Due to web browser security restrictions, it is not available from the web app.

## Diagnostic Data

### Powerwall Capacity

Like all lithium-ion batteries, Powerwall loses capacity over time. Netzero allows you to track the degradation over time. Refer to the [Tesla documentation](https://www.tesla.com/support/energy/powerwall/documents/documents) for warranty details on Powerwall 2.

### String-level Data

If you have a Powerwall+, you will also get string-level data: current, voltage, and power for each string of arrays connected to your inverter. This can be useful for investigating production issues and finding issues with individual strings of solar panels.

**Note:** due to a Tesla limitation, only data for the first Powerwall+ inverter is available.

See [Diagnosing Solar Production Issues](https://www.netzero.energy/docs/diagnostics/solar_production) for help with interpreting string-level data.

## Configuring a Password for Tesla Gateway 1

To access diagnostics with a [Tesla Gateway 1](https://service.tesla.com/docs/Public/Energy/Powerwall/Powerwall-2-Owners-Manual-NA-EN/GUID-9ACA2015-05B4-41A0-B8BC-1D9AD658B307.html),
a password must be configured first. This requires installing the Tesla One app ([iOS](https://apps.apple.com/us/app/tesla-one/id1625770308), [Android](https://play.google.com/store/apps/details?id=com.tesla.teslapros)).
Download the Tesla One app and sign in as an **External Partner** using your Tesla credentials. Then tap on **More** in the bottom right and **Tesla Device Setup**.
Tap **Manually Enter** and provide the details:
- **Network name (SSID)**: This is the Wi-Fi network name for the Gateway 1. If it is not listed on a label on the gateway, you can find it in your phone Wi-Fi settings. Look for a network name starting with **TEG**.
- **Password**:
  - This is the full serial number of the Gateway 1. Important note: in some cases you must prepend *S* to the
  password. Try both with and without the *S*.
  - If the full serial number is not listed on a label on the gateway, you can find it in the Tesla app: **Settings > My Home Info**. It will start with a **T**.

Once the Tesla One app connects to the device, tap on the gateway and go to **Settings > Advanced settings > Legacy password**. Choose and store a password. This is the password you will use in
Netzero to connect to your gateway: **Monitoring > Connect**.

## Troubleshooting

Accessing devices directly through your home network is not common and can run into issues. Additionally, Gateway firmware updates sometimes cause access issues.

Two of the most common types of issues when connecting to the Gateway are connectivity issues and authentication issues. Look at the error message displayed in Netzero to determine the type of issue:
- Connectivity issues shows a `Failed to connect` error.
- Authentication issues shows a `Failed to authenticate` error.

### Connectivity Issues

To be able to connect to the Gateway, you must:

- Be on the same home network as the Gateway. This generally means being on the same Wi-Fi network as the Gateway. You can confirm the name of the Gateway Wi-Fi network on the `Monitoring > Powerwall` screen (scroll down to the Network section). For your phone or tablet, confirm the Wi-Fi network in `Settings > Wi-Fi.` **Note:** if your Gateway is hardwired with Ethernet, it will need to be accessible from your Wi-Fi network.

- Enable the **Local Network** permission (**device Settings > Apps > Netzero > Local Network**).

- Have the correct IP address of the Gateway. Netzero usually prefills the IP address with the correct value. You can confirm the IP address using your home network router: look for device names like `Tesla Powerwall`, `LG Innotek`, or a serial number such as `1232100-10-E--CN32132...`.

- One way to confirm connectivity independent of Netzero is to open the Gateway web address in a web browser. Using the same device and Wi-Fi network used for Netzero, open a web browser and navigate to `https://192.168.1.10` (replace this IP address with your Gateway's IP address). If the page loads, you will see a security error, which you can dismiss. If the page doesn't load or keeps spinning, there's a connectivity issue and you should try the solutions below.

If you've confirmed all the steps above and are still having connection issues, try the following steps:

1. Restart your Wi-Fi access point and/or home router. Sometimes these malfunction and block connections.
2. Restart your Gateway. [Instructions for restarting](https://www.tesla.com/support/energy/powerwall/mobile-app/connecting-powerwall-wi-fi#:~:text=the%20connection%20fails%2C-,reset%20your%20Gateway,-or%20Powerwall%2B%2C%20wait). **Note:** only attempt Gateway restart when the grid is up.

### Authentication Issues

Authentication issues mean the Gateway is accessible, but the password is incorrect. Confirm you have the correct password:
- For Gateway 2, the default password is **the last 5 characters** of the **password** shown on the label behind the Gateway door. The label will show a QR code, part number, serial number, and a password.
- If you ever changed the password in the past, you will need to use it instead of the default password.
