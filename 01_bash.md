# bash

`~/.bashrc`
```bash
# shell variables

# ENV variables
export EDITOR=nano
export KUBE_EDITOR=nano
export KUBECONFIG=${KUBECONFIG}:${HOME}/.kube/config
export AWS_PROFILE=dev
export USE_GKE_GCLOUD_AUTH_PLUGIN=True
export CLOUDSDK_PYTHON=python3.11

# PATH
export PATH=$PATH:/usr/local/go/bin

# aliases, a full list of active aliases, run `alias`.
alias l='ls -laF'
alias ll='ls -lF'
alias gitlog='git log --graph --oneline --decorate'
alias k='kubectl'
alias kcontext='kubectl config get-contexts'
alias kga='kubectl get pod,service,deployment,job,cronjob,replicaset,statefulset,configmap,secret,ingress'
alias d='docker'
alias dcl='docker container ls -a'
alias dcr='docker rm -f $(docker ps -aq)'

# sources
source ~/.taskfile.bash
source <(kubectl completion bash)
complete -o default -F __start_kubectl k

# functions
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

kconfig() {
  kubectl get cm $1 -o yaml | yq e '.data' -
}

ksecret() {
  kubectl get secret $1 -o json | jq -r '.data | to_entries[] | .key + ": " + (.value | @base64d)'
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
