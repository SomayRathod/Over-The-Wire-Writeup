# Level 8

## Problem Description
The password for the next level is stored in the file `data.txt` and is the only line of text that occurs only once

## Solution
- The challenge contained a file `data.txt`
- It contained multiple lines, repeated multiple times, but the password for the another level was the line that occured only once
- I first used `sort` command to sort the lines, so that identical lines were placed next to each other
- Then, I used `uniq` command with `-u` option to display the lines that occured only once
```bash
sort data.txt | uniq -u
```
- This displayed the unique line containing the password for the next level

## Commands Learned
1. **`sort` command**
    - It is used to sort lines of text from a filel or standard input
    ```bash
    sort [options] [file]
    ```
    - Options
        - `-r` --> Reverse order
        - `-n` --> Numeric sort
        - `-u` --> Remove Duplicates
        - `-f` --> Ignore case
        - `-kx` --> Sort by field/column
        - `-t 'x'` --> Specify delimeter

2. **`uniq` command**
    - The `uniq` command is used to detect or remove adjacent duplicate lines from a file or input
    ```bash
    uniq [options] [input_file] [output_file]
    ```
    - Options
        - `-c` -->  Count repeated lines
        - `-d` --> Show duplicate lines
        - `-u` --> Show only non-repeated lines

## Takeaway
- `|` is called a pipe, it sends output of one command as the input to another command
- When you have to remove duplicates from anywhere in the file use `sort | uniq`
- Sort by frequency
```bash
sort file.txt | uniq -c | sort -nr
```
- `sort` sorts the contents of files, `uniq` counts the repetations and, `sort -nr` sorts numerically in reversed order (from highest to lowest)