# Network Troubleshooting Super-Prompt

Use the following sequence of commands and checks to resolve slow download speeds on Windows systems (especially gaming laptops with Realtek adapters).

## 1. Optimize TCP Stack
Enables Windows to dynamically adjust the receive window for better throughput.
```powershell
netsh int tcp set global autotuninglevel=normal
```

## 2. Fix Adapter-Level Issues (Realtek Specific)
Disabling Receive Segment Coalescing (RSC) often resolves driver-level performance conflicts.
```powershell
Disable-NetAdapterRsc -Name "Wi-Fi"
```

## 3. Disable Network Throttling
Modifies the registry to prevent Windows from throttling non-multimedia traffic.
```powershell
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile" /v NetworkThrottlingIndex /t REG_DWORD /d 0xffffffff /f
```

## 4. Reset Connection & Profile
Flushes DNS cache and sets the network to 'Private' for fewer restrictions.
```powershell
ipconfig /flushdns
Set-NetConnectionProfile -InterfaceAlias "Wi-Fi" -NetworkCategory Private
```

## 5. Background Activity Check
Investigate if background uploads are saturating the connection:
```powershell
Get-NetAdapterStatistics -Name "Wi-Fi" | Select-Object ReceivedBytes, SentBytes
# If SentBytes is significantly higher than ReceivedBytes, check for:
# - Google Drive (GoogleDriveFS.exe)
# - Delivery Optimization (DoSvc)
# - Windows Updates
```

## 6. Physical & Hardware Tips
- **Switch to 5 GHz:** Avoid 2.4 GHz interference.
- **Toggle Bluetooth:** Disable it temporarily as it shares the 2.4 GHz band with Wi-Fi.
- **Power Management:** Ensure the OS doesn't turn off the adapter to save power.
