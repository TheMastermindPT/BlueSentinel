---
"Title:": Parrot HTB Edition on Oracle VM installation;
tags:
  - cyber
  - linux
  - howto
  - reference
  - guide
"Created At:": 2025-06-17
"Last Updated:": 2025-06-17
"Author:": Pedro Perez Mesquita Cunha
"Source:": "[[https://academy.hackthebox.com/module/87/section/882]]"
"Description:": A guide on how to install Parrot OS HTB;
---
# Install Parrot HTB Editon 

> [!NOTE] Remember
> - If you ever have weird VM network problems—try Bridged Adapter first.
> 
> - Do not encrypt the system on installation. It will make it a pain to resize if needed. Skip this.
> 
> - Disable the optical drive or remove the drive from where the .iso is being mounted from, in order to stop looping the installation, after your installation and shut down of the machine.
> 
> 1. `Install ZSH and ohmyzsh.`
> >1. `Install the plugins.`
> >2. `Configure ZSG.`
> >3. `Get Powerlevel10k`
>   
> - Use TMUX as multiplexer.

## How to Install `xfreerdp`

### Step-by-Step:

1. **Update your repos (always good practice):**
    
    `sudo apt update`
    
2. **Install FreeRDP client:**
    
    `sudo apt install freerdp2-x11`
    
    - This will install `xfreerdp` and its dependencies.
        
3. **Verify installation:**
    
    `xfreerdp /version`
    
    - You should see version info, e.g. `This is FreeRDP version 2.x.x`.
## Steps:

### A. Increase Virtual Disk Size in VirtualBox

```
1. **Shut down the VM completely.**  
2. In VirtualBox Manager:
    - Go to **File > Virtual Media Manager...**
    - Find your Parrot VM disk (usually `.vdi`, `.vmdk`, etc.).
    - Select it, and at the bottom, you’ll see **"Size"**.
    - **Drag the slider** or type the new size you want. Click **Apply**.
```

**Back to [[_index]]**
