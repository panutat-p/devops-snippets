# SFTP Go

https://hub.docker.com/r/drakkan/sftpgo

https://github.com/drakkan/sftpgo

https://github.com/drakkan/sftpgo/blob/main/docs/howto/getting-started.md

```yaml
services:
  sftp:
    image: drakkan/sftpgo:v2
    ports:
      - '2022:2022'
      - '2121:2121'
      - '8080:8080'
    environment:
      SFTPGO_GRACE_TIME: 10
      SFTPGO_FTPD__BINDINGS__0__PORT: 2121
    volumes:
      - type: volume
        source: sftpgo_data
        target: /srv/sftpgo
      - type: volume
        source: sftpgo_data
        target: /var/lib/sftpgo
    restart: unless-stopped

volumes:
  sftpgo_data:
    external: true
```

```
http://localhost:8080/web/admin
```
