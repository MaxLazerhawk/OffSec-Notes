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

https://youtu.be/DtWjUsbuMtk?si=niE9XQOKXe-Om8L0&t=802

</details>
