# Git

https://stackoverflow.com/a/70454786

## Set up

```sh
git config --global user.name '__'
git config --global user.email '__'
git config --global init.defaultBranch 'main'
git config --global pull.rebase 'true'
```

```sh
git config --global url.'https://username:token@gitlab.com/'.insteadOf 'https://gitlab.com/'
```

## Init repo

```sh
git remote add origin https://github.com/user/repo.git
git branch -M main
git push -u origin main
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

## Clear

Discard uncommitted local changes
```sh
git restore .
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
