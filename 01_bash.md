# bash

`~/.bashrc`
```bash
source ~/.taskfile.bash

export EDITOR=nano
export KUBE_EDITOR=nano
export PATH=$PATH:/usr/local/go/bin
KUBECONFIG=~/.kube/config

alias c='clear'
alias l='ls -laF'
alias ll='ls -lF'
alias gitlog='git log --graph --oneline --decorate'
alias k='kubectl'
alias kcontext='kubectl config get-contexts'
alias d='docker'
alias dcl='docker container ls -a'
alias dremove='docker rm $(docker ps -aq)'

enc() {
  echo -n "$1" | base64
  echo
}

dec() {
  echo -n "$1" | base64 -d
  echo
}

kn() {
  [ "$1" ] && kubectl config set-context --current --namespace $1 || kubectl config view --minify | grep namespace
}

kx() {
  [ "$1" ] && kubectl config use-context $1 || kubectl config current-context
}
```
