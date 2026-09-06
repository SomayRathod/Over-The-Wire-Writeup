# Level 14

## Problem Description
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

## Solution
- As mentioned in the previous level, the password for the current level was stored in `/etc/bandit_pass/bandit14` 
- So with `cd` and `cat` command I got the password for the current level
```bash
cd /etc/bandit_pass/
cat bandit14
```
- To get the password for the next level, I have to submit the password I just obtained to `localhost:30000`
- So I used `nc` command to connect to the `localhost` on port `30000` piped with the `echo` command to submit the password
```bash
echo "password_of_level_14" | nc localhost 30000
```

## Commands Learned
1. **`nc` command**
    - `nc` (Netcat) is a command-line networking utility used to create TCP/UDP connections, listen for connections, send/receive data, scan ports, and troubleshoot network services.
    - It is often called the **"Swiss Army knife of networking"**
    ```bash
    nc [options] host port
    ```

    - Options
        - `-l` --> Listen for incoming connections
        - `-v` --> verbose output
        - `-z` --> scan ports without sending data
        - `-u` --> Use UDP instead of TCP
        - `-w x` --> Set connection timeout after x seconds
        - `-k` --> Keep listening after disconnect
        - `-q` --> Quit after EOF

## Takeaway
- `nc` can take input from `stdin` and send it through the network connection
- `echo` can be piped into `nc` to provide data automatically instead of typing it manually.
- The pipe `|` sends the output of `echo` to the standard input of `nc`.