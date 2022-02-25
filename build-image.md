# Building An Image using Dockerfile

Docker Image could be built using TWO methods:

1.  Interactive method

    Create the temporary container from existing base image

    Make changes to temp. container (docker exec or docker cp)

    Commit the changes to new image.

    ```
    docker commit -a "Author Name" -m "Message" temp IMAGENAME
    ```

2. Declarative Method

    Create `Dockerfile` [ Case sensitive, no extension] with all the steps to build an image.
    Use command `docker build` to build an image

    ```
    docker build -t IMAGENAME FOLDER-PATH
    ## Use "." for Current working directory
    docker build -t myapp2 . 
    ```

## Dockerfile Tasks

Task Name | Description
-------|---------------
FROM [IMAGE] | Specify the base image, or use `scratch`
COPY [SRC] [DEST] | Copy files/directories from Host System to Container Image.
ADD [SRC] [DEST]  | Similar to COPY, It can accept URL as SRC, it can download file and then copy.
RUN ['ARG1','ARG2',...,'ARG-N'] | Run a command or script while BUILDING the image.
ENV KEY=VALUE | Pass environment variables to new image.
EXPOSE port | Specify which port, containerized application is listening. Consider this as Documentation. 
CMD ['CMD','ARG1'] | The command to RUN when container is started (Only when used without Entrypoint).
ENTRYPOINT ['Cmd'] | The command to RUN when container is started, When used ALONG WITH CMD, CMD Becomes an Argument to Entrypoint.

## Sample Dockerfile

```Dockerfile
FROM ubuntu

ENV DEBIAN_FRONTEND=noninteractive

RUN ["apt","update","-y"]

RUN ["apt","install","-y","cowsay"]

## Both 'ENTRYPOINT' and 'CMD' Must be Used ONLY ONCE in Dockerfile
ENTRYPOINT [ "/usr/games/cowsay","-f", "dragon" ]
# When used with entrypoint, CMD becomes ARGUMENT to entrypoint
CMD ["Hello World"]
```

## Multi Stage Dockerfile

- Each `stage` would have it's OWN `FROM` statement in the beginning
- Except the `final` stage, every stage should have `An Alias`
- All `stages` are build `sequentially` and `files` can be copied from `previous` stage.

## Demo

1. Using `terminal` just `clone the repository` 

    ```
    cd ~
    git clone https://github.com/mahendra-shinde/ci-servlet-demo
    cd ci-servlet-demo
    ```

2.  Review the contents of `Dockerfile`

    ```
    cat Dockerfile
    ```

3.  Build one image `java-app`

    ```
    docker build -t java-app . 
    ```

4.  Create a container to test

    ```
    docker run -d --name t1 java-app
    IP=$(docker inspect t1 --format "{{ .NetworkSettings.IPAddress }}" )
    firefox http://$IP:8080
    ```

5.  Clean Up

    ```
    docker stop t1
    docker rm t1
    docker rmi java-app
    ```

## Push to Registry

1. You need to LOGIN into registry (Login is persistent )

    ```
    docker login REGISTRY-URL -uUSERNAME -pPASSWORD 
    ```

2.  TAG your image with either DOCKERID or REGISTRY URL

    ```
    docker tag java-app mahendrshinde/java-app
    docker push mahendrshinde/java-app
    ```

