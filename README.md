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

### `gitlab_runner_tag_list`: []

the tag list for the runner

### `gitlab_runner_description`

the description for the  runner

### `gitlab_runner_docker_prune_cron`: `yes`

if docker prune should be scheduled with cron

### `gitlab_runner_docker_prune_hour`: `5`

the schedule hour for docker prune

### `gitlab_runner_docker_prune_minute`: `30`

the schedule minute for docker prune
