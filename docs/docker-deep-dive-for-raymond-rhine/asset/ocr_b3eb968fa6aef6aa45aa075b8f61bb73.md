repo.

The following refers command signs a local image called **nigelpoulton/ddd-trust:signed** and pushes it to Docker Hub. Your image will have a different name and you'll push it to a different repo.

```
$ docker trust sign nigelpoulton/ddd-trust:signed
Signing and pushing trust data for local image nigelpoulton/ddd-t
The push refers to repository [docker.io/nigelpoulton/ddd-trust]
6495b414566f:7ef8b: Mounted from nigelpoulton/ddd-book
79867f7ef8b: Mounted from nigelpoulton/ddd-book
bca2a409639: Mounted from nigelpoulton/ddd-book
28ad2149d870: Mounted from nigelpoulton/ddd-book
4f4fb700ef54: Mounted from nigelpoulton/ddd-book
5elfc7f5df34: Mounted from nigelpoulton/ddd-book
signed: sha256:b65f91aa4e670bbafad0fbb91281ea95f9cdc7528a
Signing and pushing trust metadata
Enter passphrase for nigel key with ID 92330ea:
Successfully signed docker.io/nigelpoulton/ddd-trust:signed
```

The push operation creates the repo on Docker Hub and then signs and pushes the image. You can view the repo on Docker Hub, and you can run the following command to inspect its signing data.

```
$ docker trust inspect nigelpoulton/ddd-trust:signed --pretty

Signatures for nigelpoulton/ddd-trust:signed
```