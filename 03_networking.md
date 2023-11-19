# Networking

```shell
apt install net-tools
```

```shell
netstat --version
```

## Port number

https://www.digitalocean.com/community/tutorials/opening-a-port-on-linux

List all open ports
```shell
netstat -lntu
```

Check specific port number
```shell
netstat -na | grep :4000
```

Allow specific port number
```shell
sudo ufw allow 4000
```

## Routing table

Display routing table
```shell
netstat -nr
```

Display network interface statistics
```shell
netstat -ai
```

Show network connections
```shell
netstat -ant
```
