# SFTP

https://hub.docker.com/r/atmoz/sftp

https://github.com/atmoz/sftp

```yaml
services:
  sftp:
    image: atmoz/sftp:debian
    command: root:1234:0
    ports:
      - '2222:22'
    volumes:
      - type: volume
        source: sftp_server
        target: /home/root
    restart: unless-stopped

volumes:
  sftp_server:
    external: true
```

```sh
sftp -P 2222 root@localhost
```

```sftp
put file.txt
```

```sftp
put -R *
```
