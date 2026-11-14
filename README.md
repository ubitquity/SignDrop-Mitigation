# SignDrop-Mitigation
A PowerShell mitigation script for the November 2026 Windows CLFS "SignDrop" zero-day privilege escalation vulnerability. It detects vulnerable registry states, applies a temporary fix by modifying the CLFS Authentication Mode, and forces a Windows Defender signature update to block local SYSTEM escalation.
