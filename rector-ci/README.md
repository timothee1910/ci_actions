# rector-ci

add a comment on pull request when rector request changes

usage: 
```yaml
name: Rector CI

on:
  pull_request: null

jobs:
  rector-ci:
    runs-on: ubuntu-latest
    # run only on commits on main repository, not on forks
    if: github.event.pull_request.head.repo.full_name == github.repository
    steps:
      - uses: micro_macro/backend-ci/rector-ci@v3.3.1
        with:
          token: ${{ secrets.ACCESS_TOKEN_RECTOR }} # default ${{ github.token }}
          auth_json: ${{ secrets.ACCESS_AUTH }} # optional
```

## TODO

 - improve doc
 - make it more configurable
 - middle finger is to agressive ? replace with unicorn ?