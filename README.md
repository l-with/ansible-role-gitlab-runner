# Ansible Role GitLab Runner
Installs and registers a GitLab Runner manually (s. https://docs.gitlab.com/runner/install/linux-manually.html)

## Role Variables

###### `gitlab_runner_comand`: `register`

the command to execute with `gitlab-runner` (`register`/`unregister`)

###### `gitlab_runner_gitlab_url`

the URL of the GitLab instance 

###### `gitlab_runner_registration_token`

the token to register the runner
    

###### `gitlab_runner_executor`: `docker`

the runner executor

###### `gitlab_runner_docker_image`: `gitlab/gitlab-runner:alpine-bleeding`

the default image for the docker runner executor

###### `gitlab_runner_tag_list`: []

the tag list for the runner

###### `gitlab_runner_description`

the description for the  runner
