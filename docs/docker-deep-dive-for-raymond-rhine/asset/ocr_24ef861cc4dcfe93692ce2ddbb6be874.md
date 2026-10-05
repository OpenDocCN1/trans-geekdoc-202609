Let’s test the setup to see if it works.

Create a new container called web running NGINX on port 80 and map it to port 5005 on the Docker host. If you’re still logged on to the container from the previous example, you’ll need to type exit first.

```
$ docker run -d --name web \
n--network localnet \
n--publish 5005:80 \
nnginx
```

Verify the port mapping.

```
$ docker port web
80/tcp -> 0.0.0.0:5005
80/tcp -> [::]:5005
```

The output shows the port mapping exists on all interfaces on the Docker host.

You can test external access by pointing a web browser to the Docker host on port 5005 . You’ll need to know the IP or DNS name of your Docker host (if you’re following along on Multipass it will probably be your Multipass VM’s 192.168.x.x address). You’ll see the Welcome to nginx! page.