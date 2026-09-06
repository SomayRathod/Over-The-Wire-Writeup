# Level 15

## Problem Description
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

## Solution
- To connect `localhost` to port `30001` using SSL/TLS encryption, I used `ncat` command with option `--ssl`
- By submitting the password to the localhost, I got the password for the next level
```bash
echo "password_of_current_level" | ncat --ssl localhost 30001
```

## Commands Learned
1. **`ncat` command**
    - It is an improved networking utility developed as part of the Nmap project
    - It is similar to Netcat (`nc`), but provides additional features such as SSL/TLS, proxy support, connection brokering, IPv4/IPv6 control, and more flexible connection handling

    ```bash
    ncat [options] host port
    ```

    - Options
        - `nc` options
        - `--ssl` --> Use SSL/TLS
        - `--ssl-key` --> Specify SSL private key