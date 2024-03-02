# Networking

```shell
apt install net-tools
```

```shell
netstat --version
```

## ip

Show all network interfaces IP address
```shell
ip a
```

Show a specific network interface IP address
```shell
ip a show eth0
```

Show all network interface MAC address
```shell
ip link show
```

Show the routing table
```shell
ip r
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

Show RAW, UDP, TCP, or UNIX connection sockets
```shell
netstat -ant
```

To list services, their current state, and their corresponding ports
```
netstat -pnltu
```
