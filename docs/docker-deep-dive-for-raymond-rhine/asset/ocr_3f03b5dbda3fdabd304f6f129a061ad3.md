+   * Images tagged as latest are not guaranteed to be the most up-to-date in the repository.

Pulling images from unofficial repositories is almost the same as pulling from official repositories — you just need to add a Docker Hub username or organization before the repository name. The following example shows how to pull the v2 image from the tu-demo repository owned by a not-to-be-trusted person whose Docker Hub ID is nigelppoulton.

```
$ docker pull nigelppoulton/tu-demo:v2
```

To pull an image from a different registry, you just add the registry's DNS name before the repository name. For example, the following command pulls the latest image from Brandon Mitchell's regclient/regsync repo on GitHub Container Registry (ghcr.io).

```
$ docker pull ghcr.io/regclient/regsync:latest
latest: Pulling from regclient/regsync
614f2b64ccf: Download complete
7746d6728537: Download complete
685af2c79c31: Download complete
4c377311167a: Download complete
662e9541e042: Download complete
digest: sha256:149a95d473d6beed2a1404d7c3b000ddffa583a94836587ba8e33
Status: Downloaded newer image for ghcr.io/regclient/regsync:latest
ghcr.io/regclient/regsync:latest
```