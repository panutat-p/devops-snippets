# bash

## Basic

```sh
apt update
apt upgrade -y
```

```sh
apt install -y bash-completion lsb-release gpg gnupg apt-transport-https ca-certificates
apt install -y jq yq bzip2 alien curl wget git
```

## `~/.bashrc`

```bash
# Shell variables

# ENV variables
export EDITOR=nano
export KUBE_EDITOR=nano
export KUBECONFIG=${KUBECONFIG}:${HOME}/.kube/config
export PATH=$PATH:$(go env GOPATH)/bin

# Sources
source <(kubectl completion bash)
complete -o default -F __start_kubectl k

# Aliases
alias l='ls -laF'
alias ll='ls -lF'
alias k='kubectl'
alias kcontext='kubectl config get-contexts'
alias kga='kubectl get pod,service,deployment,job,cronjob,replicaset,statefulset,configmap,secret,ingress'
alias d='docker'
alias dcl='docker container ls -a'
alias dcs='docker container stop $(docker container ls -aq)'
alias dcr='docker rm -f $(docker container ls -aq)'

# functions
enc() {
  echo -n "$1" | base64
  echo
}

dec() {
  echo -n "$1" | base64 -d
  echo
}

hash() {
  echo -n "$1" | sha256sum
}

kn() {
  [ "$1" ] && kubectl config set-context --current --namespace $1 || kubectl config view --minify | grep namespace
}

kx() {
  [ "$1" ] && kubectl config use-context $1 || kubectl config current-context
}

kconfig() {
  kubectl get cm $1 -o yaml | yq e '.data' -
}

ksecret() {
  kubectl get secret $1 -o json | jq -r '.data | to_entries[] | .key + ": " + (.value | @base64d)'
}

gitlog() {
  git log --graph --oneline --decorate "$@"
}

gitb() {
  git branch "$@"
}

listport() {
  if [ $# -eq 0 ]
  then
    lsof -P -n -i
  else
    lsof -P -n -i | grep $1
  fi
}

killport() {
  if [ $# -eq 0 ]; then
    echo "Usage: killport port1 [port2 port3 ...]"
    return 1
  fi

  for port in "$@"; do
    pids=$(lsof -t -i:$port)
    if [ -n "$pids" ]; then
      for pid in $pids; do
        kill $pid
        echo "Closed process $pid on port $port"
      done
    else
      echo "No process running on port $port"
    fi
  done
}

forcekillport() {
  if [ $# -eq 0 ]; then
    echo "Usage: killport port1 [port2 port3 ...]"
    return 1
  fi

  for port in "$@"; do
    pids=$(lsof -t -i:$port)
    if [ -n "$pids" ]; then
      for pid in $pids; do
        kill -9 $pid
        echo "Closed process $pid on port $port"
      done
    else
      echo "No process running on port $port"
    fi
  done
}
```
