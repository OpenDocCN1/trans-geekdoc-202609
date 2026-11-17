# # Docker containers

An instance of a container is created when you run the Docker image. You can use the same Docker image to run as many containers as you want. It is an important component of the Docker ecosystem. Docker runs containers in an isolated environment.

An additional layer called a container layer, gets automatically created on top of the existing image layers when the developer runs a container. A Docker container has its own read and write layer, which allows developers to make changes that are specific to that container. Suppose you are running three containers using the same Docker image, and you install another version of the python package inside a running container. This will not affect the existing version of the python package in other containers. Docker manages the data within the Docker container using Docker Volumes.

All the files that you created in an image or a container are part and parcel of the Union file system. However, the data volume is part of the Docker host file system, and it is simply mounted inside the container.

It is initialized when the container is created. By default, it is not deleted when the container is stopped. Data volumes can be shared across containers too and can be mounted in read-only mode as well.

The command to check all the running containers is `docker ps`.

The command to check all the running and stopped containers is `docker ps -a`.

# ## Detached mode

To run Docker in the background, run the container in detached mode. You can use the `-d` flag to run the container in detached mode.

# # Docker container networking

Typically, a Docker host comprises multiple Docker containers. Docker containers also need to interact and collaborate with local as well as remote ones to come out with distributed applications. The bridge network is the default network interface that Docker Engine assigns to a container.

```
docker network ls
```

This command will show you the list of networks and their scope. The output contains the following headers:

```
NETWORK ID, NAME, DRIVER, SCOPE
```

To check the network details of any Docker container, use the following command, followed by the network ID: