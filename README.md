# git-action-testing
Git Action Testing AutoMerge

Merges main back into release branch and creates release branch if not found

```
name: Merge Main to Release
on:
  push:
    branches:
      - main
jobs:
  merge:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Set Git config
      run: |
          git config --local user.email "actions@github.com"
          git config --local user.name "Github Actions"
    - name: Create Release Branch if not exists and Merge Main to Release
      run: |
        git fetch --prune --unshallow
        git checkout -B release
        git fetch origin
        git merge origin/main --no-ff -m "Auto-merge main back to phoenix-releases"
        git push origin release

```
