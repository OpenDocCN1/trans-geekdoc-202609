![](bbox=[0.246, 0.106, 0.752, 0.426])

Figure 6.6: Docker stack

# Docker objects

While working with Docker, you can create and use Docker objects like images, containers, volumes, and networks. In this chapter, you are going to learn about some of these objects.

# Dockerfile

Dockerfile can be considered as a set of commands or instructions that enables developers to build Docker images. These commands or instructions get executed sequentially. It is a plain text document with no extension.

# Docker image

To create a Docker container, a Docker image needs to be created. It stores all the code and dependencies required to run the application and acts as a template to run a container instance. A Docker image can be uploaded on the Docker hub, from where it can be pulled to the server or system to run the container.

To view the list of available Docker images, execute the following command in the terminal:

```
docker images
```