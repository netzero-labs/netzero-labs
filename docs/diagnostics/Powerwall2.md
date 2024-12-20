---
layout: with_footer
---

# Netzero - Powerwall 2 Diagnostics

## Introduction

[Netzero](https://www.netzero.energy) provides access to diagnostic data for your Powerwall 2 system. This data is not available in the Tesla app. The diagnostic data includes battery capacity and degradation, and solar string production (solar production broken down by strings of solar panels).

## Credentials

Powerwall 2 diagnostics access requires the IP address and password for the Tesla Gateway or Powerwall+.

The IP address is usually pre-populated in Netzero, but if not, it should be listed with your other home network devices at your Wi-Fi access point or home router.

The default password consists of the last five characters of the Gateway password, which is printed on a label behind the Gateway or Powerwall+ cover. If you ever changed the default password, use that instead. For Tesla Gateway 1 systems, the password will be the last 5 characters of the serial number (note: see the Gateway 1 Password Reset Requirement section for recent changes). For details, see Tesla's documentation on [Connecting to Tesla Gateway and Powerwall+
](https://www.tesla.com/support/energy/powerwall/own/connecting-network).

## Access

Once you have the IP address and password, enter them in Netzero (`Monitoring > Connect`). Netzero will connect to the Gateway, collect diagnostic data, and display it in the Powerwall and Strings tabs.

## Diagnostic Data

### Powerwall Capacity

Like every lithium-ion battery, Powerwall will degrade over time and lose capacity. Netzero allows you to track the degradation over time. Refer to the [Tesla documentation](https://www.tesla.com/support/energy/powerwall/documents/documents) for warranty details on Powerwall 2.

## Troubleshooting

Accessing devices directly through your home network is not common and can run into issues. Additionally, Gateway firmware updates sometimes cause access issues.

Two of the most common types of issues when connecting to the Gateway are connectivity issues and authentication issues. Look at the error message displayed in Netzero to determine the type of issue:
- Connectivity issues will result in a `Failed to connect` error.
- Authentication issues will result in a `Failed to authenticate` error.

### Connectivity Issues

To be able to connect to the Gateway, you have to:

- Be on the same home network as the Gateway. This generally means being on the same Wi-Fi network as the Gateway. You can confirm the name of the Gateway Wi-Fi network on the `Monitoring > Powerwall` screen (scroll down to the Network section). For your phone or tablet, confirm the Wi-Fi network in `Settings > Wi-Fi.` Note: if your Gateway is hardwired with Ethernet, it will need to be accessible from your Wi-Fi network.

- Have the correct IP address of the Gateway. Netzero will generally prefill the IP address with the correct value. You can confirm the IP address using your home network router: look for a device named `Tesla Powerwall`, `LG Innotek`, or a serial number such as `1232100-10-E--CN32132...`.

- One way to confirm connectivity independent of Netzero is to open the Gateway web address in a web browser. Using the same device and Wi-Fi network used for Netzero, open a web browser and navigate to `https://192.168.1.10` (replace this IP address with your Gateway's IP address). If the page loads, you will see a security error, which you can dismiss. If the page doesn't load or keeps spinning, there's a connectivity issue and you should try the solutions below.

If you've confirmed all the steps above and are still having connection issues, try the following steps:

1. Restart your Wi-Fi access point and/or home router. Sometimes they get into a bad state and prevent connections.
2. Restart your Gateway. [Instructions for restarting](https://www.tesla.com/support/energy/powerwall/mobile-app/connecting-powerwall-wi-fi#:~:text=the%20connection%20fails%2C-,reset%20your%20Gateway,-or%20Powerwall%2B%2C%20wait). Note: only attempt Gateway restart when the grid is up.

### Authentication Issues

Authentication issues mean the Gateway is accessible, but the password is incorrect. Confirm you have the correct password:
- For Gateway 2, the default password is **the last 5 characters** of the **password** shown on the label behind the Gateway door. The label will show a QR code, part number, serial number, and a password.
- For Gateway 1, the default password is the **last 5 characters** of the **serial number** shown on the label behind the Gateway door. NOTE: Tesla recently changed requirements for this password, so if you have a Gateway 1 and cannot log in, see the section below.
- If you ever changed the password in the past, you will need to use it instead of the default password.
- If all else fails, try resetting the password. See the section above for opening the Gateway web address and follow the Forgot Password link.

#### Gateway 1 Password Reset Requirement

Starting with firmware version 24.36.2, Tesla requires stronger passwords for Gateway 1 access (note: this does not affect Gateway 2). To access Gateway 1, you need to first reset the password, using the following procedure:

1. Using your phone, scan the QR code behind the Gateway 1 door. This will connect to the Gateway 1 TEG Wi-Fi network, using the **full serial number** as the password. Note: in some cases, the letter `S` has to be prepended to the full serial number as the Wi-Fi password.
2. Once connected to the TEG Wi-Fi network, open a web browser and navigate to `https://192.168.91.1`
3. Dismiss the security warnings, tap Continue at the bottom, scroll down and tap Upgrade Later at the bottom.
4. You will see a login screen. Tap Change or Forgot Password.
5. Select Forgot Password. For the current password, type the **last 5 letters of the serial number**. For the new password, choose a stronger password consisting of at least 8 characters, with a number and symbol.
6. Toggle the switch on the side of your Powerwall. Tesla's documentation claims only one Powerwall needs to be toggled, however some users noted that **all** Powerwalls had to be toggled (so try that if the first approach doesn't work).
7. Submit the new password.
