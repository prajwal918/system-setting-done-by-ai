# System Settings Changes & Wi-Fi Troubleshooting Summary

**Date:** March 29, 2026
**Device:** Lenovo LOQ 15IRX9 (Model: 83DV)
**Network Adapter:** Realtek RTL8852BE WiFi 6 802.11ax PCIe Adapter
**Serial Number:** MP2QGPVB

## Part 1: Wi-Fi Troubleshooting

### Issue
The Wi-Fi connection was automatically dropping or disconnecting every ~10 minutes, despite the router functioning perfectly.

### Actions Taken by AI

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

## Part 2: System Permissions & Power Enhancements

### Actions Taken by AI

1. **CLI Tool Installation & `sudo` Configuration**
   - Bypassed default PowerShell execution policies to globally install the `@kilocode/cli` npm package.
   - Verified that Windows 11 `sudo` (inline mode) was enabled.
   - Modified the installed `kilocode.cmd` and `kilocode.ps1` background scripts to permanently prepend `sudo`, forcing the command-line tool to execute with automatic inline administrator privileges every time.

2. **PowerShell 7.6.0 Upgrade**
   - Attempted to install a user-downloaded MSI file (`PowerShell-7.6.0-win-x64.msi`), but diagnosed it as severely corrupted.
   - Bypassed the corrupt file by running the official Microsoft PowerShell web installer script to successfully install a fresh copy of **PowerShell 7.6.0**.

3. **Ultimate Performance Mode Reverted**
   - ~~Unlocked and enabled Windows' hidden "Ultimate Performance" power plan (`f3d4b34f-4e2e-4390-8681-455e65cc4707`).~~ *(Reverted by user request)*
   - Switched the system back to the standard "Balanced" power plan to conserve battery and allow hardware to rest when not under heavy load. The "Ultimate Performance" plan was deleted.

4. **Global Execution Policies Removed**
   - Set the global Windows PowerShell Execution Policy to `Unrestricted` for both the Local Machine and the Current User, allowing scripts and modules to run without prompt or block.

5. **Windows Developer Mode Reverted**
   - ~~Modified the system registry (`HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\AppModelUnlock`) to permanently enable Windows Developer Mode.~~ *(Reverted by user request)*
   - Fully disabled Developer Mode in the registry, restoring standard Windows security restrictions against unverified or unsigned applications.

## Part 3: Agent Automation & Tool Checks

### Actions Taken by AI

1. **Auto-Documentation Memory Set**
   - Permanently saved a memory rule: I will now *always* automatically document system changes, settings adjustments, and tool installations to this markdown file and auto-push it to the `prajwal918/system-setting-done-by-ai` repository without needing to be asked in any future CLI sessions.

2. **GitHub Copilot Chat (VS Code) Automation**
   - Added the custom auto-documentation instruction directly into the global VS Code `settings.json` under `github.copilot.chat.customInstructions`. The Copilot extension in VS Code will now follow this rule.

3. **GitHub Copilot CLI (`gh copilot`) Automation**
   - Created a global custom instruction file (`~/.copilot/AGENTS.md`) containing the auto-documentation rule.
   - Set a permanent Windows environment variable (`COPILOT_CUSTOM_INSTRUCTIONS_DIRS`) pointing to `~/.copilot` so that the Copilot CLI will automatically load and obey this rule across all terminal sessions.

4. **Tool Verification**
   - **Kilocode (`kilo`):** Confirmed successfully installed and running properly globally.
   - **Visual Studio Code (`code`):** Confirmed already installed (v1.109.5) and accessible from the command line.
