# Prepare files at local
* Setup environment at host_vars/localhost
> It will download needed files to `docker_path` `docker_compose_path` `dependencies_path`

* Run ``` ansible-playbook local.yml```

* Setup environment at group_vars/all
> Input `docker_image_path` `keepalive_version` `elk_version` `nginx_version` `logstash_version` `mars_version`
  Build docker image
* Run ``` docker-compose build
  put docker image to tar file
* Run ``` ansible-playbook image_export.yml```
````diff
- Notice: Docker image of mars please export to docker_image_path by yourself
````

# Deploy to server
* Setup environment at group_vars/deploy
> Input your files location at local and the file location where you want to deploy
* According hosts create docker-compose config under host_vars directory
* Run ``` ansible-playbook deploy.yml```
* Run ``` ansible-playbook image_import.yml```
