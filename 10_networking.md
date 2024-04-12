# Networking

```sh
apt install net-tools
```

## Port number

List all listening port numbers
```sh
lsof -P -n -i | grep LISTEN
```

Check task that use port 8080
```sh
lsof -P -n -i :8080
```

Close the task by SIGTERM
```sh
kill $(lsof -t -i:8080)
```

Close the task by SIGKILL
```sh
kill -9 $(lsof -t -i:8080)
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
```sh
ip r
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

## DigitalOcean Guide

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
