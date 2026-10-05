If you pull an application container; such as nginx:latest , you'll get an image with a minimal OS and the code to run the NGINX app.

# Start a container from the image

If you've been following along, you'll have a copy of the ubuntu:latest image on your Docker host, and you can use the docker run command to start a container from it.

Run the following docker run command to start a new container called test from the ubuntu:latest image.

```
$ docker run --name test -it ubuntu:latest bash
root@bbd2e5ad1817:#
```

Notice how your shell prompt has changed. This is because the container is already running and your shell is attached to it.

Let's quickly examine that docker run command.

docker run tells Docker to start a new container. The --name flag told Docker to call this container test. Next, the -it flags told Docker to make the container interactive and to attach your shell to the container’s terminal. After that, the command told Docker to base the container on the ubuntu:latest