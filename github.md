# GitHub Actions

## Example

https://docs.github.com/en/actions/quickstart

`.github/workflows/actions.yaml`
```yaml
name: Actions on push
run-name: Run by ${{ github.actor }}
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

## Events

https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows

```yaml
on:
  push:
    branches:
      - main
```

```yaml
on:
  push:
    tags:
      - *
```

```yaml
on:
  pull_request:
    types:
      - opened
      - reopened
    branches:
      - main
      - release/**
```

```yaml
on:
  schedule:
    - cron: '30 5 * * 1,3'
    - cron: '30 5 * * 2,4'
```
