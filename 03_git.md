# Git

https://stackoverflow.com/a/70454786

## Set up

```shell
git remote add origin https://github.com/user/repo.git
git branch -M main
git push -u origin main
```

```shell
git config --global user.name "monkey"
git config --global user.email "monkey@gmail.com"
git config --global init.defaultBranch main
```

## Download

```shell
git clone -b main https://github.com/freeCodeCamp/freeCodeCamp.git
```

```shell
git fetch
```

List local branches
```shell
git branch
```

List remote branches
```shell
git branch -r
```

List all branches
```shell
git branch -a
```

Checkout local or remote branch
```shell
git switch feat/v1
```

Create a new branch from the current branch
```shell
git switch -c feat/v1
```

Create a new branch from the remote branch
```shell
git switch -c feat/v2 /origin/main
```

## Manage

Rename current branch
```shell
git branch -m new-branch-name
```

Delete local branch
```shell
git branch -d feat/v1
```

## History

```shell
git status
```

```shell
git log --graph --oneline --decorate
```

## Checkout

Checkout at the revision hash
```shell
git checkout revision_hash
```

Create a new branch from revision hash
```shell
git checkout -b feat/v1 revision_hash f668219
```

## Clear

Discard uncommitted local changes
```shell
git restore
```

Delete uncommitted files
```shell
git clean -fd
```

Removes the file from the index but leaves it in the working directory
```shell
git rm --cached .DS_Store
```

## Upload

```shell
git commit -m "feat: update README.md"
```

```shell
git push -u origin feat/v1
```
