# GitHub Action - Upgrade Version

[![Lint](https://github.com/GrantFS/actions-upgrade-version/actions/workflows/lint.yaml/badge.svg)](https://github.com/GrantFS/actions-upgrade-version/actions/workflows/lint.yaml)

Upgrade the current version of NPM/Release using [standard-version](https://www.npmjs.com/package/standard-version) and commit the changes to the branch provided

## Usage

**The action requires the project to use NPM**

> Install the [standard-version](https://www.npmjs.com/package/standard-version) NPM package

```bash

npm i standard-version


```

> Add NPM script to package.json

```json

    "scripts": {
        "release": "standard-version",
        ...
    }

```

> Create a Github Workflow

```yaml

name: Version

on:
  pull_request:
    branches:
      - main


permissions:
  id-token: write
  contents: write
  pull-requests: write
  actions: read

jobs:
  main-version:
    name: Version
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3
        with:
          ref: ${{ github.event.pull_request.head_branch }}

      - name: upgrade
        uses: GrantFS/actions-upgrade-version@V0.0.3
        with:
          github-user: ${{ github.actor }}

```

## Parameters

| Parameter        | Default Value | Required | Description                  |
|--------------------------|---------------------|--------------|----------------------------------------------------|
| github-user      | -          |  ✅    | User to add the commit          |
| working-directory | .          | ❌      | Directory to run the npm command |

## Outputs

| Output           | Description            |
|------------------------------|-------------------------------------|
| current-version     | New version! |
