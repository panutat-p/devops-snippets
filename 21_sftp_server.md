# SFTP

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
        source: id_ed25519
        target: /etc/ssh/ssh_host_ed25519_key
    restart: unless-stopped

volumes:
  sftp_server_data:
    external: true
```

```sh
alias dsftp='sftp -i ~/compose/ssh_host_ed25519_key -P 2222 admin@localhost'
```

## Use ssh key in the volume

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
