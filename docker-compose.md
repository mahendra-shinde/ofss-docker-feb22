# Docker Compose

- Packaging `multi-container` application into a single artifact
- docker-compose utility will then process and execute the docker-compose file.

# Docker Compose file
- Defined as `YAML` file
- Recommended filenames:
    1. compose.yml
    1. compose.yaml
    1. docker-compose.yml
    1. docker-compose.yaml

### Docker compose file components

```yaml
version: '3.5'

services:

volumes:

networks:
```

### Basic Demo

```yaml
version: '3.5'
services:
  app: 
    image: mahendrshinde/myweb:3
    ports:
    - 80
```

> Steps

1.  Save the file as `docker-compose.yml`
1.  Verify / Validate the YAML file
    
    ```
    docker-compose config
    ```
1.  Start all the container.

    ```
    docker-compose up -d
    docker-compose ps
    ```
### Compose commands

Command | Description
--------|-----------
docker-compose config | Verify the syntax of docker-compose
docker-compose up | Start all the containers, volumes and network, use -d switch daemon mode
docker-compose ps | List all the containers from compose file.
docker-compose exec | Older: docker-compose exec SERVICE SHELL Newer: docker-compose SERVICENAME -- SHELL


### On Swarm Cluster

1.  Login in https://labs.play-with-docker.com with docker-id
1.  Click on Wrench button to choose cluster template: "1 manager with 1 Worker"
1.  Use "manager1" and clone the project
    ```
    git clone https://github.com/mahendra-shinde/docker-compose-demos
    cd docker-compose-demo/demo1
    ```

1.  Deploy the application

    ```
    docker stack deploy --compose-file docker-compose.yml proj1
    docker stack ps proj1
    ```