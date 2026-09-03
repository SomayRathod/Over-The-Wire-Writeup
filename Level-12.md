# Level 12

## Problem Description
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Solution
- The challenge contained a file `data.txt` which was also a hexdump
- I used `xxd` command with option `-r` to reverse the hexdump, and recover the original file
- I then analyzed the file-type with the `file` command
- I found out that it was a gzip-compressed file, so I used `gzip` command to extract the content
- After each extraction, I used `file` again to identify the next file type and then used appropriate command (`gzip`, `bzip2` or `tar`) to process it
- I repeated the process until I got the text file containing the password
```bash
xxd -r data.txt > data
file data
gzip -d file.gz
bzip2 -d file.bz2
```

## Commands Learned
1. **`xxd` command**
    - It displays a file in hexadecimal format
    - Useful when examining binary file or hidden data

    ```bash
    xxd [options] file
    ``` 
    - basic usage and output
    ```bash
    xxd file.txt
    ```
    ```txt
    00000000: 4865 6c6c 6f20 576f 726c 64         Hello World
    ```
    - Format
        - Left side --> byte offset
        - Middle --> hexadecimal bytes
        - Right side --> ASCII representation

    - Options
        - `-r` --> Reverse a hex dump back to binary 
        - `-p` --> Display output in plain hexadecimal format
        - `-l <length>` --> Display only the specified number of bytes
        - `-s <offset>` --> Start reading from a specified byte offset
        - `-c <cols>` --> Set the number of bytes displayed per line
        - `-g <bytes>` --> Group output bytes together
        - `-u` --> Use uppercase hexadecimal letters
        - `-a` --> Automatically skip repeated lines containing only zeros

2. **`gzip` command**
    - It is used to compress and decompress files using the .gz format

    ```bash
    gzip [options] file
    ```

    - Options
        - `-d` --> Decompress a file
        - `-k` --> compress/decompress but keep the original file
        - `-f` --> Force compression or decompression
        - `-l` --> Display compression information
        - `-v` --> Show detailed operation information

3. **`bzip2` command**
    - It is used to compress an decompress files using the .bz2 format
    
    ```bash
    bzip2 [options] file
    ```
    
    - Options
        - `-d` --> Decompress file
        - `-k` --> Keep the original file
        - `-t` --> Test the integrity of a compressed file
        - `-v` --> Verbose output

4. **`tar` command**
    - It is used to combine multiple files and directories into a single archive
    - It can also work with compression tools such as `gzip` and `bzip2`

    ```bash
    tar [options] archive_files
    ```

    - Options
        - `-c` --> Create an archive
        - `-x` --> Extract an archive
        - `-t` --> List archive contents
        - `-f` --> Specify archive filename
        - `-v` --> Verbose output
        - `-z` --> Use gzip compression
        - `-j` --> Use bzip2 compression
        - `-C` --> Extract into a specified directory

5. **`cp` command**
    - It means copy

    ```bash
    cp source destination
    ```

    - Options
        - `-r` --> Copy directories recursively
        - `-i` --> Ask before overwriting
        - `-v` --> Show copied files
        - `-a` --> Copy recursively while preserving attributes

6. **`mv` command**
    - It is used to move and rename the files

    ```bash
    mv file path_to_move
    mv oldname newname
    ```

    - Options
        - `-i` --> Ask before overwriting
        - `-n` --> Do not overwrite existing files
        - `-v` --> Show moved files

7. `mktemp`
    - It creates a temporary file or directory with a unique name

    ```bash
    mktemp [options]
    ```

    - Options
        - `-d` --> Create a temporary directory
        - `-p <directory>` --> Create a temporary file in specified directory
        - `--suffix` --> Add a suffix to the temporary filename

## Takeaway
- `file` command can be used to know the file type, no matter what the suffix says