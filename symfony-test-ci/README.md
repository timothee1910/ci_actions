# symfony-test-ci

use php unit to test symfony application.

usage: 
```yaml
name: CI / Test symfony / php unit

on:
  pull_request: null

jobs:
  symfony-test-ci:
    runs-on: ubuntu-latest
    services:
      # https://docs.docker.com/samples/library/mysql/
      mysql:
        image: mysql:5.7
        env:
          MYSQL_ROOT_PASSWORD: root
        ports:
          - 3306:3306
        options: --health-cmd="mysqladmin ping" --health-interval=10s --health-timeout=5s --health-retries=3
    strategy:
      fail-fast: true
    steps:
      - uses: micro_macro/backend-ci/symfony-test-ci@v2
        with:
          es_port: 9209 # default 9209
          database_url: mysql://root:root@127.0.0.1:3306/your_database
          auth_json: ${{ secrets.ACCESS_AUTH }}
```