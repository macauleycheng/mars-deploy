# Prepare files at local
* Setup environment at host_vars/localhost
> It will download needed files to `docker_path` `docker_compose_path` `dependencies_path`

* Run ``` ansible-playbook -vvv local.yml```

* Setup environment at group_vars/all
> Input `docker_image_path` `keepalive_version` `elk_version` `nginx_version` `logstash_version` `mars_version` <br> 
> Build docker image
* Run ``` docker-compose build
> Put docker image to tar file
* Run ``` ansible-playbook image_export.yml```
````diff
- Notice: Docker image of mars please export to docker_image_path by yourself
- Notice: if your change the git downlod folder mars-deploy, please also modify the docker image name in image_export.yml. The builded docker imaged name will have folder name as prefix
````

# Deploy to server
* Setup environment at group_vars/deploy
> Input your files location at local and the file location where you want to deploy <br>
> Modify hosts to specify which host to deploy
* According hosts create docker-compose config under host_vars directory
* Run ``` ansible-playbook deploy.yml```
* Run ``` ansible-playbook image_import.yml```
