compromise your cluster. For example, a malicious actor with access to an old manager node may be able to re-join it to the swarm and gain unwanted access.

Fortunately, you can use Swarm's *autolock* feature to force restarted managers to present a key before being admitted back into the swarm.

You can autolock new swarms at build time by passing the --autolock flag to the `docker swarm init` command. For existing swarms, you can autolock them with the `docker swarm update` command.

Run the following command from one of your swarm managers to lock your existing swarm cluster.

```
$ docker swarm update --autolock=true
Swarm updated.
To unlock a swarm manager after restarts, run the `docker swarm unlock-key` provide the following key:

WMKEY-1-XDeU3XC75Ku7rvGvIxJ0vV7ehdVJGgVIAvq0D8VuEAEaw
```

Please remember to store this key in a password manager...

While it's possible to run a `docker swarm unlock-key` command on any manager to view your unlock key, you should