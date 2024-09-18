# SFTP Go

https://hub.docker.com/r/drakkan/sftpgo

https://github.com/drakkan/sftpgo

https://github.com/drakkan/sftpgo/blob/main/docs/howto/getting-started.md

https://github.com/drakkan/sftpgo/blob/main/docs/full-configuration.md

https://github.com/drakkan/sftpgo/blob/main/sftpgo.json

```yaml
services:
  sftp:
    image: drakkan/sftpgo:v2
    ports:
      - '2022:2022'
      - '2121:2121'
      - '8080:8080'
    environment:
      SFTPGO_DEFAULT_ADMIN_USERNAME: root
      SFTPGO_DEFAULT_ADMIN_PASSWORD: 1234
      SFTPGO_HTTPD__ADMIN__USERNAME: root
      SFTPGO_HTTPD__ADMIN__PASSWORD: 1234
      SFTPGO_FTPD__BINDINGS__0__PORT: 2121
      SFTPGO_GRACE_TIME: 10
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
