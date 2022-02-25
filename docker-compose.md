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
