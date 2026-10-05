Encrypting the data plane will keep the application traffic private, but it incurs a performance penalty that varies based on factors such as traffic type and traffic flow. It's not uncommon for the performance penalty to be around 10%, but you should perform your own testing against your own applications.

The stack also publishes the web-fe service on port 5001 on the swarm-wide ingress network and maps it back to port 8080 on all service replicas. This allows external clients to reach the service by hitting any swarm node on port 5001.

```
services:
web-fe:
<Snip>
ports:
  target: 8080      <-- Service replicas listen on this
  published: 5001   <-- and are published externally on
```

Let's look at the volumes and mounts.

# Volumes and mounts

The app defines a single volume called counter-vol and mounts it into the /app directory on all web-fe replicas. This means all reads and writes to the /app folder will be read and written to the volume.