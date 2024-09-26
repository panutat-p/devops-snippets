# zsh

## SSH Client

```sh
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519
```

```sh
ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa
```

## OH MY ZSH

https://ohmyz.sh/#install

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Theme: power level 10k

https://github.com/romkatv/powerlevel10k

```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
echo 'ZSH_THEME="powerlevel10k/powerlevel10k"' >> ~/.zshrc
```

```sh
p10k help
```

### Amazon CodeWhisperer

```
wget -O code_whisperer.dmg 'https://desktop-release.codewhisperer.us-east-1.amazonaws.com/latest/CodeWhisperer.dmg'
open code_whisperer.dmg
```

```sh
cw -h
```

```sh
cw integrations install input-method
```

### Auto suggestions

https://github.com/zsh-users/zsh-autosuggestions

```sh
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### Instant prompt

https://github.com/romkatv/powerlevel10k/blob/master/README.md#instant-prompt

```bash
cat .p10k.zsh
```

## `.zshrc`

```zsh
# Powerlevel10k instant prompt
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi
plugins=( 
  git
  zsh-autosuggestions
)

# Shell variables
ZSH_THEME="powerlevel10k/powerlevel10k"

# ENV variables
export ZSH="$HOME/.oh-my-zsh"
export EDITOR=nano
export KUBE_EDITOR=nano
export KUBECONFIG=${KUBECONFIG}:${HOME}/.kube/config
export PATH=$PATH:$HOME/go/bin

# Sources
source $ZSH/oh-my-zsh.sh
[[ $commands[kubectl] ]] && source <(kubectl completion zsh)
complete -o default -F __start_kubectl k

# Aliases
alias l='ls -laF'
alias ll='ls -lF'
alias k='kubectl'
alias kcontext='kubectl config get-contexts'
alias kga='kubectl get pod,service,deployment,job,cronjob,replicaset,statefulset,configmap,secret,ingress'
alias d='docker'
alias dcl='docker container ls -a'
alias dcr='docker rm -f $(docker ps -aq)'

# Functions
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
