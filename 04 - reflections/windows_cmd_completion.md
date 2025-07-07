---
"Title:": Windows CMD completion
tags:
  - cyber
  - htb/logs
  - reflection
  - reference
"Created At:": 2025-06-17
"Last Updated:": 2025-06-17
"Author:": Mastermind
Objective: CDSA Exam Cert;
Module: Introduction to Windows Command Line;
Sections: Skills assesment;
"Description:": A reflection on this module, what ive learned and what ive couldve done better.
Done: true
---
## 1. Introduction

This is today’s reflection on the exercises I completed for the Windows Command Line fundamentals module on HTB. 

---

### User4: Filtering for the Real Flag

Things got interesting with the user4 exercise. I had hundreds of folders, each with a `flag.txt` file. Most of them were empty (0 bytes)—except for one. I quickly ran a `tree /f` command and filtered the output to show only files larger than 0 bytes. That let me find the correct flag file without wasting time.

### User6: Using System Info

For user6, I used the `systeminfo` command to find the registered owner.

### User7: Chained Passwords and Module Discovery

For the user7 flag, I connected via SSH to the domain controller. The password was chained from the previous user—so to log in as user7, I needed the flag (password) from user6. I used `get-module` to check which modules were installed and running, then found a script called `Get-Flag`, which gave me the answer.

### User8: Active Directory Filtering

For user8, I filtered for the correct AD user (Rick) with:

`Get-ADUser -Filter {Surname -eq "Flag"}`

This quickly identified the user whose surname was "Flag."

### Advanced Filtering and PowerShell Challenges

The last two challenges really tested my filtering and research skills. I relied on Microsoft’s documentation to get more comfortable with PowerShell. Since I could always use PowerShell on these boxes, I used:

`tasklist | sort /R | findstr "^vm"`

This sorted tasks in reverse order and filtered for those starting with "vm," which got me the answer.

### Event Log Analysis

The final challenge was a leap in difficulty. I’m still not fully comfortable with all PowerShell cmdlets. After logging back into the domain controller shell, I eventually figured out the right command:

`(Get-WinEvent -FilterHashTable @{LogName=Security; Id=4625} -MaxEvents 15)[14].Message`

Several login attempts happened in quick succession at 7 PM. I filtered the first 15 entries, expanded the message property, and checked which user account was attempting to log in. Since PowerShell outputs arrays of objects, I had to parse the array, select the last entry, and read the message to extract the needed info.

---

## 3. Conclusion

These exercises moved from basic command line navigation to real-world filtering, AD queries, and event log analysis. The main challenge was building fluency with PowerShell and learning to process complex outputs. Overall, I’m getting faster and more confident, but I still need to drill PowerShell filtering and event log parsing until it feels natural. The biggest takeaway: dig into the docs, break the problem into steps, and don’t hesitate to use one-liners to save time.

![[4xuGNBf49W.png]]

**Back to [[_index]]**
