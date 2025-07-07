---
"Title:": Reflection on Cap Box(easy)
tags:
  - cyber/red
  - boxes
  - reflection
  - reference
"Created At:": 2025-06-17
"Last Updated:": 2025-06-17
"Author:": Mastermind
"Source:": "[[https://app.hackthebox.com/machines/Cap]]"
"Description:": A reflection of what ive learned in Cap Box on HTB;
"Done:": true
---


Reflecting on my experience with the "Cap" box on Hack The Box, I encountered several important lessons that deepened my understanding of practical penetration testing.

Initially, I jumped straight into enumeration using Gobuster, defaulting to web directory fuzzing out of habit. This turned out to be ineffective, as the box's initial access was not web-based. A key lesson here was realizing that automated tools aren't always the best initial approach. Slowing down to carefully examine provided artifacts or clues would have saved time and effort.

My next step was attempting to crack credentials using Metasploit, which, in retrospect, was another example of rushing to use tools rather than careful analysis. The password I needed was readily available inside a PCAP file, clearly indicating I should have paused to inspect and analyze the provided artifacts first. Diving into the packet capture with Wireshark would have immediately revealed the plaintext credentials, highlighting the value of careful manual inspection before automated brute force.

Additionally, transferring scripts onto the box was more challenging than anticipated. I initially had an empty `linpeas.sh` file due to a failed transfer, something I noticed after verifying the file size. I quickly learned to double-check transferred scripts, and how to efficiently transfer them using `scp`. Moreover, since the transferred script wasn't immediately executable, I learned the alternative of invoking scripts directly via the shell (`sh script.sh`).

Finally, there was confusion regarding the location of the root flag. Initially, I assumed the root directory (`/`) was root's home, but learned through experience that root’s home directory is actually `/root`. This misunderstanding cost some extra searching time, but solidified my understanding of Linux directory structures.

Overall, while the box itself might not have been exceptionally challenging due to available walkthroughs, the minor roadblocks—such as transfer issues, incorrect assumptions, and rushed enumeration—provided valuable real-world lessons. Moving forward, I intend to approach future boxes more deliberately, prioritize artifact analysis over brute force, and always verify file transfers carefully.

**Back to [[_index]]**