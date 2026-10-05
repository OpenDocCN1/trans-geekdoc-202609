new container called ctr1 based on the nginx image.

```
$ docker run -d --name ctr1 nginx
```

Run a docker ps command to see if the container is running.

| CONTAINER ID | IMAGE | COMMAND | CREATED |
|--- | --- | --- | --- |
| 9cfb0c9aacb2 | nginx | "/docker-entrypoint..." | 9 seconds ago |

When you run commands like this, the Docker client converts them into API requests and sends them to the API exposed by the daemon.

The daemon can expose the API on a local socket or over the network. On Linux, the local socket is /var/run/docker.sock and on Windows it's \pipe\docker_engine.

The daemon receives the request, interprets it as a request to create a new container, and passes it to containerd. Remember that the daemon no longer contains any code to create containers.