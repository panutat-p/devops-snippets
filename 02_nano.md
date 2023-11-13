# nano

https://bash-prompt.net/guides/nanorc-settings

https://github.com/serialhex/nano-highlight#nano-highlight

```shell
apt install nano
```

```shell
apk add nano
```

```shell
yum install nano
```

`~/.nanorc`
```bash
set linenumbers
set zap
set tabsize 2
set tabstospaces
set autoindent

bind ^a redo main
bind ^z undo main
bind ^x cut main
bind ^c copy main
bind ^v paste main
bind ^f whereis main
bind ^g wherewas main
```
