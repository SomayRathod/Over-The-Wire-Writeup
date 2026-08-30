# Level 10

## Problem Description
The password for the next level is stored in the file data.txt, which contains base64 encoded data

## Solution
- The challenge contained a file `data.txt` containing base64 encoded data
- I used `base64 -d` command to decode the content
```bash
base64 -d data.txt
```
- This decoded the data and displayed the password for the next level directly on the terminal

## Commands Learned
1. **`base64` command**
    - It is used to encode or decode data using base64 encoding
    ```bash
    base64 [options] [file]
    ```
    - Options
        - `-d` --> decode base64
        - `-w x` --> wrap encoded output after x characters