## Use docker for development

- Install docker CE: https://docs.docker.com/install/linux/docker-ce/ubuntu/

- First time installation:

    1. Replace name project in `docker-compose.yml` 
    2. Replace name project in `nginx/conf.d/app.conf` 
    ```
        {project} => real name project
    ```

    `make run`: Start some container

    OR

    `make run-d`: Start some background container

    `make migrate-seed`: Create + migrate + seed database

    `make app-exec`: Run a command inside the container app


- Note
  ```
    Make sure that all background container was started, run docker ps to check that.
  ```
- Start server:
  ```
  make run
  ```

- Migrate database then start server:
  ```
  make migrate
  ```

- Create/migrate/reset/seed database:
  ```
  make migrate-seed
  ```

- Remove docker containers:
  ```
  make down
  ```

- Config Nginx:
  ```
  ./docker/nginx/conf.d/app.conf
  ```

- Init user mysql:
  ```
  ./docker/mysql/init.sql
  ```
  
- Error Mysql:
    ```
    mysqld: [Warning] World-writable config file '/etc/mysql/conf.d/my.cnf' is ignored.
    ```
    
    ```
    chmod 0444 docker/mysql/cofig/my.cnf
    ```