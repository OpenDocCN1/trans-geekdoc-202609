The command output includes a **docker swarm join** command. Copy this command and run it **node2**.

```
$ docker swarm join \
  --token SMTKN-1-0hz2ec...2vye \
  172.31.1.5:2377
This node joined a swarm as a worker.
```

You now have a two-node Swarm with **node1** as a manager and **node2** as a worker.

Create a new overlay network

Let's create a new encrypted overlay network called **uber-net**.

Run the following command from your manager node **(node1)**.

```
$ docker network create -d overlay -o encrypted uber-net
dvulyly429jvt04hgdm0mjqcc6
```

That's it. You've created a brand-new encrypted overlay network. The network spans both nodes in the swarm and Docker uses TLS to encrypt it (AES in GCM mode). It also rotates the encryption keys every 12 hours.

If you don't specify the **-o encrypted** flag, Docker will still encrypt the control plane (management traffic) but won't