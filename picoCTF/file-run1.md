
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

First, we will use the command `ls -l`. The `ls -l` command lists files and directories in the current directory in long format, providing detailed information about each item.

Details of each field:
- **File permissions** (`-rw-r--r--`): Indicates file type and permissions.
- **Number of links** (`1`): Number of hard links.
- **Owner** (`user`): Username of the file's owner.
- **Group** (`group`): Group to which the file belongs.
- **File size** (`1234`): Size in bytes.
- **Modification date and time** (`Jun 7 12:34`): Last modification date and time.
- **Filename** (`filename.txt`): Name of the file or directory.

```bash
remnux@remnux:~/ctf/pico/file-run1$ ls -l
```
```plaintext
-rw-rw-r-- 1 remnux remnux 16736 Mar 15  2023 run
```

The string `-rw-rw-r--` represents the file permissions in a Unix-based operating system. Let's break down what each character in this string means:

1. **File type**: The first character indicates the type of file:
   - `-` indicates a regular file.
   - `d` would indicate a directory.
   - `l` would indicate a symbolic link.
   - There are other possible characters for special file types, such as `b` for block device, `c` for character device, etc.

2. **User (owner) permissions**: The next three characters (`rw-`) indicate the permissions for the file's owner:
   - `r` means read permission.
   - `w` means write permission.
   - `-` means no execute permission.

3. **Group permissions**: The following three characters (`rw-`) indicate the permissions for the group that owns the file:
   - `r` means read permission.
   - `w` means write permission.
   - `-` means no execute permission.

4. **Others (world) permissions**: The final three characters (`r--`) indicate the permissions for all other users:
   - `r` means read permission.
   - `-` means no write permission.
   - `-` means no execute permission.

### Summary

`-rw-rw-r--` indicates that this is a regular file where:
- The **owner** has read and write permissions.
- The **group** has read and write permissions.
- All **other users** have read-only permissions.
  
Since we don't have execute permission, we need to change its mode to make it an executable. This can be accomplished using the `chmod` command with the `+x` flag.
```bash
remnux@remnux:~/ctf/pico/file-run1$ chmod +x run
```
This allows us to directly execute the program by adding `./` in front of the executable, specifying that we want to run the file located in our current directory.
```bash
remnux@remnux:~/ctf/pico/file-run1$ ./run
```
```plaintext
The flag is: picoCTF{U51N6_Y0Ur_F1r57_F113_e5559d46}
```
We have found our flag! This challenge was super easy and a good introduction to permissions.
