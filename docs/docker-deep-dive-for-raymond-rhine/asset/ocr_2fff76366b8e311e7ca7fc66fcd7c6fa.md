SIGNED TAG DIGEST SIGNERS
signed 30e6d35703c578ee...4fcbbbb0f281 nigel

List of signers and their keys for nigerpoulton/ddd-trust:signed
SIGNER KEYS
igel 4d6f1bf55702

Administrative keys for nigerpoulton/ddd-trust:signed
Repository Key: 5e72e54afafb8444f...6b27444b32010ad22
Root Key: 40418fc47544ca630...69a2cb89028c22092

You can export the **DOCKER_CONTENT_TRUST** variable with a value of **1** to force a Docker host to sign and verify all images.

```
$ export DOCKER_CONTENT_TRUST=1
```

Once enabled, you won’t be able to pull and work with unsigned images.

Test it by trying to pull an unsigned image.

```
$ docker pull nigerpoulton/ddd-book:web0.2
Error: remote trust data does not exist for docker.io/nigerpoulton does not have trust data for docker.io/nigerpoulton/ddd-book
```

You can no longer pull images without trust data!