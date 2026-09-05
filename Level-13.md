# Level 13

## Problem Decription
The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level. If you need help with this level: a hint file can be found in the home directory. Make sure to read the error messages as they are informative.

## Solution
- This challenge contained a private ssh key for logging into the next level
- Because the password to the next level is stored in `/etc/bandit_pass/bandit14` and can only be accessed by the user `bandit14`
- So using `scp` command I securely copied the private ssh key `sshkey.private` to my local machine
```bash
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
```
- Then I tried `ssh` command with option `-i` to connect to bandit14 using the private ssh key, but an error occured `unprotected private key`, because the file was too permissive
- So I changed the permissons of the file using `chmod` with option `700`, to give permission only to the owner
```bash
chmod 700 sshkey.private
```
- Then I did `ssh -i` command to login into `bandit14`
```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```
## Commands Learned
1. **`scp` command**
    - It is used to copy files between yur local machine and a remote machine using `ssh`

    ```bash
    scp [options] source destination
    ```

    - Path difference:
        - local path --> path
        - remote path --> user@host:/path 
    - Options:
        - `-r` --> Recursively copy directories
        - `-P` --> Specify SSH port
        - `-i` --> Use a specific private key for auth. 
        - `-v` --> Verbose/debug output
    
2. **`ssh` command**
    - It is used to securely connect to and control a remote computer over a network
    
    ```bash
    ssh [options] user@hostname
    ```
    ```    
    How SSH works
    Your Computer                    Remote Computer
        │                                 │
        │──── SSH connection ────────────>│
        │                                 │
        │<─── Authentication ─────────────│
        │                                 │
        │──── Commands / Data ───────────>│
    ```

    - Options: 
        - `-p` --> Specify SSH port (Default 22)
        - `-i` --> Use a specific private key
        - `-v` --> Verbose/debug output

3. **`chmod` command**
    - `chmod` means change mode
    - It is used to change the permissions of files and directories

    ```bash
    chmod [options] mode file
    ```

    - Linux permission three groups Owner, Group, and Others and each having three permissions r(read), w(write), x(execute)
    - Linux also represents permissions numerically as `---` --> 0 to `rwx` --> 7
    - With the values comming comming from r = 4, w = 2, x = 1
    - For example, `755` --> `rwx r-x --x`
    - Options:
        - `-R` --> Recursively change permissions (usually for directories)
        - `-v` --> Show a diagnostic for every file
        - `-c` --> Report only when a change is made
        - `-f` --> Suppress most error messages