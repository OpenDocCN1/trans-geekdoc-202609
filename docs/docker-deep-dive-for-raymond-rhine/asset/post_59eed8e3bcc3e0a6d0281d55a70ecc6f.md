
Run the following command to verify your **test** container is still running.

| CONTAINER ID | IMAGE | COMMAND | CREATED | STATUS | NAME |
|---|---|---|---|---|--|
| bbd2e5ad1817 | ubuntu:latest | "/bin/bash" | 7 mins | Up 7 min | test container |

The output shows your **test** container, and you can see it was created 7 minutes ago and has been running for 7 minutes.

**Execute a command inside the container**

You can use the **docker attach** command to attach your shell to the container’s main process.

Run the following command to attach your shell to the Bash process inside the container.

```
$ docker attach test
root@bbd2e5ad1817:/#
```

Make sure your shell prompt changes, indicating you successfully connected to the container.

Exit the container again by typing **Ctrl-C** and verify your shell prompt reverts to your local machine.

# Delete the container

Run another **docker ps** to verify your container is still running.

| CONTAINER ID | IMAGE | COMMAND | CREATED | STATUS | NAMES |
| bbd2e5ad1817 | ubuntu:latest | "/bin/bash" | 9 mins | Up 9 min | test |

Stop and kill the container using the **docker stop** and **docker rm** commands.

```
$ docker stop test
test
```

It can take a few seconds for the container to stop.

```
$ docker rm test
test
```

Verify the container was successfully deleted by running the **docker ps** command with the **-a** flag to list all containers, even those in the stopped state.

```
$ docker ps -a
CONTAINER ID | IMAGE | COMMAND | CREATED | STATUS | PORTS
```

Congratulations, you’ve pulled a Docker image, started a container from it, logged in to it, executed a command inside it, stopped it, and deleted it.

# The Dev Perspective

Containers are all about applications.

You’ll complete all of the following steps in this section:

- Clone an app from a GitHub repo
- Inspect the app’s Dockerfile
- Containerize the app
- Run the app as a container

Run the following command to make a local clone of the repo. This will copy the application code to your machine so you can containerize it in a future step. You’ll need the git CLI for this to work.

```
$ git clone https://github.com/nigelpoulton/psweb.git
Cloning into 'psweb'...
remote: Enumerating objects: 63, done.
remote: Counting objects: 100% (34/34), done.
remote: Compressing objects: 100% (22/22), done.
remote: Total 63 (delta 13), reused 25 (delta 9), pack-reused 29
```

Receiving objects: 100% (63/63), 13.29 KiB | 4.43 MiB/s, done.
Resolving deltas: 100% (21/21), done.

Change into the psweb directory and list its contents.

```
$ cd psweb
$ ls -l
total 32
-rw-r--r-- 1 nigelpoulton staff 324 5 Feb 12:31 Dockerfile
-rw-r--r-- 1 nigelpoulton staff 378 5 Feb 12:31 README.md
-rw-r--r-- 1 nigelpoulton staff 341 5 Feb 12:31 app.js
-rw-r--r-- 1 nigelpoulton staff 355 5 Feb 12:47 package.json
drwxrxr-xr-x 3 nigelpoulton staff 96 5 Feb 12:31 views
```

The app is a simple Node.js web app running some static HTML.

Inspect the app’s Dockerfile. The Dockerfile is a plain-text document that tells Docker how to build it.

```dockerfile
FROM alpine
LABEL maintainer="nigelpoulton@hotmail.com"
RUN apk add --update nodejs npm
COPY . /src
WORKDIR /src
RUN npm install
EXPOSE 8080
ENTRYPOINT ["node", "app.js"]
```

Right now, all you need to know is that each line in the Dockerfile represents an instruction to build the image.

List the contents of the Dockerfile.

```bash
$ cat Dockerfile
```

# Containerize the app

Run the following command to create an image based on the instructions in the Dockerfile. If you're following along, run:

```
$ docker build -t test .
[+] Stage 1/1 : FROM alpine
[+] Stage 1/1 : LABEL maintainer="nigelpoulton@hotmail.com"
[+] Stage 1/1 : RUN apk add --update nodejs npm
[+] Stage 1/1 : COPY . /src
[+] Stage 1/1 : WORKDIR /src
[+] Stage 1/1 : RUN npm install
[+] Stage 1/1 : EXPOSE 8080
[+] Stage 1/1 : ENTRYPOINT ["node", "app.js"]
Successfully built bbd2e5ad1817
docker: test: bbd2e5ad1817
```

Congratulations, you’ve pulled a Docker image, started a container from it, logged in to it, executed a command inside it, stopped it, and deleted it.

# The Dev Perspective, we’ll look under the hood of the Docker Engine.

This chapter has a strong operations focus, and you can use Docker without knowing everything you’re about to learn. However, to truly master something, you need to understand what’s going on under the hood. So, if you want to master Docker, you should read this chapter.

I’ve divided the chapter into the following sections:

- Docker Engine – The TLDR
- The Docker Engine
- The influence of the Open Container Initiative (OCI)
- runc
- containerd
- Starting a new container (example)
- What’s the shim all about
- How it’s implemented Linux

Let’s learn about the Docker Engine.

# Docker Engine – The TLDR

Docker Engine is jargon for the server-side components of Docker that run and manage containers. If you’ve ever worked with VMware, the Docker Engine is similar to ESXi.

The Docker Engine is modular and built from many small specialized components pulled from projects such as the OCI, the CNCF, and the Moby project.

In many ways, the Docker Engine is like a car engine:

- A car engine is made from many specialized parts that work together to make a car drive — intake manifolds, throttle bodies, cylinders, pistons, spark plugs, exhaust manifolds, and more.
- The Docker Engine is made from many specialized tools that work together to create and run containers — the API, image builder, high-level runtime, low-level runtime, shims, and etc.

Figure 5.1 shows the components of the Docker Engine that create and run containers. Other components exist, but this simplified diagram focuses on the components that start and run containers.
