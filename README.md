# Ansible Role GitLab Runner

Installs and registers a GitLab Runner manually (s. https://docs.gitlab.com/runner/install/linux-manually.html)

## Dependencies

This role needs docker to be installed.

## Role Variables

<!-- markdownlint-disable MD033 -->
| group | variable | default | description |
| --- | --- | ---| --- |
| lifecycle | gitlab_runner_unregister | `no` | if the gitlab-runner should be unregistered instead of registered |
| basic | gitlab_runner_description | | the description for the  runner |
| basic | gitlab_runner_executor | `docker` | the runner executor |
<!-- markdownlint-enable MD033 -->

## Role Variables only used, when not `gitlab_runner_unregister` 

<!-- markdownlint-disable MD033 -->
| group | variable | default | description |
| --- | --- | ---| --- |
| gitlab | gitlab_runner_gitlab_url | | the URL of the GitLab instance |
| gitlab | gitlab_runner_registration_token | | the token to register the runner |
| runner | gitlab_runner_docker_image | `gitlab/gitlab-runner:alpine-bleeding` | the default image for the docker runner executor |
| runner | gitlab_runner_docker_pull_policy | `if-not-present` | the docker-pull-policy |
| runner | gitlab_runner_tag_list | `""` | the tag list for the runner |
| runner | gitlab_runner_run_untagged | `yes` | if the runner should be registered with `--run_untagged` |
| runner | gitlab_runner_locked | `"true"` | the parameter for `--locked` |
| prune | gitlab_runner_docker_prune_cron | `yes` | if docker prune should be scheduled with cron |
| prune | gitlab_runner_docker_prune_hour | `5` | the schedule hour for docker prune |
| prune | gitlab_runner_docker_prune_minute | `30` | the schedule minute for docker prune |
| cache | gitlab_runner_s3_cache_minio | `no` | if s3 cache via [minio](https://min.io/) should be provided |
| cache | gitlab_runner_s3_cache_name | `runner` | the name of the s3 bucket shared by the GitLab runners |
| cache | gitlab_runner_minio_address | | the url of minio for the GitLab runners |
| cache | gitlab_runner_minio_root_user | | the url of minio for the GitLab runners | the user name of the minio root user |
| cache | gitlab_runner_minio_root_password | | the password of the minio root user |
| cache | gitlab_runner_s3_cache_minio_args | see below| the arguments used for registering the GitLab runner if `gitlab_runner_s3_cache_minio` is yes |
<!-- markdownlint-enable MD033 -->

default for `gitlab_runner_s3_cache_minio_args`:

```yml
  - --cache-shared
  - --cache-type s3
  - --cache-s3-server-address {{ gitlab_runner_minio_address }}
  - --cache-s3-access-key {{ gitlab_runner_minio_root_user }}
  - --cache-s3-secret-key {{ gitlab_runner_minio_root_password }}
  - --cache-s3-bucket-name {{ gitlab_runner_s3_cache_name }}
  - --cache-s3-insecure
```
