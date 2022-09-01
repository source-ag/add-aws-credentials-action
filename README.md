# AWS Credentials Action

## :warning: DEPRECATED

Please use [`aws-actions/configure-aws-credentials`](https://github.com/aws-actions/configure-aws-credentials) 
instead. [The bug](https://github.com/actions/runner/issues/789) that the action in this repo is a workaround for has 
been fixed, so we can use the official action instead.

---

This Github Action will configure AWS credentials without using environment variables. 
Contrary to the [official Github Action](https://github.com/aws-actions/configure-aws-credentials) 
for configuring credentials, this action can be called multiple times in a workflow, completely 
overwriting the previously configured credentials.

Usage:

```yaml
name: doing-aws-things

on:
  push:
    branches:
      - main

jobs:
  do-stuff:
    runs-on: ubuntu-latest
    steps:
      - name: Login to AWS
        uses: source-ag/add-aws-credentials-action@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: eu-central-1
          role-to-assume: ${{ secrets.MY_ROLE }}
```
