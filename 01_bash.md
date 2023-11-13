# bash

`~/.bashrc`
```bash
export EDITOR=nano
export KUBE_EDITOR=nano

KUBECONFIG=~/.kube/config

alias c='clear'
alias l='ls -laF'
alias ll='ls -lF'
alias gitlog='git log --graph --oneline --decorate'
alias k='kubectl'
alias d='docker'
alias dc='docker-compose'
alias dlist='docker container ls -a'
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
