# Level 11

## Problem Description
The password for the next level is stored in the file `data.txt`, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

## Solution
- The challenge contained a file `data.txt`, which contained the text where all the letters were rotated by 13 positions using ROT13
- I used `tr` command to replace each letter with its corresponding letter 13 positions away
```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
- The command decoded the text and displayed the password for the next level
> ROT13 is its own reverse, meaning that applying ROT13 twice returns the original text

## Commands Learned
1. **`tr` command**
    - `tr` stands for translate, it is mainly used to replace, delete or squeeze characters from input 
    ```bash
    tr [options] set1 set2
    ```
    - Usually, `tr` reads input from the standard input, so it is commonly used with pipe(`|`)
    - Replace each character in `set1` with the corresponding character in `set2`
    - Options
        - `-d` --> delete characters (only one set required)
        - `-s` --> squeeze repeated characters (only one set required)
        - `-c` --> complements (everything except set)

