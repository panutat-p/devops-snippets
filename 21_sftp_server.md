# SFTP Server

https://hub.docker.com/r/atmoz/sftp

https://github.com/atmoz/sftp

## Simple

```yaml
services:
  sftp:
    container_name: sftp-server
    image: atmoz/sftp:debian
    command: 'admin:1234:1001:100:'
    ports:
      - '2222:22'
    volumes:
      - type: bind
        source: sftp_files
        target: /home/admin/project
    restart: unless-stopped
```

```sh
rm ~/.ssh/known_hosts
```

```sh
sftp -P 2222 admin@localhost
```

## Provide host SSH key pair

```sh
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519
```

```yaml
services:
  sftp-server:
    container_name: sftp-server
    image: atmoz/sftp:debian
    command: 'admin:1234:1001:100:'
    ports:
      - '2222:22'
    volumes:
      - type: bind
        source: sftp_files
        target: /home/admin/project
      - type: bind
        source: ${HOME}/.ssh/id_ed25519
        target: /etc/ssh/ssh_host_ed25519_key
        read_only: true
      - type: bind
        source: ${HOME}/.ssh/id_ed25519.pub
        target: /home/admin/.ssh/keys/id_ed25519.pub
        read_only: true
    restart: unless-stopped
```

```sh
sftp -i ~/.ssh/id_ed25519 -P 2222 admin@localhost
```

```sh
sftp -P 2222 admin@localhost
```

## Volume mounting issue

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
