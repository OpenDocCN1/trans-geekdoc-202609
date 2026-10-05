not much app stuff. When this build stage completes, it outputs a large image that later stages can use.

The **build-client** stage doesn't pull a new image. Instead, it uses the `FROM base AS build-client` instruction to use the intermediate image created by the **base** stage. It then issues a **RUN** instruction to compile the client app into a binary executable. The goal of this stage is to create an image with the compiled `client` binary that can be referenced by later stages.

The **build-server** stage does the same for the **server** component and outputs a similar image for use by later stages.

The **prod** stage pulls the minimal **scratch** image. It then runs two `COPY --from` instructions to copy the compiled `client app` from the **build-client** stage and the compiled `server app` from the **build-server** stage. It then tells Docker to run the server app when it's started as a container. This stage outputs the final production image containing just the client and server binaries inside a tiny scratch image and the metadata telling Docker how to start the app.

The builder will run the **base** stage first, then run the **build-client** and **build-server** stages in parallel, and finally run the **prod** stage.