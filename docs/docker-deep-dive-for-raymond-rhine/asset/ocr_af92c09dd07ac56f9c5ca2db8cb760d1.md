The next instruction runs a COPY ./src command to copy the app code into the image. The previous instruction scored a cache hit, meaning Docker can check if it has a cached layer built by running a COPY ./src against the AAA layer. If it has a cached layer for this, it links to the layer and proceeds to the next instruction. If it doesn’t have a cached layer, it builds and invalidates the cache for the rest of the build.

This process continues for the rest of the Dockerfile.

It’s important to understand a few things.

Any time an instruction results in a cache miss, the cache is invalidated and no longer checked for the rest of the build. This means you should write your Dockerfiles so that instructions most likely to invalidate the cache near the end of the Dockerfile. This allows builds to benefit from the cache for as long as possible.

You can force a build to ignore the cache by running docker build --no-cache option.

It’s also important to understand that COPY and ADD instructions include logic to ensure the content you’re copying into the image hasn’t changed since the last build. For example, you might have a cached layer that Docker built by running a