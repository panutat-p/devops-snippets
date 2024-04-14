# zsh in MacOS

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
alias gitlog='git log --graph --oneline --decorate'
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

## OH MY ZSH

https://ohmyz.sh/#install

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Theme: power level 10k

https://github.com/romkatv/powerlevel10k

```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

```sh
p10k configure
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

## Colima

```sh
brew install colima
```

List available CPUs
```sh
qemu-system-aarch64 -cpu help
```

```sh
colima start --cpu 4 --memory 8 --network-address --very-verbose
```

```sh
colima status --very-verbose
```

```sh
colima stop --force
```

```sh
colima delete
```

## Docker

```sh
brew install docker
```

## Docker plugins

https://github.com/abiosoft/colima/discussions/273#discussioncomment-4959736

```sh
mkdir -p ~/.docker/cli-plugins
```

```sh
brew install docker-buildx
```

```sh
ln -sfn /opt/homebrew/opt/docker-buildx/bin/docker-buildx ~/.docker/cli-plugins/docker-buildx
```

https://github.com/docker/compose/issues/8630#issuecomment-1169537632

```sh
brew install docker-compose
```

```sh
ln -sfn /opt/homebrew/opt/docker-compose/bin/docker-compose ~/.docker/cli-plugins/docker-compose
```

## Lazy Docker

https://github.com/jesseduffield/lazydocker

```sh
brew install lazydocker
```

## GitHub CLI

https://docs.github.com/en/copilot/github-copilot-in-the-cli/using-github-copilot-in-the-cli

```sh
brew install gh
```

```sh
gh auth login --web -h github.com
```

```sh
gh extension install github/gh-copilot
gh extension upgrade gh-copilot
```

```sh
echo 'eval "$(gh copilot alias -- zsh)"' >> ~/.zshrc
```

```sh
ghce 'go programming'
```

```sh
ghcs 'list running port numbers in MacOS'
```

```sh
ghcs -t git 'delete files/dirs that are not tracked'
```

```sh
ghcs -t git 'discard all local changes'
```

```sh
ghcs -t git 'discard all local changes'
```
