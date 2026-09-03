# Level 7

## Problem Description
The password for the next level is stored in the file `data.txt` next to the word `millionth`

## Solution
- The challenge contained a file `data.txt`
- First, I tried to print the contents of `data.txt` to the terminal, but it contained a very large amount of data
- Therefore, I used `grep` command to search the word millionth
```bash
grep "millionth" data.txt
```
- The command displayed the line containing the word `millionth`, along with the password for the next level 

## Commands Learned
1. `grep`
    - Searches for text patterns inside files or input and displays the matching lines

```bash
grep [OPTIONS] PATTERN [FILE...]
```

