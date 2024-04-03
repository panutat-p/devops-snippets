# zsh in MacOS

## `.zshrc`

```zsh
export PATH=$PATH:$HOME/go/bin

[[ $commands[kubectl] ]] && source <(kubectl completion zsh)
complete -o default -F __start_kubectl k
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

### Auto suggestions

https://github.com/zsh-users/zsh-autosuggestions

```sh
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### `.zshrc`

```shell
#ZSH_THEME="robbyrussell"
ZSH_THEME="powerlevel10k/powerlevel10k"

plugins=( 
  git
  zsh-autosuggestions
)

export ZSH="$HOME/.oh-my-zsh"

source $ZSH/oh-my-zsh.sh
[[ $commands[kubectl] ]] && source <(kubectl completion zsh)
# Updates PATH for the Google Cloud SDK.
if [ -f '/Users/pnt/google-cloud-sdk/path.zsh.inc' ]; then . '/Users/pnt/google-cloud-sdk/path.zsh.inc'; fi
# Enables shell command completion for gcloud.
if [ -f '/Users/pnt/google-cloud-sdk/completion.zsh.inc' ]; then . '/Users/pnt/google-cloud-sdk/completion.zsh.inc'; fi
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
colima start --cpu 4 --memory 8 --very-verbose
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
gh copilot explain 'go programming'
```
