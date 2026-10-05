I've snipped the output and highlighted the subnet info and the IPs of connected containers. One thing to note is that Docker only shows you the IP addresses of containers running on the local node. For example, the output in the book only shows the IP of the first replica called test.1.tro...kgk . If you run the same command on node2 , you'll see the name and IP of the other replica.

Run the following commands on both nodes to get the local container names, IDs, and IP addresses of both replicas and make a note of them.

The ID at the end of the second command ( d776923a5a7 ) is the container ID as returned by the docker ps command. You'll need to substitute the value from your environment.

| docker ps | | IMAGE | COMMAND | CREATED | STATU |
| --- | --- | --- | --- | --- |
| d776923a5a7 | ubuntu:latest | "sleep infinity" | 2 hrs ago | Up 2 |

```
$ docker inspect \
 --format='{{{{range .NetworkSettings.Networks}}{{.IPAddress}}{{en
10.0.0.3
```

I have the following in my environment :