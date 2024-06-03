# Bbbbloat (Write-Up)

**Category:** Reverse Engineering \
**Points:** 300 \
**CTF Event:** picoCTF 2022 \
**Author:** gnisrever

---

## Challenge Description

Can you get the flag? Reverse engineer this [binary](https://artifacts.picoctf.net/c/46/bbbbloat)

---

## Approach
- **Challenge File:** bbbbloat (https://artifacts.picoctf.net/c/46/bbbbloat)

### Tools Used
*Note: All tools used in this write-up are preinstalled on REMnux (https://remnux.org/).*
| Tool       | Purpose                                                      |
|------------|--------------------------------------------------------------|
| [Tool 1]   | [Brief description of the tool and its purpose in this challenge] |
| [Tool 2]   | [Brief description of the tool and its purpose in this challenge] |
| [Tool 3]   | [Brief description of the tool and its purpose in this challenge] |

### Step-by-Step Solution

#### 1. Initial Analysis

[Describe the steps taken for static analysis. Include relevant code snippets, screenshots, or command outputs.]

```bash
remnux@remnux:~/ctf/pico$ mkdir bbbbloat
```

```bash
remnux@remnux:~/ctf/pico$ cd bbbbloat
```

```bash
remnux@remnux:~/ctf/pico/bbbbloat$ wget https://artifacts.picoctf.net/c/46/bbbbloat
```
```plaintext
--2024-06-02 20:56:58--  https://artifacts.picoctf.net/c/46/bbbbloat
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 18.155.216.44, 18.155.216.22, 18.155.216.49, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|18.155.216.44|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14472 (14K) [application/octet-stream]
Saving to: ‘bbbbloat’

bbbbloat                 100%[==================================>]  14.13K  --.-KB/s    in 0s      

2024-06-02 20:56:59 (209 MB/s) - ‘bbbbloat’ saved [14472/14472]
```

```bash
remnux@remnux:~/ctf/pico/bbbbloat$ file bbbbloat
```
```plaintext
bbbbloat: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=db1dc86836c3e0e4140eb30914db4af5bce7cb18, for GNU/Linux 3.2.0, stripped
```
```bash
remnux@remnux:~/ctf/pico/bbbbloat$ chmod -x bbbbloat
```
```bash
remnux@remnux:~/ctf/pico/bbbbloat$ ./bbbbloat
```
```plaintext
What's my favorite number?
```
```plaintext
Sorry, that's not it!
```
```bash
remnux@remnux:~/ctf/pico/bbbbloat$ strings ./bbbbloat
```
```plaintext
/lib64/ld-linux-x86-64.so.2
libc.so.6
__isoc99_scanf
__stack_chk_fail
putchar
strdup
printf
strlen
stdout
fputs
__cxa_finalize
__libc_start_main
free
GLIBC_2.7
GLIBC_2.4
GLIBC_2.2.5
_ITM_deregisterTMCloneTable
__gmon_start__
_ITM_registerTMCloneTable
u+UH
< ~XH
A:4@r%uLH
4Ff0f9b0H
3=_cf0ehH
d_be6bN
VUUUH
VUUUH
VUUUH
VUUUH
VUUUH
VUUUH
VUUUH
VUUUH
dH3<%(
[]A\A]A^A_
What's my favorite number? 
Sorry, that's not it!
:*3$"
GCC: (Ubuntu 9.4.0-1ubuntu1~20.04.1) 9.4.0
.shstrtab
.interp
.note.gnu.property
.note.gnu.build-id
.note.ABI-tag
.gnu.hash
.dynsym
.dynstr
.gnu.version
.gnu.version_r
.rela.dyn
.rela.plt
.init
.plt.got
.plt.sec
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.init_array
.fini_array
.dynamic
.data
.bss
.comment

```
