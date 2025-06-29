---
"Title:": Installation of Windows 10 for target;
tags:
  - cyber
  - guide
  - howto
  - htb
  - reference
"Created At:": 2025-06-17
"Last Updated:": 2025-06-17
"Author:": Mastermind
"Source:": "[[https://academy.tcm-sec.com/courses/2527344/lectures/55597162]]"
"Description:": A setup guide for Windows 10 lab as a target machine by TCM security;
"Done:": true
---
#### **References**

- [https://git-scm.com/](https://git-scm.com/)
- [https://github.com/MalwareCube/SOC101](https://github.com/MalwareCube/SOC101)

---
#### Install GuestAdditions and remember to take snapshots.
#### **Commands**

##### **Disable real-time protection**

`Set-MpPreference -DisableRealtimeMonitoring $true`

##### **Disable the scanning of network files**

`Set-MpPreference -DisableScanningNetworkFiles $true`

##### **Disable the blocking of files at first sight**

`Set-MpPreference -DisableBlockAtFirstSeen $true`

##### **Disable Windows Defender AntiSpyware**

`reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows Defender" /v DisableAntiSpyware /t REG_DWORD /d 1 /f`  

##### **Clone the course repository**

`git clone [https://github.com/MalwareCube/SOC101.git](https://github.com/MalwareCube/SOC101.git)`

Next, extract each of the course ZIP files onto the desktop using the password below:

##### **ZIP file password**

`LCty2JmHQLB3uc9VxjeohENr`

##### **Disable Windows Defender Alternative**

Sometimes Windows Defender likes to turn itself back on. If you're having persistence issues, particularly with real-time protection, you can try the following:

Press `Win + R` to open the **Run** dialog box. Type `gpedit.msc` and press **Enter** to open the **Local Group Policy Editor**. Navigate to `Computer Configuration -> Administrative Templates -> Windows Components -> Microsoft Defender Antivirus`. Double-click on the policy named **"Turn off Microsoft Defender Antivirus"** on the right pane. Select the **Enabled** option. Click **Apply** and then **"OK."**

**Back to [[_index]]**
