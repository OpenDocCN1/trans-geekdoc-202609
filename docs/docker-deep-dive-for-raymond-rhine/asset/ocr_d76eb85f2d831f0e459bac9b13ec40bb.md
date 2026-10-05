```
{
  <Snip>
  "debug":true,
  "log-level": "debug",
  <Snip>
}
```

If your daemon.json file doesn't exist, create it. Also, be sure to restart Docker after making any changes to the file.

That was the daemon logs. What about container logs?

You can normally view container logs with the docker logs command. If you're running Swarm, you should use the docker service logs command. However, Docker supports a few different log drivers, and they don't all work with native Docker commands. For some of them, you might have to view logs using the platform's native tools.

json-file and journald are probably the easiest to configure and both work with the docker logs and docker service logs commands.

The following snippet from a daemon.json shows a Docker host configured to use journald.

```
{
  "log-driver": "journald"
}
```