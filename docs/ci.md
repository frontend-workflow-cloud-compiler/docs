# CI Systems Usage

Its very common to compile your dist files into a docker image while running your pipelines, therefore those are examples for unglue usage inside of CI system.

## GitLab

```yaml
  image: php:7.4-cli
  stage: build
  services:
    - name: unglue/server
      alias: unglue
  before_script:
    - apt-get -y update && apt-get install -y wget
    - wget -O unglue.phar https://github.com/unglue-workflow/client/raw/master/unglue.phar
    - chmod +x unglue.phar
  script:
    - ./unglue.phar compile --server=unglue:3000
```

Maybe its required to publish your artifacts for further steps, therefore use something like thise, while `resources` is the folder the compiled files are published:

```yaml
artifacts:
  paths:
    - "resources"
```
