# Git

https://stackoverflow.com/a/70454786

## Config

```sh
git config --global user.name '__'
git config --global user.email '__'
git config --global init.defaultBranch 'main'
git config --global pull.rebase 'true'
git config --global rebase.autoStash 'true'
git config --global pager.branch 'false'
git config --global core.editor 'nano'
git config --global alias.log1 'log --graph --oneline --decorate'
```

Use Visual Studio Code
```sh
git config --global core.editor 'code --wait'
```

```sh
git config --global url.'https://token@github'.insteadOf 'https://github'
```

```sh
git config --global url.'https://username:token@gitlab.com'.insteadOf 'https://gitlab.com'
```

Show global git config
```sh
git config --list --global
```

Show git config of current repository
```sh
git config --list --local
```

Multiple remote
`.gitconfig`
```
[includeIf "gitdir:~/github/"]
    path = ~/github/.gitconfig
```

## Remote

```sh
git remote rm origin
git remote add origin https://github.com/user/repo.git
git branch -M main
git push -u origin main
```

List remote hosts
```sh
git remote -v
```

View branch config
```sh
git branch -vv
```

Set the upstream of the current branch
```sh
git branch -u origin/main
```

## View

```sh
git status
```

```sh
git log --graph --oneline --decorate
```

## Branch

List remote branches
```sh
git branch -r
```

List all branches
```sh
git branch -a
```

Force pull
```sh
git fetch origin
git reset --hard origin/feat/v1
```

Create a new branch that tracks the remote branch
```sh
git branch --track feat/v1 origin/feat/v1
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
git push -u origin feat/v2
```

Clone a remote branch
```sh
git switch --track -c feat/v1 origin/feat/v1
```

Rename branch
```sh
git branch -m feat/v3
```

Rename branch forcefully
```sh
git branch -M feat/v3
```

Delete local branch
```sh
git branch -d feat/v1
```

Checkout at the revision hash
```sh
git switch -d 772952b
```

Create a new branch from revision hash
```sh
git switch -c feat/v1 772952b
```

Return to the previous branch
```sh
git switch -
```

## Stash

Stash only tracked files
```sh
git stash
```

Stash both tracked and untracked files (`-u` is `--include-untracked`)
```sh
git stash -u
```

Stash everything including ignored files
```sh
git stash --all
```

```sh
git stash list
```

```sh
git stash apply
```

Apply and remove the top item
```sh
git stash pop
```

```sh
git stash apply stash@{1}
```

Remove top item in stash
```sh
git stash drop
```

Remove specific item in stash
```sh
git stash drop stash@{1}
```

Remove all items in stash
```sh
git stash clear
```

## Clear

https://stackoverflow.com/a/42903805

Unstage changes
```sh
git restore --staged .
```

Discard unstaged changes
```sh
git restore .
```

Delete untracked files
```sh
git clean -fd
```

Discard both unstaged chagnes and staged changes
```sh
git reset --hard
```

Removes the file from the index but leaves it in the working directory
```sh
git rm --cached .DS_Store
```

## Download

```sh
git clone -b main https://github.com/skills/introduction-to-github.git
```

```sh
git clone https://github.com/skills/introduction-to-github.git intro_to_github
```

## Upload

```sh
git add .
```

```sh
git add go.*
```

```sh
git add -f .env
```

```sh
git commit -m "feat: update README.md"
```

Rename commit message
```sh
git commit --amend -m 'business-date'
```

```sh
git push -u origin feat/v1
```

## Rebase

https://www.youtube.com/watch?v=42392W7SgnE

Move past commits forward
```sh
git fetch origin
git rebase origin/main
```

Edit past commits interactively
```sh
git pull
git rebase -i f893a71
# Change pick to edit
# Then edit the files
git add .
git rebase --continue
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
ghcs -t git 'list stash, apply specific stash then delete it'
```
