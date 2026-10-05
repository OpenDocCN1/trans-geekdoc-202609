Run the following command from the node you want to be the first manager. We'll run the example from mgr1.

```
$ docker swarm init
Swarm initialized: current node (7xam...662z) is now a manager.
```

That's it! You've configured a secure swarm with a cryptographic cluster ID, an encrypted cluster store, a certificate authority with a 90-day certificate rotation policy, a set of secure join tokens to use when adding new managers and workers, and configured the current manager with a client certificate for mutual TLS — all with a single command!

Figure 16.4 shows the current swarm configuration. Some of the details may be different in your lab.

![](bbox=[0.246, 0.668, 0.663, 0.781])

Figure 16.4