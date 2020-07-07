# EveryWorkflow Project Docker

A docker for every workflow project.


## Stack

- nginx
- php-7.4
- redis
- mongodb


## Setup

- git clone this repo
- `mkdir project` or `git clone <some_git_repo_url> project`
- `docker-compose up -d`
- `docker-compose exec php bash`


## Notes

- In current stage, this docker can only be used in dev box
- Home URL: `http://{localhost/any_valid_host}:2000/`
- For more info read `docker-compose.yml`
- `project` dir is code root dir
```
- <some_project_docker>
- <some_project_docker>/data <-- all docker data persist
- <some_project_docker>/nginx
- <some_project_docker>/php
- <some_project_docker>/project <-- every workflow project
- <some_project_docker>/project* <-- added in .gitignore
```
- MongoDB Compass client can be directly connected using following details:-
```
mongodb://root:root@localhost:27017/?authSource=admin
```

## Issues

- Permission reset issue, exec into project dir and do `chmod -R 777 .` for now in dev box

