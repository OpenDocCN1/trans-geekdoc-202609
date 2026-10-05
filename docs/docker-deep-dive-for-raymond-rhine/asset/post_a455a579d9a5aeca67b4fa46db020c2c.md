
# nslookup command again.

```
docker > install bind
Tip: You can install any package available at: https://search.nix
installing 'bind-9.18.19'
<Snip>

docker > nslookup nigelpoulton.com
Server:       192.168.65.7
Address:      192.168.65.7#53

Non-authoritative answer:
Name:               nigelpoulton.com
Address:      192.124.249.126
```

The command worked, and nslookup is now installed in your toolbox and will be available in future Docker Debug sessions.

Congratulations, you've used Docker Debug to attach to a running container and run troubleshooting commands that aren't part of the container. You've also seen how to install additional tools to your Docker Debug toolbox. Remember, any changes you make to running containers are immediately visible to the container and persist after you close the session.

Type exit to terminate the debug session and return to your local shell.

Run the following command to create a new Docker Debug session that debugs the nigelpoulton/ddd-book:web0.1 image. Docker will automatically pull the image from Docker Hub if you don't have a local copy.

```
$ docker debug nigelpoulton/ddd-book:web0.1
```

![](img/aae0230bf8529bd80767c4c780dca8d3_161_0.png)

> Note: This is a sandbox shell. All changes will not affect the actual Version: 0. root@3f5b281b914b /src [nigelpoulton/ddd-book:web0.1] dockerer >

Notice the different message this time. Debugging images creates a sandbox shell and changes won't affect the actual image. This reminds you that debugging images and stopped containers behaves differently from debugging running containers:

- Changes made while debugging a live container are persisted
- Changes made while debugging images or stopped containers are deleted when you quit the debug session

Run an nslookup command to prove the tool is saved to your toolbox and available for use without re-installing.

```
docker > nslookup craigalanson.com
Server: 192.168.65.7
Address: 192.168.65.7#53

Non-authoritative answer:
Name: craigalanson.com
Address: 198.185.159.144
<Snip>
```

Docker Debug has a built-in entrypoint command that lets you print, lint, and test an image or container's Entrypoint or Cmd command. These are the commands Docker executes to start the container's app.

Run the following entrypoint command to reveal the default command this container will run when it starts.

```
docker > entrypoint --print
node ./app.js
```

The entrypoint command is clever enough to look for Entrypoint and Cmd instructions.

Type exit to quit the debug session.

In summary, Docker Debug is a new tool for debugging slim images and containers. It gets you access to containers and images that don't include a shell, and you can run troubleshooting tools that aren't available in the container or image. Any changes you make to running containers take immediate effect and persist across stop and restart operations. However, changes made while debugging images and stopped containers are lost when you close the session. In all cases, the tools you install and use are never part of the container or image.

# Self-healing containers with restart policies

Container restart policies are a simple form of self-healing that allows the local Docker Engine to automatically restart failed containers.

You apply restart policies per container, and Docker supports the following four policies:

- no (default)
- on-failure
- always
- unless-stopped

| Restart | Non- | Zero | docker | when |
|---|---|---|---|---|
| | | stop | Daemon | |
| | exit code | exit code | command restarts |
| no | N | N | N | N |
| on-failure | Y | N | N | Y |
| always | Y | Y | N | Y |
| unless-stopped | Y | Y | N | N |

Non-zero exit codes indicate a failure occurred. Zero exit codes indicate the container exited normally without an error.

We'll demo some examples, but you should also do your own testing.

Let's demonstrate the **always** policy by starting a new interactive container with the **--restart always** flag and telling it to run a shell process. We'll then type **exit** to kill the shell process **and** the container to see what happens.

Run the following command to start an interactive container called **neversaydie** with the **always** restart policy.

```
$ docker run --name neversaydie -it --restart always alpine sh #
```

Your terminal will automatically connect to the shell process inside the container.

Type **exit** to kill the shell process and return to your local terminal. This will cause the container to exit with a zero exit code, indicating a normal exit without any failures.

According to the previous table, the **always** restart policy should automatically restart the container.

Run a `docker ps` command to see if this happened.

| CONTAINER ID | IMAGE | COMMAND | CREATED | STATUS |
|---|---|---|---|
| 193362830bb | alpine | "sh" | 15 seconds | Up 2 seconds |

The container is running as expected. However, because you killed it 15 seconds ago, it has restarted. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart.

167

1. You start a new container with the `always` policy
2. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart.
3. You stop the container with `docker stop`
4. It's important to know that if you force Docker to stop, it won't restart. It's important to know that if you force Docker to stop, it won't restart.

You can also delete containers and images with the following:

```
$ docker rm $(docker ps -aq) -f
ac16541921f
5bd3741185fa

$docker rmi $(docker images -q)
Untagged: nigelpoulton/ddd-book:web0.1
Deleted: sha256:3f5b281b914b1e39df8a1fc189270a567ff99ebaeba2c8672bd
Untagged: ubuntu:24.04
Deleted: sha256:ff0b5139e74bb0dee9ca8b5724d69ea2795deb8dc4c8672
Untagged: alpine:latest
Deleted: sha256:c5b1261d6d3e43071626931fc004f70149eba2c8672
```
