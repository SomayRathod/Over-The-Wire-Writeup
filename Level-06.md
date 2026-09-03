# Level 6

## Problem Description
The password for the next level is stored somewhere on the server and has all of the following properties:
- owned by user `bandit7`
- owned by group `bandit6`
- 33 bytes in size

## Solution
- The file could be located anywhere on the server
- Therefore, I used `find` command to search the entire filesystem, for a file owned by user `bandit7` and group `bandit6` and is 33 bytes in size
```bash
find / -user "bandit7" -group "bandit6" -size 33c 2>/dev/null
```

- When using `find /`, some directories may return a Permission denied error because the current user does not have permission to access them
- To hide these error messages, `2>/dev/null` is used, it redirects error messages to `/dev/null`, where the messages are discarded
- After finding the file, I used the `cat` command to display its contents and obtain the password for the next level

## Takeaways
- Linux have two output streams
    - `1` --> standard  output (`stdout`)
    - `2` --> standard error (`stderr`)
- By redirecting the error on the stream `2` to `/dev/null`, we can effectively discard the error messages, while still displaying the normal output