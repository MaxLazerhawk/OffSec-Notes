# Web Enumeration

### Gobuster

```gobuster dir -u http://[URL] -w [path/to/wordlist]``` - Enumerate directories on specified port.

```gobuster dir -u http://[URL] -w [path/to/wordlist] -x.conf.config.js.sh.php``` - Enumerate directories on specified port and search for specific file extensions.

```gobuster dns -d http://[URL] -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt``` - Enumerate subdomains.

```gobuster vhost -u http://example.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt``` - Enumerate virtual hosts.

### Useful Wordlists

 Script   | Service  | Description |
|:--------|:--------|:-----------|
| smb-os-discovery.nse    | SMB (445)  | Enumerate OS, domain name,etc. |
| smb-enum-users.nse      | SMB (445)  | Used to enumerate all users on remote Windows system using SAMR enumeration and LSA bruteforcing. |
| smb-enum-shares.nse     | SMB (445)  | SMB shares. |
| nbstat.nse     | NetBIOS (137)  | NetBIOS enumeration, use -sU for UDP. |


