# SignDrop (CLFS) Zero-Day Mitigation

This repository provides a temporary mitigation script for the "SignDrop" zero-day vulnerability disclosed by Nightmare Eclipse in November 2026. 

The vulnerability allows local users to escalate to `SYSTEM` privileges by abusing the interaction between the Common Log File System (CLFS) and Windows Defender's `ServerMpUpdateEngineSignature` function. The exploit relies on the CLFS `Authentication Mode` registry key being set to `0` (learning mode) or `1` (enforcement mode).

**Note:** As of November 2026, Microsoft has not yet issued an official CVE or patch, but reports that fully updated Windows Defender signatures will block known exploitation attempts.

## Affected Systems
* Windows 11 26H2
* Windows 11 26H2 Experimental
* Windows Server 2025 Experimental

## What the Script Does
1. Checks the `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\CLFS\Authentication` path.
2. Reads the `Mode` value. If it is `0` or `1`, the system is vulnerable.
3. Sets the `Mode` value to `2` to break the exploit chain.
4. Forces a Windows Defender signature update using `Update-MpSignature`.

## Usage

1. Open PowerShell as Administrator.
2. Clone this repository or download the `Mitigate-SignDrop.ps1` file.
3. Execute the script:
   ```powershell
   .\Mitigate-SignDrop.ps1
