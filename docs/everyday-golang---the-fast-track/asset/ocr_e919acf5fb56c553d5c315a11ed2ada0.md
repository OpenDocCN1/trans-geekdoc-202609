```
uses: docker/build-push-action@v5
with:
  outputs: "type=registry,push=true"
  platforms: linux/amd64,linux/arm/v6,linux/arm64
  build-args: |
    Version=${{ env.TAG }}
    GitCommit=${{ github.sha }}
  tags: |
    ghcr.io/${{ env.REPO_OWNER }}/release-it:${{ github.sha }}
    ghcr.io/${{ env.REPO_OWNER }}/release-it:${{ env.TAG }}
    ghcr.io/${{ env.REPO_OWNER }}/release-it:latest
```

You can see that the build-args are populated just as when we ran docker build or buildx locally, and then we have some additional actions for setting up qemu. Qemu is used by buildx to cross compile your code to work on other machines.

The list of platforms (linux/amd64, linux/arm/v6, linux/arm64) means this container will work on Raspberry Pi OS, 64-bit Arm servers and regular Intel/AMD servers too.

If you're using ghcr.io, things are much simpler, GitHub Actions will provide a temporary token that can be used to publish images, just make sure you remember to include the permissions and packages: write sections from above so the token has the appropriate permissions. For the Docker Hub or a private registry, you'll need to create a separate pair of secrets i.e. DOCKER_USERNAME and DOCKER_PASSWORD, then update the docker/login-action@v2 step to use them instead.

Note that with GHCR, your container image may be set to private by default. You'll also need to make it public to share it, or authenticate your Docker engine or Kubernetes cluster otherwise.