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
| /usr/share/wordlists/dirb/extensions_common.txt            | Useful for when fuzzing for files. |


### WPscan

```wpscan –-url http://cmnatics.playground –-enumerate t``` - Enumerate themes.

```wpscan –-url http://cmnatics.playground –-enumerate p``` - Enumerate plugins.

```wpscan –-url http://cmnatics.playground –-enumerate u``` - Enumerate users.

```wpscan –-url http://cmnatics.playground –-passwords rockyou.txt –-usernames cmnatic``` - Brute-force.

### Nikto

```nikto -h [URL] -p 80,8000,8080``` - Basic Nikto command to enumerate ports 80, 8000 and 8080.

```nikto -h [URL] -Plugin apacheuser``` - Enumeration with a specific plugin enabled. Check plugin list.

Plugin Name |	Description
|:--------|:-----------|
| apacheusers	| Attempt to enumerate Apache HTTP Authentication Users |
| cgi	| Look for CGI scripts that we may be able to exploit |
| robots |	Analyse the robots.txt file which dictates what files/folders we are able to navigate to |
| dir_traversal |	Attempt to use a directory traversal attack (i.e. LFI) to look for system files such as /etc/passwd on Linux (http://ip_address/application.php?view=../../../../../../../etc/passwd) |

```nikto -h [URL] -Display 2``` - Enumeration displaying cookies as an example. Check Display mode list.

```nikto -h [URL] -Tuning 2``` - Enumeration and trying specific vulnerabilities (Misconfiguration/default files) in this case. Check list.


