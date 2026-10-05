Both modes respect node availability and will only deploy replicas to eligible nodes. For example, if you don't allow your swarm to deploy applications to managers, both modes will only deploy to workers.

If you want to deploy a global service, you need to pass the -- mode global flag to the docker service create command. Obviously, it doesn't support the --replicas flag, as it always deploys a single replica on each available node.

# Scaling services

Another powerful feature of services is the ability to scale them up and down by adding or removing replicas.

Assume business is booming and you're experiencing double the number of requests to your web front-end. Fortunately, you can easily scale the number of replicas with the docker service scale command.

Run the following command to scale the web-fe service from 5 to 10 replicas.

```
$ docker service scale web-fe=10
web-fe scaled to 10
overall progress: 10 out of 10 tasks
1/10: running [================================================================]
```