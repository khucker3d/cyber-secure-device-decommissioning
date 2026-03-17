# Secure Device Decommissioning, BitLocker, Clean Reprovisioning (Windows 10)

Author: Kellie Hucker  

---

## Context

This device was previously issued by a former employer and later transferred to me as personal hardware. 

At the time of reclaiming the system, it still retained enterprise BitLocker encryption and potential management artifacts. Since recovery keys and tenant access were not available, the device was treated as untrusted and fully re-provisioned to establish a secure baseline under personal ownership. The rebuild process began with a clean installation of Windows 10 from trusted media to ensure full removal of legacy partitions and enterprise controls. The system was then upgraded to Windows 11 Pro and re-secured using modern platform protections.

---

## Overview

This project documents a secure, repeatable runbook for reclaiming a personally owned Windows laptop that retained legacy enterprise BitLocker encryption.

The system could not be trusted due to unknown key ownership, possible enterprise policy control, and lack of recovery access. A full secure wipe and clean rebuild was performed to establish a trusted cybersecurity lab baseline.

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
- Installed Windows 11 Pro from trusted media  
- Re-enabled Secure Boot and TPM-backed encryption  
- Validated system readiness for lab use  

---

## Outcome

- 100 percent removal of legacy enterprise controls  
- Clean and trusted system baseline  
- Device ready for SIEM, VM, and malware lab environments  

---

## Skills Demonstrated

- Endpoint security  
- Encryption management  
- Secure decommissioning  
- Risk-based decision making  
- OS hardening fundamentals  

---

## Preconditions

- Physical access to the device  
- BIOS or UEFI access  
- Trusted Windows 11 installation media  
- Acceptance of full data destruction  

---

## What Not To Do

- Do not attempt BitLocker bypass techniques  
- Do not use untrusted third-party unlock tools  
- Do not rely on "Reset this PC" in uncertain ownership scenarios  
- Do not retain old partitions if establishing a trusted baseline  

---

## Key Steps (Technical Summary)

### 1. Validate BitLocker State
Validated encryption status and key ownership.
manage-bde -status

### 2. Check for Enterprise Management
Checked whether the device was still enrolled in a domain or Azure AD.
dsregcmd /status

### 3. Validate Platform Security Readiness
Verified TPM and Secure Boot status.
Get-Tpm
Confirm-SecureBootUEFI

### 4. Perform Secure Disk Wipe
Booted from trusted Windows installation media and deleted all partitions.

### 5. Reinstall and Harden System
Installed Windows 11 Pro and re-enabled TPM and Secure Boot.

### 6. Re-enable BitLocker Under Personal Ownership
manage-bde -on C: -usedspaceonly

### 7. Validate Trusted Baseline
manage-bde -status
Get-Tpm
Confirm-SecureBootUEFI
