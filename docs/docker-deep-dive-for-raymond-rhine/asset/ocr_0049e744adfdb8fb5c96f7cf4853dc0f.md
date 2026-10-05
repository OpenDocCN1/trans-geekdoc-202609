command, or you can specify it when performing individual builds.

The following command uses the --builder flag to use the cloud-nigelpoulton-ddd cloud builder to build the same images in the previous steps. Remember to use your own cloud builder if you're following along.

```
$ docker buildx build \
  --builder=cloud-nigelpoulton-ddd \
  --platform=linux/amd64,linux/arm64 \\
  -t nigelpoulton-ddd-book:ch8.1 --push

=> [internal] connected to docker build cloud service <Snip>
```

At the time of writing, Build Cloud supports various AMD and ARM architectures, whereas the docker-container driver supports more but is slower and less reliable.

# A few good practices

Let's finish the chapter with a few best practices. This isn't a full list, and the advice applies to local and cloud builds.

# Leverage the build cache