# GitHub Actions

https://docs.github.com/en/actions/quickstart

`.github/workflows/actions.yaml`
```yaml
name: Actions on push
run-name: Triggered by ${{ github.actor }}
on:
  push:
    branches:
      - main

jobs:
  info:
    runs-on: ubuntu-latest
    steps:
      - run: echo "Triggered by a ${{ github.event_name }} event"
      - run: echo "Repository is ${{ github.repository }}"
      - run: echo "Branch is ${{ github.ref }}"
```
