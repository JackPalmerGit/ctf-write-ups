![banner](https://github.com/gnisrever/re-write-ups/assets/165166334/adb45311-d4d0-4fac-8c8c-f7ab3c94e7f2)


# file-run1 (Write-Up)

**Category:** Reverse Engineering \
**Points:** 100 \
**CTF Event:** picoCTF 2022 \
**Author:** gnisrever

---

## Challenge Description

A program has been provided to you, what happens if you try to run it on the command line? Download the program [here](https://artifacts.picoctf.net/c/219/run).

---

## Approach
In this write-up, we will reverse engineer the provided binary to uncover the flag.

### Tools Used
*Note: All tools used in this write-up are preinstalled on REMnux (https://remnux.org/).*
| Tool       | Purpose                                                                                      |
|------------|----------------------------------------------------------------------------------------------|
| Ghidra     | Software Reverse Engineering (SRE) framework developed by the National Security Agency (NSA) |

### Step-by-Step Solution

#### 1. Setup
To prepare for the challenge, we first create a new directory named `bbbbloat` using the `mkdir` command. This directory will serve as our workspace for analysis.
```bash
remnux@remnux:~/ctf/pico$ mkdir bbbbloat
```
Next, we change to the newly created directory using the `cd` command.
```bash
remnux@remnux:~/ctf/pico$ cd bbbbloat
```
With our workspace ready, we download the binary file into this directory using the `wget` command. The binary can be obtained from the provided [link](https://artifacts.picoctf.net/c/46/bbbbloat).
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
Now that we have obtained the binary, we can proceed with our initial analysis.
