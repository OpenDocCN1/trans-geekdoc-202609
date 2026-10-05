+   - SWMTKN-1-<hash-of-cluster-certificate>--<manager-join-token>

Copy the command and run it on mgr2:

```
$ docker swarm join --token SWMTKN-1-1dmtwu...r17stb-2axi5...8p7g

This node joined a swarm as a manager.
```

List the nodes in your swarm.

| ID | HOSTNAME | STATUS | AVAILABILITY | MANAGER STATUS |
|---|---|---|---|--|
| 7xamk...ge662z | mgr1 | Ready | Active | Leader |
| i0ue4...zcjm7f * | mgr2 | Ready | Active | Reachable |

Now you have a two-node swarm with mgr1 and mgr2 as managers. Both have access to the cluster store and are configured with client certificates for mutual TLS.

In the real world, you'll always run three or five managers for high availability.

Figure 16.5 shows the updated swarm with both managers.