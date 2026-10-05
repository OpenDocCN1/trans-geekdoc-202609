A few things are worth noting from the output.

The bottom few lines that I’ve snipped from the book related to the history of the `node:20.8.0-alpine` base image that was pulled by the `FROM` instruction.

All lines ending with `buildkit.docker.v0` relate to instructions from the Dockerfile used to build the image.

The `CREATED BY` column lists the exact Dockerfile instruction that created the layer or metadata.

Lines with a non-zero value in the `SIZE` column created new layers, whereas the lines with `0B` only added metadata. In this example, three lines/instructions created layers.

Run a `docker inspect` to see the list of image layers.

```
docker inspect ddd-book:ch8.node

<Snip>
"RootFS": {
  "Type": "layers",
  "Layers": [
    "sha256:5f4d9fc4c98de918202a9c81e501cc66429bc87
    "sha256:6b20c4e93dbab9786f9268bbe32c208d385f2c4
    "sha256:012c308a78ec993a47db7c7c4d17b53d8ce2649a
    "sha256:35a839ac7cc922afd896a0297e629141c77ed603
    "sha256:918caa8070410ccfb2c5b3b4d62ca66742c46bf21
```