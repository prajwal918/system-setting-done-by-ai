# Wi-Fi Troubleshooting Summary

**Date:** March 29, 2026
**Device:** Lenovo LOQ 15IRX9 (Model: 83DV)
**Network Adapter:** Realtek RTL8852BE WiFi 6 802.11ax PCIe Adapter
**Serial Number:** MP2QGPVB

## Issue
The Wi-Fi connection was automatically dropping or disconnecting every ~10 minutes, despite the router functioning perfectly.

## Actions Taken by AI

1. **System Diagnosis**
   - Identified the exact Wi-Fi adapter model (Realtek RTL8852BE), which is known for aggressive power-saving, roaming behaviors, and Wi-Fi 6 compatibility issues that cause random drops.
   - Identified the specific laptop model to ensure correct driver matching.

2. **Network Adapter Power & Roaming Settings Adjusted**
   - **Roaming Sensitivity Level:** Changed from `"Middle"` to `"Disabled"`. (Stops the adapter from constantly scanning and attempting to switch to other networks).
   - **Leisure Power Save:** Changed from `"Auto"` to `"Low"`. (Prevents Windows from aggressively putting the Wi-Fi card to sleep to save power).

3. **Wireless Mode Adjusted for Stability (The "Wi-Fi 6 Fix")**
   - **5G Wireless Mode:** Changed from `"IEEE 802.11a/n/ac/ax"` (Wi-Fi 6) to `"IEEE 802.11a/n/ac"` (Wi-Fi 5).
   - **2.4G Wireless Mode:** Changed from `"IEEE 802.11b/g/n/ax"` (Wi-Fi 6) to `"IEEE 802.11b/g/n"` (Wi-Fi 4).
   *Reason:* The Realtek RTL8852BE often struggles to maintain stable connections with certain Wi-Fi 6 routers. Forcing older, more stable protocols (Wi-Fi 5/4) is a proven workaround for dropping connections when driver updates do not resolve the issue.

4. **General Network Maintenance**
   - Flushed the DNS Resolver Cache (`ipconfig /flushdns`) to clear out any outdated or corrupted network configurations.

5. **Driver Update Attempt**
   - Checked Lenovo Vantage and Lenovo Support for updates, but a newer driver was not required or available.
