# Steganography

**SNOW** - used for recovering secret data from a text file. 

```SNOW.EXE -C -p "password" [filename]``` - Extract hidden data from text file.

**Openstego** - GUI version of SNOW and Steghide. 

### Steghide

```steghide embed -cf Cat03.jpg -ef secret.txt -p Iaginomt``` - Embed secret.txt into Cat03.jpg set password of "Iaginomt".

```steghide extract -sf [file]``` - Extract confidential file from, for example, picture .jpg file.

```stegcracker <file> [wordlist]``` - Crack password protected file. *stegseek can also be used, it is much faster.

```crunch 8 8 -p Imaginto >> bruteforce.txt``` - Create wordlist with crunch. This command creates 8 character long words consisting of characters "Imaginto" non-repeating and saves it into .txt file.

