At a high level, there are two major parts to the Docker platform:

+   * The CLI (client)
* The engine (server)

The CLI is the familiar `docker` command-line tool for deploying and managing containers. It converts simple commands into API requests and sends them to the engine.

The engine comprises all the server-side components that run and manage containers.

Figure 2.1 shows the high-level architecture. The client and engine can be on the same host or connected over the network.

![](bbox=[0.263, 0.613, 0.651, 0.743])

Figure 2.1 Docker client and engine.