The daemon communicates with containerd via a CRUD-style API over gRPC.

Despite its name, even containerd cannot create containers. It converts the required Docker image into an OCI bundle and tells runc to use this to create a new container.

runc interfaces with the OS kernel to pull all the constructs necessary to create a container (namespaces, cgroups, etc.). The container is started as a child process of runc, and as soon as the container starts, runc exits.

Figure 5.3 summarizes the process.

![](bbox=[0.143, 0.549, 0.804, 0.883])