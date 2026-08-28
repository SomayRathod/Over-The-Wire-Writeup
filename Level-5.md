## Level 5 

### Problem Description
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

    human-readable
    1033 bytes in size
    not executable

### Solution
- The challenge contained a `inhere` directory with multiple folders and files
- I used `find` command to find the file that is human readable and 1033 bytes in size
```bash
find -type f -size 1033c
```
- This returned the file `./maybehere07/.file2`
- Since thee file was human-readable, I displayed its content using
```bash
cat ./maybehere07/.file2
```
- The output contained the password for the next level

## Commands Learned
1. `find`
```bash
find [starting-path] [conditions] [actions]
```

- **Starting path**
    - `.` --> current directory
    - `/` --> entire filesystem
    - `home/` --> inside home directory
- **Conditions**
    - Name Codintions : `-name "filename"`
    - Type Conditions : `-type`
        - `f` --> regular file
        - `d` --> directory
        - `l` --> symbolic links & more
    - Size Conditions : `-size`
        - `c` --> bytes
        - `k` ---> KiB
        - `M` --> MiB
        - `G` --> GiB
        - `+` --> greater than
        - `-` --> less than
    - Owner Conditions : 
        - `-user "username"` --> by username
        - `-uid "userID"` --> by user ID
        - `-group "groupname"` --> by groupname
        - `-gid "groupID"` --> by group ID
    - and more

## Takeaways
- To use the `find` command to search for the files based on the type and size