# SMB Enumeration and Exploitation

### Handy Metasploit modules

 Module    | Service  | Description       |
| --------|:--------:|:-----------------|
| smb_login     | SMB      |    Brute-force SMB credentials. |
| smb_version   | SMB      |    Scan for SMB version.        |
| smb_enumshares| SMB      |    Enumerates SMB shares.       |

```enum4linux -a [IP] [PORT]``` - Enumerate everything about SMB on specified IP and PORT.

```smbclient //[IP]/[Share] -U [Username] -p 139/445``` - Connect to SMB share only username.

```smbclient //[IP]/[Share] -U [Username]%[Password] -p 139/445``` - Connect to SMB share when you know Username and Password.

```get 'filename.txt'``` - Used in smbclient to download file.
