# Git

```shell
git remote add origin https://github.com/user/repo.git
git branch -M main
git push -u origin main
```

```shell
# list all branches
git branch -a
```

```shell
# create a local branch
git branch develop origin/develop

# checkout a local branch
git checkout develop

# checkout a remote branch
git checkout -b develop origin/develop
```

```shell
git log --graph --oneline --decorate
```

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
