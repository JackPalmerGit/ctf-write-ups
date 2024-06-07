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

### Step-by-Step Solution

#### 1. Setup
To prepare for the challenge, we first create a new directory named `file-run1` using the `mkdir` command. This directory will serve as our workspace for analysis.
```bash
remnux@remnux:~/ctf/pico$ mkdir file-run1
```
Next, we change to the newly created directory using the `cd` command.
```bash
remnux@remnux:~/ctf/pico$ cd file-run1
```
With our workspace ready, we download the binary file into this directory using the `wget` command. The binary can be obtained from the provided [link](https://artifacts.picoctf.net/c/219/run).
```bash
remnux@remnux:~/ctf/pico/file-run1$ wget https://artifacts.picoctf.net/c/219/run
```
```plaintext
--2024-06-06 20:58:52--  https://artifacts.picoctf.net/c/219/run
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 18.155.216.22, 18.155.216.44, 18.155.216.49, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|18.155.216.22|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16736 (16K) [application/octet-stream]
Saving to: ‘run’

run                            100%[===================================================>]  16.34K  --.-KB/s    in 0.002s  

2024-06-06 20:58:53 (7.68 MB/s) - ‘run’ saved [16736/16736]
```
Now that we have obtained the binary, we can proceed with our initial analysis.
