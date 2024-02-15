# bash

`~/.bashrc`
```bash
# shell variables

# ENV variables
export EDITOR=nano
export KUBECONFIG=${KUBECONFIG}:${HOME}/.kube/config
export KUBE_EDITOR=nano
export PATH=$PATH:$(go env GOPATH)/bin
export USE_GKE_GCLOUD_AUTH_PLUGIN=True

# aliases, a full list of active aliases, run `alias`.
alias l='ls -laF'
alias ll='ls -lF'
alias gitlog='git log --graph --oneline --decorate'
alias k='kubectl'
alias kcontext='kubectl config get-contexts'
alias d='docker'
alias dcl='docker container ls -a'
alias dcr='docker rm -f $(docker ps -aq)'

# sources
source ~/.taskfile.bash

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
```
