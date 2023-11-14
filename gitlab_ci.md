# GitLab CI

## Example

https://docs.gitlab.com/ee/ci/quick_start/#create-a-gitlab-ciyml-file

`.gitlab-ci.yml`
```yaml
stages:
  - prepare

info:
  stage: prepare
  script:
    - date
    - echo "Job ID is $CI_JOB_ID"
    - echo "Triggered by $CI_PIPELINE_SOURCE"
    - echo "Run by $GITLAB_USER_LOGIN"
    - echo "Branch is $CI_COMMIT_BRANCH"

rules:
  - exists:
      - main
```

## Predefined variables

https://docs.gitlab.com/ee/ci/variables/predefined_variables.html

## Rules

https://docs.gitlab.com/ee/ci/quick_start/tutorial.html#start-using-merge-request-pipelines

https://docs.gitlab.com/ee/ci/yaml/index.html#rules

```yaml
rules:
  - exists:
      - main
```

```yaml
rules:
  - if: $CI_PIPELINE_SOURCE == 'merge_request_event'
```

```yaml
rules:
  - exists:
      - $CI_COMMIT_TAG
```
