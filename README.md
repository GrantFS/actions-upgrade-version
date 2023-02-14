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

      - name: Upgrade Version
        uses:  ./.github/actions/upgrade-version
        with:
          github-user: ${{ github.actor }}
          working-directory: "/src"

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
