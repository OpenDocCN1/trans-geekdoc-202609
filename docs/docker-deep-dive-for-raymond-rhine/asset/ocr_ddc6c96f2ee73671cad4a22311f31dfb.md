# Looking closer at the stack file

Stack files are identical to Compose files with a few differences at run-time. For example, Docker Compose lets you build images at run-time, but Docker Stacks don't.

Let's look at the networking elements defined in our stack file.

# Networks and networking

One of the first things Docker does when you deploy an app from a stack file is create the networks listed under the **networks** key. If they already exist, Docker doesn't need to do anything. But if they don't exist, it creates them.

This app defines a single encrypted overlay network called **counter-net.**

```
networks:
  counter-net:      <---- Network name
    driver: overlay   <---- Driver/type of network
    driver_opts:
      encrypted: 'yes' <---- Encrypt the data plane
```

It needs to be an overlay network so it can span all nodes in the swarm.