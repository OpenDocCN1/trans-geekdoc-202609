
![](img/aae0230bf8529bd80767c4c780dca8d3_131_0.png)

In this example, each container has its own thin R/W layer shares the same image. The containers can see and access the files and apps in the image *through* their own R/W layer, and if they make any changes, these get written to their R/W layer. When you stop a container, Docker keeps the R/W layer and restores it when you restart the container. However, when you delete a container, Docker deletes its R/W layer. This way, each container can make and keep its own changes without changing the shared image.

## Docker is running

Run `docker version` to check Docker is running. It checks the CLI and engine components.

```
$ docker version
Client:  v24.0.7
API version: v1.43
OS/Arch:  darwin/arm64
Server: Docker Desktop 4.30.0
Engine: 26.1.1
API version: 1.45
OS/Arch: linux/64
```

As long as you get a response from Client and Server, you’re good to go and can skip the next section. If you get an error, this usually means your Docker daemon isn’t running or your user account doesn’t have permission to access it. If you’re running on Linux, you’ll need to ensure your user account is a member of the docker group. If it isn’t, you can add it by running usermod -aG docker <username> and restarting your shell. Alternatively, you can prefix all docker commands with sudo to access the API socket /var/run/docker.sock.

If your user account is already a member of the docker group and you still get an error from the daemon, there's a good chance Docker isn't running. Run one of the following commands to check the status of the daemon on Linux systems using Systemd:

```
$ service docker status
$ systemctl is-active docker
```

If the daemon isn't running, start it with the appropriate command for your system.

## Starting a container

The docker run command is the simplest and most common way to start a new container. Run the following command to start a new container called webserver:

```
$ docker run -d --name webserver -p 5005:8080 ngelpoulton/ddd-book
unable to find image 'nigelpoulton/ddd-book:web0.1' locally
web0.1: Pulling from ngelpoulton/ddd-book
4f4fb70ef54: Already exists
c2fa07f3ff77: Download complete
0a1f0c11ea9: Download complete
claf4b5db42: Download complete
digest: sha256:3f5b281b914b39df8a1fbc189270a5672ff9e98bf0319
status: Downloaded newer image for ngelpoulton/ddd-book:web0.1
b5594b3b8b3bfdce544d2ca048e340d176be9c9fdc43081a20f1852c395e96b
```

Let's take a closer look at the command and the output.

- **docker run** tells Docker to run a new container
- The **-d** flag tells Docker to run it in the background as a daemon process and detached from your local terminal
- The **name** flag tells Docker to name this container **webserver**.
- The **-p 5005:8080** flag maps port **5005** on your local system to port **8080** inside the container. This works because the container’s web server is listening on port **8080**.

The `nigelpoulton/ddd-book:web0.1` argument tells Docker which image to use to start the container. When you hit **Return**, the Docker client converted the command into an API request and posted it to the Docker daemon. The Docker daemon accepted the command and searched its local image repository for a copy of the `nigelpoulton/ddd-book:web0.1` image. It didn’t find one, so it searched Docker. In the example, it found one on Docker Hub and pulled a local copy.

Once it had a local copy of the image, the daemon made a request to containerd asking for a new container. containerd then instructed runc to create the container and start the app. It also performed the port mapping.

Run the following commands to verify the image was pulled locally and a new container called **webserver** is running.

```
$ docker images
| TAG | IMAGE ID | CREATED |
| :--- | :--- | :--- | :--- |
| ngelpoulton/ddd-book | web0.1 | 3f5b281b914b | 12 minutes ago |

$ docker ps
| IMAGE | COMMAND | STATUS | PORT |
| :--- | :--- | :--- | :--- |
| b5594b3b8b3f | ngelpoulton... | "node ./app.js" | Up 2 mins | 0.0.0.0:5005 |
```

You can also connect a browser to port 5005 on your Docker host to test the app. If you're using Docker Desktop, point your browser to localhost:5005. If you're not running Docker Desktop, point your browser to the container's IP address.

![](img/aae0230bf8529bd80767c4c780dca8d3_131_0.png)

## How do containers start

In the previous section, you created a container. But how did the container know which app to start? There are three ways to start a container:

1. An Entrypoint defined in the image
2. A CMD defined in the image
3. An argument passed to the docker run command

The Entrypoint and CMD are defined in the Dockerfile, but they can be overridden when you run the container. If you specify a <command>, it will override the CMD instruction.

As mentioned, the <command> is optional; you'll learn more about these in the next chapter. The format of the docker run command is:

```
docker run <arguments> <image> <command>
```
