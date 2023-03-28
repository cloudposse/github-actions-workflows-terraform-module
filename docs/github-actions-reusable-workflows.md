<!-- markdownlint-disable -->
## Workflows

| Name | Description |
|------|-------------|
| [Features Branch (Pull Request) Workflow ](#features-branch-pull-request-workflow) | ### Usage  |
| [Main Branch Workflow](#main-branch-workflow) | ### Usage  |




## Features Branch (Pull Request) Workflow 

### Usage 

In your repo create  __`.github/workflows/feature-branch.yaml`__

```yaml
  name: Feature Branch
  on:
    pull_request:
      branches: [ main ]
      types: [opened, synchronize, reopened]
  
  permissions:
    pull-requests: write
    id-token: write
    contents: read
  
  jobs:
    default:
      uses: cloudposse/github-actions-workflows-terraform-module/.github/workflows/feature-branch.yml@main
      secrets:
        github_access_token: ${{ secrets.GH_ACCESS_TOKEN }}
```





### Secrets

| Name | Description | Required |
|------|-------------|----------|
| github\_access\_token | GitHub API token | false |






## Main Branch Workflow

### Usage 

In your repo create  __`.github/workflows/main-branch.yaml`__

```yaml
  name: Main Branch
  on:
    push:
      branches: [ main ]
  
  permissions:
    contents: write
    id-token: write
  
  jobs:
    terraform-module:
      uses: cloudposse/github-actions-workflows-terraform-module/.github/workflows/feature-branch.yml@main
      secrets:
        github_access_token: ${{ secrets.GH_ACCESS_TOKEN }}
```





### Secrets

| Name | Description | Required |
|------|-------------|----------|
| github\_access\_token | GitHub API token | true |





<!-- markdownlint-restore -->
