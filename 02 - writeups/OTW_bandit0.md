---
"Title:": OverTheWire
tags:
  - boxes
  - reference
  - status/in-progress
  - OTW
"Created At:": 2025-06-17
"Last Updated:": 2025-06-17
"Author:": Mastermind
"Source:": "[[Select Note]]"
"Description:": Notes to myself as im doing Over The Wire Bandit Levels;
"Done:": true
---
**Back to [[_index]]**


**bandit0:** `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`

---
**bandit1:** `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

> To open the - file : `cat ./- or cat < -`
---

**bandit2:** MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
``` bash
To open a file with spaces in its name.
cat "spaces in this filename" OR 
cat spaces\ in\ this\ filename
```
---
**bandit3**: `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

---
**bandit4:** `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

```bash
# Just as in bandit1 exercise, the files do not display a file extension and the filename is under the format of -filename.

# This will display all the filetypes
Solution : file ./-file??

#Concatenate the correct file
cat ./-file07
```
---
**bandit5:** `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

```bash

# Find a file which is human-readable, exactly 1033 bytes and NOT executable

Solution: find ./ -type f ! -executable -size 1033c -exec file {} + -exec cat {} \;
```
---

**bandit6:** `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

``` bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
---

**bandit7:** `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

```bash
Solution: grep millionth data.txt
```
---
**Bandit8**: `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

```bash

# Sort file first as uniq only works with adjacent lines. 
#Then with -u print the only unique lines.

Solution: sort file.txt | uniq -u
```
---
**Bandit9:** `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

```bash
#Replace every character before === and after ===. -a treats the file as text

grep -a "====" data.txt | sed 's/.*==== //;s/ ====.*//'

```
---
**Bandit10:** `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`

```bash
#Password enconded by base64
Solution: base64 -d data.txt
```
---
**Bandit11:** `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`

```bash
# The text is using ROT13 a cypher used by Julius Cesar, therefore the characters need to be rotated again. The alphabet has 26 characters, by shifting 13 positions again we reset to its original format.

tr "A-Za-z" "N-ZA-Mn-za-m" < data.txt
```
---
**Bandit12:** `FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

```bash

# The challenge gives a file with a hexdump (ASCII text representation of binary data).

# We must reverse the hexdump, then repeatedly decompress the resulting files until we extract a plain ASCII text file containing the password.

# File extensions are misleading — use the `file` command to detect the actual file type at each step.

# Step 1: Reverse the hexdump back to binary
xxd -r data.txt > stage1

# Step 2: Identify the real file type
file stage1

# Step 3: Rename based on file type (example: if it's gzip)
mv stage1 stage1.gz

# Step 4: Decompress using the correct tool
gunzip stage1.gz  # becomes 'stage1' again

# Step 5: Repeat the process — always inspect the new file:
file stage1
# If it's still compressed, rename & decompress again

# Step 6: Once `file` reports "ASCII text", read it
cat stage_final  # this will print the password
```
---
**Bandit13:** `MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`

```bash

# A public key in home directory was present. This key is used to ssh into the bandit14 account and read a file.

Solution:
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```
---
**Bandit14:** `8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`

```bash

#Connect to port 30000 on localhost and instert password from previous level.

Solution: netcat -v localhost 30000
```
---
**Bandit15:** `kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`

```bash

#Estabilishing an SSL/TLS encryption to the server with openssl.

Solution: openssl s_client -connect 127.0.0.1:30001
```
---
**Bandit16:** 

```
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```

```bash
# CONNECTED COMMANDS
If a connection is established with an SSL server then any data received from the server is displayed and any key presses will be sent to the server. If end of
       file  is  reached  then  the  connection  will  be closed down. When used interactively (which means neither -quiet nor -ign_eof have been given), then certain
       commands are also recognized which perform special operations. These commands are a letter which must appear at the start of a line. They are listed below.

       Q   End the current SSL connection and exit.

       R   Renegotiate the SSL session (TLSv1.2 and below only).

       k   Send a key update message to the server (TLSv1.3 only)

       K   Send a key update message to the server and request one back (TLSv1.3 only)

# The previous password started with a k, which lead the output of KEYUPDATE. -quiet option needs to be run.
  
Solution : openssl s_client -quiet -connect 127.0.0.1:31790

#Check if its a valid key
openssl rsa -in bandit17.key -check 

# OpenSSH refuses to use private keys unless they're secured
Fetch the key. Store it in a .keyfile with chmod 600 permissions.
```
---
**Bandit17:** `x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`

```bash
Solution: diff password.new password.old
```
---
**bandit18:** `cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8`

```bash

# Since bandit18 login shell is deliberately disabled or invalid, SSH disconnects immediately after authentication. This prevents interactive access.

# However, SSH allows remote command execution inline, bypassing the need for a shell.

# The file `readme` (containing the password for the next level) is located in `/home/bandit18/`, but direct access from `bandit17` is blocked due to permissions.

Solution:

ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme

This works because:

- SSH authenticates normally
- Instead of trying to spawn a shell, it runs the command (`cat readme`) directly 
- The command executes in the context of `bandit18`, so it bypasses permission issues

Conclusion: 
Even without an interactive shell, SSH can be used to exe

```
---
**bandit19:** `0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO`

```bash
# Used the binary with the filepath
```

---
**bandit20:** `EeoULMCra2q0dSkYj561DX7s1CpBuOBt`

```bash

# Try to host a TCP service using ncat.
-k listens for another connection after one has been completed. 
```
---

**bandit21:** `tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q`

The cron configuration located in `/etc/cron.d/` contains the following entries:

```
/usr/bin/cronjob_bandit22.sh &> /dev/null * * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null`
```

These lines execute the script `/usr/bin/cronjob_bandit22.sh` as user `bandit22`, with both `stdout` and `stderr` redirected to `/dev/null`. This redirection suppresses all output when the script is run via cron.

However upon checking, i could manually execute the script as `bandit21`:

`bash /usr/bin/cronjob_bandit22.sh`

The following error messages were observed:

```
chmod: changing permissions of '/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv': Operation not permitted /usr/bin/cronjob_bandit22.sh: line 3: /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv: Permission denied`
```

These errors revealed the temporary file path used within the script. Although the file was owned by `bandit22`. 

Conclusion: The STDERR shouldve been in the .sh file and not in the cronjob. This allowed me to see the filepath of the file that sh would modify. From there:

`cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`

---
**bandit22:** `0Zf11ioIjMVN551jX3CmStKLYqjk54Ga`

Kind of the same as before. I was able to inspect contents of bandit23.sh in cron.d

``` bash
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytar
```


The file above specifies that it collects 2 variables, one uses the whoami provided and then mytarget uses a formula to turn something into an md5sum digest. From there it uses that hash to output a file into /tmp/hashformula

Then it was a matter of accessing that folder content and extract the passwd.

---
**bandit24:** `gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8`

Objective: Steal bandit24's password using bandit23's cronjob.

## Key Insights
- Passwords stored in `/etc/bandit_pass/<username>`.

- Cronjob `/usr/bin/cronjob_bandit24.sh` runs as bandit24 every minute.

- Cronjob executes and deletes files in `/var/spool/bandit24/foo` owned by bandit23, redirecting all output to `/dev/null`.

## Solution Steps
1. **Create Writable Directory as bandit23**:
   - Run `mktemp -d` to create `/tmp/tmp.XXXXXX`.
   - Set permissions: `chmod 777 /tmp/tmp.XXXXXX` to allow bandit24 writes.

2. **Craft Script as bandit23**:
   ```bash
   #!/bin/bash
   cat /etc/bandit_pass/bandit24 > /tmp/tmp.XXXXXX/bandit24_pass.txt
   chmod 644 /tmp/tmp.XXXXXX/bandit24_pass.txt

```

- Save as script.sh in home directory.
- Set executable: chmod +x script.sh.
- Ensure ownership: chown bandit23:bandit23 script.sh.
- Move to cronjob directory: mv script.sh /var/spool/bandit24/foo.

3. **Wait and Retrieve**:
    - Cronjob runs script within 60 seconds.
    - Read password: cat /tmp/tmp.XXXXXX/bandit24_pass.txt.

## Pitfalls

- **Permissions**: Using tee or > fails if /tmp directory lacks 777 permissions for bandit24.
- **Cronjob**: Only executes files owned by bandit23 in /var/spool/bandit24/foo.
- **Output**: Cron nullifies stdout/stderr; use file writes for verification.
- **Directory**: /var/spool/bandit24/foo must exist; create if missing with mkdir as bandit23.
  
  ---
**bandit25:** `iCi86ttT4KSNe1armKiwbQNmB3YJP3q4`

---
**bandit26:** `s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ`

After getent passwd ive observed that user bandit26 has /usr/bin/showtext associated as shell. Upon further inspection into this file content, ive stumbled upon a bash script that ends with the following lines.

```bash
#!bin/sh
export TERM=linux  
more ~/text.txt  
exit 0 
```

This points out that the shell displays the banner in text.txt via more and terminates at exit 0, killing the session quick if the window fits it all.

More chains to vi when you hit 'v' at the --More-- prompt. more is a pager that displays text little by little if the content is too large or the window too small—resized my terminal to tiny (like 10-15 lines) before ssh to force that interactive mode instead of auto-exit.

Ive attempted connection with the bandit26.sshkey from bandit25's home, window resized small: ssh -i bandit26.sshkey bandit26@localhost. This lands me in more's pager as bandit26 since the key authorizes it. Now i need a full shell or just the password. Either way since i can run vi subcommands as bandit26 ive got options:

1.
```json
From more's --More-- prompt, press 'v' to launch vi on text.txt, then in vi: :e /etc/bandit_pass/bandit26 to open and read the password file directly.
```

2.
```json
In vi after 'v': :set shell=/bin/bash and :sh to escape the editor with a complete interactive bash shell as bandit26, then cat /etc/bandit_pass/bandit26 for the goods.
```

```json
Exit vi with :q!, quit more with q, and use the password for next ssh, but remember shells reset on relogin so repeat the dance if needed.
```

`./banditdo27 cat /etc/bandit_pass/bandit27`
for the password

---
bandit27: `upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB`

``` 
# Made a tmp directory in order to clone the git repo. Specify port 2220 to ssh git clone command at localhost:PORT part of the URL
```
---
bandit28: `Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN`

> Same stuff as level above

---
##### Bandit  29: `4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7`
###### Credentials

- username: bandit29
- password: xxxxxxxxxx
```
#My intuition kicked in so i decided to check the logs. I found the output below
```

Ben Dover   674690a00a0056ab96048f7317b9ec20c057c06b

```bash

# After some investigation i see that this is the number of commit. so in order to see what changed I

git show 674690a00a0056ab96048f7317b9ec20c057c06b
```

Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
- password: `4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7`
---
bandit30: `qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL`

# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>
 
*I wonder if there is some folder with credentials done in a development branch because that was hinted in README file*

*Searching the logs and refs manually wont do me any favors like before so this time ill list the logs trough the CLI with -p which unrolls patch history and details*

`git log --all -p | grep -C 5 "password"`

![[VirtualBoxVM_MgAROtTf27.png]]

---
bandit30-31: `fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy`
`git tag`
`git show secret`

---
bandit 32: `3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K`

```bash
# create a key.txt file with the content 'May come in?'

add->commit>push

git add key.txt
git commit -m 'May I come in?'
git push origin master
```
---
