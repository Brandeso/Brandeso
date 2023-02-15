# Useful commands, tips and tricks

> Last updated on (15 / February / 2023)

## Databases

### PostgreSQL

- Reset autoincrement pointer to N+1 using last entry on table

    ```SQL
        BEGIN;
        -- protect against concurrent inserts while you update the counter
        LOCK TABLE your_table IN EXCLUSIVE MODE;
        -- Update the sequence
        SELECT setval('your_table_id_seq', COALESCE((SELECT MAX(id)+1 FROM your_table), 1), false);
        COMMIT;    
    ```

- Mass instert with possible violations to unique keys combinations

    ```SQL
    ON CONFLICT(branch_id, date) DO NOTHING;
    ```

## Connections

### SSH

- Connect to a remote server via SSH

    ```bash
    ssh -i "amaterasu-ssh.pem" ubuntu@3.84.106.178
    ```

    _-i flag and .pem file are optionals_

- Copy files from remote server

    ```bash
    scp -r user@server:path localPath
    scp -r root@192.168.1.255:/var/log/nginx logs
    ```

    The _-r_ flag is to make a recursive call, therefore copying all the files from the indicaetd path

## Bash Commands

- Change permissions on a file

  - Linux & OSX

    ```bash
    chmod 400 'your_file'
    ```

  - Windows
    > Source: [StackOverflow](https://stackoverflow.com/a/43317244)

    1. We define the path to our .pem key (or file we want to change permissions to)

        ```bash
        $path = ".\aws-ec2-key.pem"
        ```

    2. Reset to remove explict permissions

        ```bash
        icacls.exe $path /reset
        ```

    3. Give current user explicit read-permission

        ```bash
        icacls.exe $path /GRANT:R "$($env:USERNAME):(R)"
        ```

    4. Disable inheritance and remove inherited permissions

        ```bash
        icacls.exe $path /inheritance:r
        ```
