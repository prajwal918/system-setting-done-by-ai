# Network Speed & DNS Error Fix (Exact-Performance Workflow)

Documenting the permanent removal of VPN-related DNS blocks and network-level stutter fixes.

---

## Objective
Restore the "DIDLER ach" Wi-Fi connection to **maximum possible speed and stability** on the Windows 11 host, including:
- removal of DNS-blocking VPN software,
- permanent registry performance tweaks,
- and fixing driver-level hardware stutters.

---

## Inputs (Applied)
1. **Network Adapter:** Realtek RTL8852BE WiFi 6 802.11ax.
2. **Current Network:** Open 2.4GHz ("DIDLER ach").
3. **Problem:** DNS_PROBE_STARTED errors and intermittent slowdowns.

---

## Non-negotiable rules (Followed)
1. **Prioritize Stability:** Do not leave VPN services running that could trigger a Kill Switch.
2. **Maximum Throughput:** Disable all Windows-side bandwidth throttling.
3. **Reproducibility:** Provide a "One-Click Fix" for the user to reset the adapter if the router acts up.

---

## Step-by-step workflow

### Step 1: Diagnose DNS Blockage
- Tested `8.8.8.8` (ping worked) vs `google.com` (DNS failed).
- Identified **Surfshark Service** was active with a **Kill Switch** blocking DNS requests.

### Step 2: Full Software Cleanup
- Force-uninstalled **Surfshark**, **Proton VPN**, and **Cloudflare WARP**.
- Removed "Optimizer" tools: **Winhance** and **Antigravity**.
- Closed **qBittorrent** to stop bandwidth "choking."

### Step 3: Hardware & Protocol Fixes
- **Disabled IPv6** to prevent conflicts on the open network.
- **Set Public DNS:** Configured `8.8.8.8` and `1.1.1.1` as primary servers.
- **Modified Registry:** 
    - `NetworkThrottlingIndex` = `0xffffffff` (Disable system-level throttling).
    - `SystemResponsiveness` = `0` (Maximize networking priority).

### Step 4: Stutter-Fix (Driver Level)
- Disabled **Large Send Offload (LSO)** on the Realtek card to fix packet-burst stutters.
- Disabled **Leisure Power Save** and **Roaming Sensitivity** to stop the Wi-Fi card from "sleeping" or "searching" in the background.

### Step 5: Final Validation & Persistence
- Created `FIX_MY_WIFI.bat` on the user's Desktop for manual resets.
- Verified DNS resolution via `Resolve-DnsName google.com` (Success).
- Verified connectivity via `ping 8.8.8.8` (0% packet loss).

---

## Produced Artifacts
- `FIX_MY_WIFI.bat` (Saved to Desktop for instant recovery).
- Updated Registry Settings (Multimedia/SystemProfile).
- Optimized Wi-Fi Adapter Advanced Properties.

---

## Commit/push Summary
1. Documented all actions in `network_fix_apr_2026.md`.
2. Staged changes for the `system-setting-done-by-ai` repository.
3. Push to GitHub for tracking.

---

## Ready-to-use command intent summary
“Restore my Wi-Fi to peak performance by removing Surfshark/Proton blocks, disabling Windows throttling, and fixing Realtek stutters. Provide a recovery script on the desktop.”
