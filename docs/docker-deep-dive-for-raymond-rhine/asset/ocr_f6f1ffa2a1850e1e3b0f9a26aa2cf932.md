![](bbox=[0.195, 0.105, 0.705, 0.345])

# # Run a Wasm container

Now that you’ve packaged the Wasm app as an OCI image and pushed it to a registry, you can run it as a container.

The following command runs it in a new container called wasm-ctr and maps it to port 5556 on your Docker host. The -runtime flag makes sure Docker executes the container with the spin Wasm runtime. Versions of Docker Desktop older than 4.24 may not have the spin runtime and will fail.

```
$ docker run -d --name wasm-ctr \\n--runtime=io.containerd.spin.v2 \\n--platform=wasi/wasm \
```