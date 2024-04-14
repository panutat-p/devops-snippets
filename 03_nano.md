# nano

https://bash-prompt.net/guides/nanorc-settings

```shell
apt install nano
```

## Nano highlight

https://github.com/serialhex/nano-highlight#nano-highlight

```shell
git clone https://github.com/serialhex/nano-highlight ~/.nano
```

```shell
wget -O ~/.nano/go.nanorc http://go-lang.cat-v.org/text-editors/nano/go.nanorc
```

`~/.nanorc`
```bash
include "~/.nano/*.nanorc"

set linenumbers
set zap
set tabsize 2
set tabstospaces
set autoindent

bind ^a mark main
bind ^r redo main
bind ^z undo main
bind ^x cut main
bind ^c copy main
bind ^v paste main
bind ^f whereis main
bind ^g wherewas main
```
