# Level 9

## Problem Description
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

## Solution
- The challenge contained a file `data.txt`
- First I tried to print the contents of `data.txt` with `cat` command, but it was not redeable
- Since the file contained non-printable data, I used the `strings` command to extract the readable strings from the file
- As the password was precedded by `=`, I used `grep "="` to search for the lines with `=` 
```bash
strings data.txt | grep "="
```
- This displayed the readable strigns on the terminal containing `=`, including the password for the next level

## Takeaway
- `cat` may not be useful when a file conatins binary or non-printable data
- `strings` command can be used too extract human-readable text from such files