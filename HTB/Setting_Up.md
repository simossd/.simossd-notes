### Password Managers

Tools that securely store and manage your passwords in an encrypted vault, so you only need to remember one master password. They can also generate strong passwords and autofill them for you.

Example: [Proton](https://proton.me/pass)

### Logging

Logging is essential for both documentation and our protection. If third parties attack the company during our penetration test and damage occurs, we can prove that the damage did not result from our activities. For this, we can use the tools `script` and `date`. `Date` can be used to display the exact date and time of each command in our command line. With the help of `script`, every command and the subsequent result is saved in a background file. To display the date and time, we can replace the `PS1` variable in our `.bashrc` file with the following content.

## PS1
```c
PS1="\[\033[1;32m\]\342\224\200\$([[ \$(/opt/vpnbash.sh) == *\"10.\"* ]] && echo \"[\[\033[1;34m\]\$(/opt/vpnserver.sh)\[\033[1;32m\]]\342\224\200[\[\033[1;37m\]\$(/opt/vpnbash.sh)\[\033[1;32m\]]\342\224\200\")[\[\033[1;37m\]\u\[\033[01;32m\]@\[\033[01;34m\]\h\[\033[1;32m\]]\342\224\200[\[\033[1;37m\]\w\[\033[1;32m\]]\n\[\033[1;32m\]\342\224\224\342\224\200\342\224\200\342\225\274 [\[\e[01;33m\]$(date +%D-%r)\[\e[01;32m\]]\\$ \[\e[0m\]"
```

## Date
```shell
─[eu-academy-1]─[10.10.14.2]─[Cry0l1t3@htb]─[~] └──╼ [03/21/21-01:45:04 PM]$
```

To start logging with `script` (for Linux) and [Start-Transcript](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-7.1) (for Windows), we can use the following command and rename it according to our needs. It is recommended to define a certain format in advance after saving the individual logs. One option is using the format `<date>-<start time>-<name>.log`.

## Script
```shell
Cry0l1t3@htb[/htb]$ script 03-21-2021-0200pm-exploitation.log Cry0l1t3@htb[/htb]$ <ALL THE COMMANDS> 
Cry0l1t3@htb[/htb]$ exit
```

## Start-Transcript
```powershell
C:\> Start-Transcript -Path "C:\Pentesting\03-21-2021-0200pm-exploitation.log" 
Transcript started, output file is "C:\Pentesting\03-21-2021-0200pm-exploitation.log" 
C:\> ...SNIP... 
C:\> Stop-Transcript
```
*This will automatically sort our logs in the correct order, and we will no longer have to examine them manually. This also makes it more straightforward for our team members to understand what steps have been taken and when.*

### VPS Providers

A `Virtual Private Server` (`VPS`) is an isolated environment created on a physical server using virtualization technology.

[WHAT IS VPS](https://www.youtube.com/watch?v=AzoMDdmLD4w&t=15s)

### SSH Agent

**SSH Agent Basics & SSH Security**

- The **SSH Agent** runs in the background and manages your **SSH keys** (used to prove your identity when connecting to servers).
- The **ssh tool** is used to securely connect to remote servers.
- To improve security, you should **harden your SSH server configuration**.
- On **Ubuntu/Debian**, the SSH config file is located at: `/etc/ssh/sshd_config`.

## Server Side
```shell
cry0l1t3@MyVPS:~$ vim /etc/ssh/sshd_config
```

You will see many different settings that can be enabled, but the first ones we highly recommend you to change are the following:
```bash
PermitRootLogin no 
PubkeyAuthentication yes 
PasswordAuthentication no 
X11Forwarding no 
Port 4444 
AllowUsers cry0l1t3
```

In this Example We :

- **Disabled root login** via SSH.
- Changed SSH port to **4444**
- Allowed access **only for user `cry0l1t3`**
- Enabled **SSH key authentication only** (no passwords)
- After changes → **restart SSH server**
```shell
  cry0l1t3@MyVPS:~$ sudo service ssh restart
```

In order to use the SSH agent there are a few things we need to do. First, we need a highly secure SSH key. One of the most effective methods is the following:

**Clien Side**
```Shell
cry0l1t3@htb:~$ ssh-keygen -t ed25519 -f ~/.ssh/cry0l1t3 

Generating public/private ed25519 key pair. 
Enter passphrase (empty for no passphrase): **************************** 
Enter same passphrase again: **************************** 

Your identification has been saved in /home/cry0l1t3/.ssh/cry0l1t3 Your public key has been saved in /home/cry0l1t3/.ssh/cry0l1t3.pub The key fingerprint is: SHA256:5TNgGHaqFsIhfqbsFPxa2PllgV2NZdHacaxNddlA0WI cry0l1t3@htb 
The key's randomart image is: 
+--[ED25519 256]--+
|. .   o ..++o.=+*|
|oo . .o=.... oE=+|
| +oo..ooo . o.*. |
|. O..o ..+ . o . |
| = =o oS +       |
|o o.. o   o      |
| o    .          |
|                 |
|                 |
+----[SHA256]-----+
```

[SSH IN 2 Minutes](https://youtu.be/P0Fk-K2eZF8?si=3sg4Qzy9W6dspr3d)
[Learn SSH - Beginners Guide to SSH Tutorial](https://www.youtube.com/watch?v=v45p_kJV9i4&t=78s)
[How SSH Works | Keys, Encryption & Real-World Examples](https://www.youtube.com/watch?v=s-vhqtyUF4I)
[How SSH Works](https://www.youtube.com/watch?v=5JvLV2-ngCI)

### Containers vs VMs vs VPS

- **Containers**:  
    Lightweight, fast and share the host system’s kernel. They only package the app + its dependencies. Great for scalability and modern apps.
- **VMs (Virtual Machines)**:  
    Heavier, each one runs a full operating system. More isolated but slower and uses more resources.
- **VPS (Virtual Private Server)**:  
    Basically a virtual machine hosted on a remote server. You rent it from a provider and use it like your own server.

**In short:**  
Containers = lightweight & fast  
VMs = fully isolated but heavy  
VPS = rented VM on the internet

_You can look deeper into containers later and see how they compare in real-world use..._


Continue → [[Linux]] .
