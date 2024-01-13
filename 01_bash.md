# bash

`~/.bashrc`
```bash
source ~/.taskfile.bash

KUBECONFIG=~/.kube/config

export EDITOR=nano
export KUBE_EDITOR=nano
export PATH=$PATH:/usr/local/go/bin
export PATH=$PATH:~/go/bin
export USE_GKE_GCLOUD_AUTH_PLUGIN=True

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

## OH MY ZSH

https://ohmyz.sh/#install

```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

https://github.com/zsh-users/zsh-autosuggestions

`.zshrc`
export ZSH="$HOME/.oh-my-zsh"

ZSH_THEME="robbyrussell"

```shell
plugins=( 
    git
    zsh-autosuggestions
)

[[ $commands[kubectl] ]] && source <(kubectl completion zsh)
if [ -f '/Users/pnt/google-cloud-sdk/path.zsh.inc' ]; then . '/Users/pnt/google-cloud-sdk/path.zsh.inc'; fi
if [ -f '/Users/pnt/google-cloud-sdk/completion.zsh.inc' ]; then . '/Users/pnt/google-cloud-sdk/completion.zsh.inc'; fi

source $ZSH/oh-my-zsh.sh
```
