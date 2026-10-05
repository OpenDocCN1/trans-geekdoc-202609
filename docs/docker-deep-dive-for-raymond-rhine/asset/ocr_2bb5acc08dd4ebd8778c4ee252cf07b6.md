```
<Snip>
linux/amd64/v3
```

Notice how the first builder supports more platforms than the cloud builder. This is because the docker-container driver utilizes QEMU to emulate target hardware. It usually works but can be slow.

The second builder is Docker’s Build Cloud, which only supports AMD and ARM builds. Builds running in Build Cloud run on native hardware and offer a shared cache so that teammates can share a common cache for even faster builds. Complex builds can be much quicker when executed on native hardware such as Build Cloud.

Run a docker buildx inspect command against one of your builders.

```
$ docker buildx inspect cloud-nigelpoulton-ddd

Name: cloud-nigelpoulton-ddd
Driver: cloud
Nodes:
Name: linux-arm64
Endpoint: cloud://nigelpoulton-ddd_linux-arm64
Status: running
Buildkit: v0.12.5
Platforms: linux/arm64*
Labels:
```