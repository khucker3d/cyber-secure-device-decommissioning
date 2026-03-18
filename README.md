# Secure Device Decommissioning, BitLocker, Clean Reprovisioning (Windows 10 → Windows 11)
Author: Kellie Hucker  

---

## Overview
This project documents a secure, repeatable runbook for reclaiming a personally owned Windows laptop that retained legacy enterprise BitLocker encryption. Due to unknown key ownership, possible enterprise policy control, and lack of recovery access, the system could not be trusted. A full disk wipe and clean rebuild was performed to establish a trusted cybersecurity lab baseline.

### Context
This device was previously issued by a former employer and later transferred to me as personal hardware. At the time of reclaiming the system, it retained enterprise BitLocker encryption and potential management artifacts. Recovery keys and tenant access were not available, so the device was treated as untrusted. To ensure full removal of legacy controls, the rebuild process began with a clean installation of Windows 10 from trusted media, followed by an upgrade to Windows 11 Pro. The system was then re-secured using modern platform protections.

---

## Objective
- Remove all legacy enterprise controls  
- Eliminate inaccessible BitLocker encryption  
- Rebuild the system using trusted installation media  
- Re-enable platform security (TPM, Secure Boot, BitLocker)  
- Establish a clean, trusted endpoint for cybersecurity lab use  

---

## Scope
- Personally owned Windows laptop  
- BitLocker enabled from prior employer  
- Recovery key unavailable  

---

## Success Criteria
- All partitions removed and disk wiped  
- Windows 11 Pro installed from trusted media  
- TPM and Secure Boot enabled  
- BitLocker re-enabled under personal ownership  
- Device validated as a clean lab baseline  

---

## Problem Statement
- Device retained enterprise BitLocker encryption  
- Recovery key unavailable  
- System trust could not be verified  
- Standard reset options were insufficient or risky  

---

## Security Risks Identified
- Encrypted data is inaccessible but still present  
- Unknown enterprise key escrow and policies  
- Potential compliance and privacy exposure  
- Inability to verify system integrity  

---

## Actions Taken
- Verified BitLocker and TPM state  
- Confirmed recovery key could not be retrieved  
- Performed a full disk wipe, removing all partitions  
- Installed Windows 10 from trusted media  
- Upgraded to Windows 11 Pro  
- Re-enabled Secure Boot and TPM-backed encryption  
- Validated system readiness for lab use  

---

## Outcome
- 100 percent removal of legacy enterprise controls  
- Clean and trusted system baseline  
- Device ready for SIEM, VM, and malware lab environments  

---

## Skills Demonstrated
- Endpoint security and device hardening  
- Encryption management (BitLocker)  
- Secure decommissioning workflows  
- Risk-based decision making  
- OS provisioning and system validation  

---

## Preconditions
- Physical access to the device  
- BIOS or UEFI access  
- Trusted Windows installation media  
- Acceptance of full data destruction  

---

## What Not To Do
- Do not attempt BitLocker bypass techniques  
- Do not use untrusted third-party unlock tools  
- Do not rely on "Reset this PC" in uncertain ownership scenarios  
- Do not retain old partitions when establishing a trusted baseline  

---

## Key Steps (Technical Summary)
### 1. Validate BitLocker State
Validated encryption status and key ownership: `manage-bde -status`

### 2. Check for Enterprise Management
Checked whether the device was still enrolled in a domain or Azure AD: `dsregcmd /status`

### 3. Validate Platform Security Readiness
Verified TPM and Secure Boot status:
- `Get-Tpm`
- `Confirm-SecureBootUEFI`

### 4. Perform Secure Disk Wipe
Booted from trusted installation media and deleted all partitions to remove all prior OS and enterprise artifacts.

### 5. Reinstall and Harden System
- Installed Windows 10 from trusted media
- Upgraded to Windows 11 Pro
- Enabled TPM and Secure Boot in BIOS
- Applied system updates and trusted drivers

### 6. Re-enable BitLocker Under Personal Ownership
`manage-bde -on C: -usedspaceonly`

### 7. Validate Trusted Baseline
- `manage-bde -status`
- `Get-Tpm`
- `Confirm-SecureBootUEFI`

### Confirmed:
- BitLocker fully enabled
- TPM ready
- Secure Boot active

## Result
- Delivered a clean, trusted endpoint suitable for cybersecurity lab environments.
- Demonstrated strong risk-based decision-making in handling encrypted enterprise assets, along with practical experience in secure device decommissioning and system hardening.
