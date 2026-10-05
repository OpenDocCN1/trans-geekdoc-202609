# 10: Docker Swarm

Now that you know how to install Docker, pull images, and work with containers, the next logical step is to do it all at scale. That's where Docker Swarm comes into play.

I've split the chapter into the following main parts:

+   - Docker Swarm – The TLDR
- Swarm primer
- Build a secure Swarm cluster
- Deploy and manage an app on swarm
- Service logs
- The commands

# Docker Swarm – The TLDR

Docker Swarm is two things:

+   1. An enterprise-grade cluster of Docker nodes
2. An orchestrator of microservices apps

On the clustering front, Swarm groups one or more Docker nodes into a cluster. Out of the box, you get an encrypted distributed cluster store, encrypted networks, mutual TLS, secure cluster join tokens, and a PKI that makes managing and