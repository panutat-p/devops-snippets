# Git

```shell
git remote add origin https://github.com/user/repo.git
git branch -M main
git push -u origin main
```

## List branches

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

## Create a local branch

```shell
git switch -c feat
```

```shell
git switch -c feat dev
```

## Graph

```shell
git log --graph --oneline --decorate
```

## Clear

```shell
# delete uncommitted files
git clean -fd

# clear local changes
git reset --hard
```

```shell
# removes the file from the index but leaves it in the working directory
git rm --cached .DS_Store
```
