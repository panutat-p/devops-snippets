# Linux Commands

## directory

Go back to previous directory
```sh
cd -
```

## stdout

Show available disk space & write/overwrite to a file
```sh
df -h | tee disk_usage.txt
```

Show available disk space & append to a file
```sh
df -h | tee -a file.out
```

## PATH

```shell
echo $PATH
```

```shell
export PATH=$PATH:/usr/local/go/bin
```

```shell
export PATH=$PATH:/usr/lib/jvm/java21/bin
```

## System

```shell
lsb_release -a
```

```shell
systemctl status nginx
```

```shell
systemctl start nginx
```

```shell
systemctl stop nginx
```

```shell
systemctl restart  nginx
```

## User

```shell
sudo -i
```

```shell
whoami
```

## Kill a process

```shell
ps aux
```

```shell
htop
```

```shell
kill <pid>
```

## Background

```shell
commmand &
```

```shell
bg
```

```shell
fg
```

```shell
fg %1
```
