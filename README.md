# action-prettier
GitHub action that yells if formatting is not up to snuff.

## Disclaimer

You probably do not want to use this directly but rather have it as a component
in another github composite action.

## Usage

```yaml
name: Prettier

on: pull_request

jobs:
  prettier:
    name: Prettier
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2

    - name: Setup Node
      uses: actions/setup-node@v2
      with:
        node-version: '16'
        cache: 'npm'

    - name: Install dependencies
      run: npm ci
      working-directory: ./test

    - name: Prettier
      uses: reload/action-prettier
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
```
