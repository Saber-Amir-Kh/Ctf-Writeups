# picoCTF 
## Overview

| Tables | Description |
| ------ | ----------- |
| Category | Forensics |
| Challenge Name | File types |
| Points | 100 |

## Description

This file was found among some files marked confidential but my pdf reader cannot read it, maybe yours can.

#### Hint

Remember that some file types can contain and nest other files

## Approach

```bash
┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file Flag.pdf 
Flag.pdf: shell archive text

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ mv Flag.pdf Flag.sh

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ chmod +x Flag.sh

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ ./Flag.sh 
x - created lock directory _sh00046.
x - extracting flag (text)
x - removed lock directory _sh00046.

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file flag 
flag: current ar archive

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ ar x flag

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file flag 
flag: cpio archive

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ mv flag Flag

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ cpio -i < Flag
2 blocks

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file flag 
flag: bzip2 compressed data, block size = 900k

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ mv flag flag.bz2

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ bzip2 -dv flag.bz2 
  flag.bz2: done

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file flag 
flag: gzip compressed data, was "flag", last modified: Tue Mar 15 06:50:36 2022, from Unix, original size modulo 2^32 329

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ mv flag flag.gz

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ gunzip flag.gz

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file flag 
flag: lzip compressed data, version: 1

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ mv flag flag.lz

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ lzip -d flag.lz

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file flag
flag.lz4: LZ4 compressed data (v1.4+)

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ mv flag flag.lz4

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ lz4 -dv flag.lz4 
*** LZ4 command line interface 64-bits v1.9.3, by Yann Collet ***
Decoding file flag 
flag.lz4             : decoded 283 bytes

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file flag
flag.lz4: LZ4 compressed data (v1.4+)

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ mv flag flag.lz4

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ lz4 -dv flag.lz4 
*** LZ4 command line interface 64-bits v1.9.3, by Yann Collet ***
Decoding file flag 
flag.lz4             : decoded 266 bytes

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file flag
flag: LZMA compressed data, non-streamed, size 255

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ mv flag flag.lzma

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ lzma -d flag.lzma

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file flag 
flag: lzop compressed data - version 1.040, LZO1X-1, os: Unix

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ mv flag flag.lzo

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ lzop -d flag.lzo

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file flag
flag: lzip compressed data, version: 1

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ mv flag flag.lzip

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ lzip -d flag.lzip

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file flag.lzip.out

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ mv flag.lzip.out flag.xz

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ xz -d flag.xz

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ file flag 
flag: ASCII text

┌──(kali㉿kali)-[~/Documents/pico ctf]
└─$ cat flag | xxd -r -p

```

## Flag

```
picoCTF{f1len@m3_m@n1pul@t10n_f0r_0b2cur17y_347eae65}
```