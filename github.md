# GitHub Actions

https://docs.github.com/en/actions/quickstart

`.github/workflows/actions.yaml`
```
name: Actions on push
run-name: Triggered by ${{ github.actor }}
on:
  push:
    branches:
      - main
```
