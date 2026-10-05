# $ docker pull <repository>:<tag>

The example from earlier pulled the Redis image with the following command. It pulled the image tagged as latest from the top-level redis repository.

```
$ docker pull redis:latest
```

The following examples show how to pull a few different official images.

```
$ docker pull mongo:7.0.5
//Pulls the image tagged as '7.0.5' from the official 'mongo' repository

$ docker pull busybox:glibc
//Pulls the image tagged as 'glibc' from the official 'busybox' repository

$ docker pull alpine
//Pulls the image tagged as 'latest' from the official 'alpine' repository
```

A couple of things are worth noting.

+   - As previously mentioned, if you don't specify an image tag after the repository name, Docker assumes you want the image tagged as latest. The command will fail if the repository has no image tagged as latest.