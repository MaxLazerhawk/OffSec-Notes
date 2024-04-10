# Web Enumeration

### Gobuster

```gobuster dir -u http://[URL] -w [path/to/wordlist]``` - Enumerate directories on specified port.

```gobuster dir -u http://[URL] -w [path/to/wordlist] -x.conf.config.js.sh.php``` - Enumerate directories on specified port and search for specific file extensions.

```gobuster dns -d http://[URL] -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt``` - Enumerate subdomains.

```gobuster vhost -u http://example.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt``` - Enumerate virtual hosts.

### Useful Wordlists

 Wordlist   | Description |
|:--------|:-----------|
| /usr/share/wordlists/dirbuster/directory-list-2.3-*.txt    |  |
| /usr/share/wordlists/dirbuster/directory-list-1.0.txt      |  |
| /usr/share/wordlists/dirb/big.txt                          |  |
| /usr/share/wordlists/dirb/common.txt                       |  |
| /usr/share/wordlists/dirb/small.txt                        |  |
| /usr/share/wordlists/dirb/extensions_common.txt            |  |

