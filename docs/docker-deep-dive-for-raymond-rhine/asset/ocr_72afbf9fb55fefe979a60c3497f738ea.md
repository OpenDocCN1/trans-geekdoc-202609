Copying new images onto your Docker host is called pulling.
Pull the ubuntu:latest image.

```
$ docker pull ubuntu:latest
latest: Pulling from library/ubuntu
b91d887f8f44: Download complete
digest: sha256:e956c25505f33ff72e88b299087c9dcf230f23259da296
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
```

Run another docker images to confirm your pull command worked.

| REPOSITORY | TAG | IMAGE ID | CREATED | SIZE |
| ubuntu | latest | e9569c25505f | 10 days ago | 106MB |

We'll discuss the details of where the image is stored and what's inside it in later chapters. For now, all you need to know is that images contain enough of an operating system (OS) and all the code and dependencies required to run the application. The Ubuntu image you pulled includes a stripped-down version of the Ubuntu Linux filesystem and a few of the standard Linux utilities that ship with Ubuntu.