# OffSec-Notes
Repository created for keeping notes on various topics, vulnerabilities and tools useful in penetration testing. 

# Reconnaissance
<details>
<summary>nmap</summary>

```nmap -sT [IP]``` - Use TCP connect scan (-sT) if not root/sudo user. Only option for non sudoers.

```sudo nmap [IP] ``` -  By default nmap uses TCP SYN scan (-sS), but this should be used only from root/sudo user.

```sudo nmap -sV -O -v [URL] -p- -oN [Filename.txt]``` - Default SYN scan with enabled version detection (-sV) and OS detection (-O). Additional flags - verbose mode (-v), all ports (-p-), output to .txt file (-oN). 

```sudo nmap -A [IP]``` - Default SYN scan with enabled OS detection, version detection, script scanning, and traceroute (-A).

```sudo nmap --script http-methods [IP]``` - Default SYN scan with specific script (--script). As an example script *http-methods* (enumerates allowed HTTP methods) is used.

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
