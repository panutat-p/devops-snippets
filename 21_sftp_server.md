# SFTP Server

https://hub.docker.com/r/atmoz/sftp

https://github.com/atmoz/sftp

## Command

* `user:pass:user_id:group_id:user_home_directory`
* `admin:1234:::` not restrict to a specific directory
* `admin:1234:::/home/admin` restrict the user to the `/home/admin` directory and its subdirectories

## User `admin` without `chroot` with SSH private key

```sh
ssh-keygen -t ed25519 -f ~/compose/id_ed25519 < /dev/null
```

```yaml
services:
  sftp:
    image: atmoz/sftp:debian
    command: 'admin:1234:::'
    ports:
      - '2222:22'
    volumes:
      - type: volume
        source: sftp_server_data
        target: /home/admin
      - type: bind
        source: id_ed25519.pub
        target: /etc/ssh/ssh_host_ed25519_key
    restart: unless-stopped

volumes:
  sftp_server_data:
    external: true
```

```sh
ssh-keygen -R "[localhost]:2222"
```

```sh
alias dsftp='sftp -i ~/compose/id_ed25519 -P 2222 admin@localhost'
```

## Create a docker volume with a file

```sh
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519 < /dev/null
```

```sh
docker volume create ssh_key_data
```

```sh
docker run --rm -v ssh_key_data:/data -v ~/.ssh/id_ed25519:/tmp/id_ed25519 alpine:3 /bin/sh -c 'cp /tmp/id_ed25519 /data && chmod 600 /data/id_ed25519'
```

```sh
docker run -it --rm -v ssh_key_data:/data alpine:3 sh
```

## Use ssh key in the volume

🚫 limitation with Docker volumes.
* When a file is mounted from a Docker volume into a container
* the file's permissions are set to `0755` regardless of the permissions set on the file in the volume

```
sftp-server-1  | [/entrypoint] Executing sshd
sftp-server-1  | @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
sftp-server-1  | @         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
sftp-server-1  | @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
sftp-server-1  | Permissions 0755 for '/etc/ssh/ssh_host_ed25519_key' are too open.
sftp-server-1  | It is required that your private key files are NOT accessible by others.
sftp-server-1  | This private key will be ignored.
sftp-server-1  | Unable to load host key "/etc/ssh/ssh_host_ed25519_key": bad permissions
sftp-server-1  | Unable to load host key: /etc/ssh/ssh_host_ed25519_key
sftp-server-1  | Unable to load host key: /etc/ssh/ssh_host_rsa_key
```

```yaml
services:
  sftp:
    image: atmoz/sftp:debian
    command: 'admin:1234:::'
    ports:
      - '2222:22'
    volumes:
      - type: volume
        source: sftp_server_data
        target: /home/admin
      - type: volume
        source: ssh_key_data
        target: /etc/ssh/ssh_host_ed25519_key
    restart: unless-stopped

volumes:
  sftp_server_data:
    external: true
  ssh_key_data:
    external: true
```

```sh
alias sftp='sftp -i ~/.ssh/id_ed25519'
```

```sh
sftp -P 2222 admin@localhost
```

```sftp
lcd ~/project
cd ~/project
get file.txt
put file.txt
put -R *
```
