# ncat

https://nmap.org/ncat

https://nmap.org/ncat/guide/index.html

## Install

### Ubuntu rpm to deb

https://nmap.org/download.html#linux-rpm

```sh
wget https://nmap.org/dist/ncat-7.94-1.x86_64.rpm
alien --to-deb ncat-7.94-1.x86_64.rpm
dpkg --install ncat_7.94-2_amd64.deb
```

### Ubuntu apt

```sh
apt install -y ncat
```

### MacOS

https://nmap.org/download.html#macosx

```sh
wget -O nmap.dmg https://nmap.org/dist/nmap-7.94.dmg
open nmap.dmg
```

## connect mode

### manually retrieve a web page from an HTTP server

```sh
ncat -C google.com 80
```

```sh
ncat -C localhost 4000
```

hit enter twice
```
GET / HTTP/1.0
```

### Check TCP connection

```sh
ncat -vz localhost 4000
```

### Check UDP connection

```sh
ncat -vzu localhost 4000
```

## listen mode

### Host a an HTTP file

`hello.http`
```
HTTP/1.0 200 OK

<html>
  <body>
    <h1>Hello, world!</h1>
  </body>
</html>
```

```sh
ncat -l localhost 8080 < hello.http
```

### Host an HTML file

https://nmap.org/ncat/guide/ncat-tricks.html#ncat-httpserv

```sh
ncat -lk -p 8080 --sh-exec "echo -e 'HTTP/1.1 200 OK\r\n'; cat index.html"
```

### Forward proxy

```sh
ncat -lk 4001 --sh-exec 'ncat 10.98.32.11 6379'
```

```sh
ncat -lk 8080 --sh-exec 'ncat localhost 4000'
```

### Running in background

```sh
nohup ncat -lk 4001 --sh-exec 'ncat 10.2.1.1 6379' &
```

```sh
ps aux | grep 'ncat'
```

```sh
kill $PID
```

```sh
kubectl port-forward pod/ubuntu 4001:4001
```

```sh
redis-cli -h localhost -p 4001 PING
```
