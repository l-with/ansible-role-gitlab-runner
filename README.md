# Ansible Role GitLab Runner

Installs and registers a GitLab Runner manually (s. https://docs.gitlab.com/runner/install/linux-manually.html)

## Dependencies

This role needs docker to be installed.

## Role Variables

### `gitlab_runner_unregister`: `no`

if the gitlab-runner should be unregistered instead of registered

### `gitlab_runner_gitlab_url`

the URL of the GitLab instance 

### `gitlab_runner_registration_token`

the token to register the runner

### `gitlab_runner_executor`: `docker`

the runner executor

### `gitlab_runner_docker_image`: `gitlab/gitlab-runner:alpine-bleeding`

the default image for the docker runner executor

### `gitlab_runner_docker_pull_policy`: `if-not-present`

the docker-pull-policy

### `gitlab_runner_tag_list`: ""

the tag list for the runner

### `gitlab_runner_description`

the description for the  runner


### `gitlab_runner_locked`: `"true"`

the parameter for `--locked`

### `gitlab_runner_docker_prune_cron`: `yes`

if docker prune should be scheduled with cron

### `gitlab_runner_docker_prune_hour`: `5`

the schedule hour for docker prune

### `gitlab_runner_docker_prune_minute`: `30`

the schedule minute for docker prune

### `gitlab_runner_s3_cache_minio`: `no`

if s3 cache via [minio](https://min.io/) should be provided

### `gitlab_runner_s3_cache_name`: `runner`

the name of the s3 bucket shared by the GitLab runners

### `gitlab_runner_minio_address`

the url of minio for the GitLab runners

### `gitlab_runner_minio_root_user`

the user name of the minio root user

### `gitlab_runner_minio_root_password`

the password of the minio root user

### `gitlab_runner_s3_cache_minio_args`

default is

```yml
  - --cache-shared
  - --cache-type s3
  - --cache-s3-server-address {{ gitlab_runner_minio_address }}
  - --cache-s3-access-key {{ gitlab_runner_minio_root_user }}
  - --cache-s3-secret-key {{ gitlab_runner_minio_root_password }}
  - --cache-s3-bucket-name {{ gitlab_runner_s3_cache_name }}
  - --cache-s3-insecure
```

the arguments used for registering the GitLab runner if `gitlab_runner_s3_cache_minio` is yes
