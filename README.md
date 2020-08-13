# EveryWorkflow Project Docker

A docker for every workflow project


## Stack

- nginx
- php-7.4
    - mongodb-1.8.0 extension
    - redis extension
    - composer cli
    - symfony cli
- redis
- mongodb


## Setup

- git clone this repo
- `mkdir project` or `git clone <some_git_repo_url> project`
- `docker-compose up -d`
- `docker-compose exec php-cli bash`


## Notes

- In current stage, this docker can only be used in dev box
- Home URL: `http://{localhost/any_valid_host}:2000/` 
- For more info and change, check `docker-compose.yml`
- Set `www-data` as file owner
- `php-cli` container stays alive due to `tty: true` in `docker-compose.yml` file
- `project` dir is code root dir
```
- <project-docker> <-- docker root dir
- <project-docker>/data <-- all docker data persist
- <project-docker>/nginx <-- nginx
- <project-docker>/php-fpm <-- php-fpm container
- <project-docker>/php-cli <-- php-cli container
- <project-docker>/project <-- every workflow project root dir
- <project-docker>/project* <-- added in .gitignore
```
- MongoDB Compass client can be directly connected using following details:-
```
mongodb://root:root@localhost:27017/?authSource=admin
```


## Phpstorm

Simply add remote docker php cli interpreter (php-cli), change path mapping and configure remote interpreter everywhere.


## Container + vscode

With vscode's remote container extension, we can simply connect into `php-cli` container.
