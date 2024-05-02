# Git

https://stackoverflow.com/a/70454786

## Set up

```sh
git config --global user.name '__'
git config --global user.email '__'
git config --global init.defaultBranch 'main'
git config --global pull.rebase 'true'
git config --global rebase.autoStash 'true'
```

```sh
git config --global url.'https://token@github'.insteadOf 'https://github'
```

```sh
git config --global url.'https://username:token@gitlab.com/'.insteadOf 'https://gitlab.com/'
```

## Init repo

```sh
git remote rm origin
```

```sh
git remote add origin https://github.com/user/repo.git
git branch -M main
git push -u origin main
```

```sh
git remote -v
```

## Download

```sh
git clone -b main https://github.com/skills/introduction-to-github.git
```

```sh
git clone https://github.com/skills/introduction-to-github.git intro_to_github
```

```sh
git fetch
```

```sh
git pull
```

```sh
git pull --rebase
```

List local branches
```sh
git branch
```

List remote branches
```sh
git branch -r
```

List all branches
```sh
git branch -a
```

Checkout local or remote branch
```sh
git switch feat/v1
```

Create a new branch from the current branch
```sh
git switch -c feat/v1
```

Create a new branch from the remote branch
```sh
git switch -c feat/v2 /origin/main
```

## Manage

Rename current branch
```sh
git branch -m new-branch-name
```

Delete local branch
```sh
git branch -d feat/v1
```

## History

```sh
git status
```

```sh
git log --graph --oneline --decorate
```

## Checkout

Checkout at the revision hash
```sh
git checkout revision_hash
```

Create a new branch from revision hash
```sh
git checkout -b feat/v1 revision_hash f668219
```

## Stash

```sh
git stash --all
```

```sh
git stash list
```

```sh
git stash apply 
```

## Clear

https://stackoverflow.com/a/42903805

Discard uncommitted local changes
```sh
git restore .
```

Discard all local changes
```sh
git reset --hard
```

Delete uncommitted files
```sh
git clean -fd
```

Removes the file from the index but leaves it in the working directory
```sh
git rm --cached .DS_Store
```

## Upload

```sh
git commit -m "feat: update README.md"
```

```sh
git push -u origin feat/v1
```

## GitHub CLI

https://docs.github.com/en/copilot/github-copilot-in-the-cli/using-github-copilot-in-the-cli

Ububtu
```sh
mkdir -p -m 755 /etc/apt/keyrings && wget -qO- https://cli.github.com/packages/githubcli-archive-keyring.gpg | tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null
chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | tee /etc/apt/sources.list.d/github-cli.list > /dev/null
apt update
apt install gh -y
echo 'eval "$(gh copilot alias -- bash)"' >> ~/.bashrc
```

MacOS
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
