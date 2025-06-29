---
"Title:": VM Networking Setup
tags:
  - cyber
  - reference
  - guide
  - howto
"Created At:": 2025-06-28T00:00:00
"Last Updated:": 2025-06-28T00:00:00
"Author:": Mastermind
"Source:": "[[Select Note]]"
"Description:": A guide on how to setup your own VM Network;
"Done:": true
---
---
# **Oracle VM VirtualBox: Isolating Lab Networks**

###### **Goal:** Keep lab machines talking to each other, but not to your host or the outside world.
---

1. Go to **Oracle VM > Tools**
![[VirtualBox_v9Lo48952c.png]]

2. **Select your VM, then click **Network**:**
---
![[9faELNn9WI 1.png]]
3. **Set up a NatNetwork for the lab VMs:**
---

![[VirtualBox_EZlETixUEf.png]]

- **Windows blocks ICMP** by default (unless firewall allows it).
    - Symptom: You can ping _from_ Windows to Linux, but not the other way around.
        
- **Fix:** When troubleshooting, _always_ ping **from Windows to Linux** first. Unless firewall allows it.
    - **Commands:**
        - `ipconfig` (Windows) — find your Windows IP
        - `ifconfig` (Linux) — find your Linux IP
        - `ping [linux_ip]` (from Windows)

 **In order to set Windows 10 as a target lab:**
  - Disable Defender & all protection modules, or they’ll block your attacks/malware samples.

> [!todo]-  **Commands**
> 
> **Disable real-time protection**
>- `Set-MpPreference -DisableRealtimeMonitoring $true`
>
> **Disable the scanning of network files**
>- `Set-MpPreference -DisableScanningNetworkFiles $true`
>
>**Disable the blocking of files at first sight**
>- `Set-MpPreference -DisableBlockAtFirstSeen $true`
>
>**Disable Windows Defender AntiSpyware**
>
>- `reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows Defender" /v DisableAntiSpyware /t REG_DWORD /d 1 /f`
   

---

**Back to [[_index]]**
