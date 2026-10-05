The docker inspect command is great for getting detailed image information.

You can also use the docker history command to inspect an image and see its layer data. However, this command shows the build history of an image and is not a strict list of layers in the final image. For example, some Dockerfile instructions ( ENV, EXPOSE, CMD, and ENTRYPOINT ) only add metadata and don't create layers.

Base layers

All Docker images start with a base layer, and every time you add new content, Docker adds a new layer.

Consider the following oversimplified example of building a simple Python application. Your corporate policy mandates all applications be built on top of the official Ubuntu 24:04 image. This means the official Ubuntu 24:04 image will be the base layer for this app. Installing Python will add a second layer, and your application source code will add a third. The final image will have three layers, as shown in Figure 6.8. Remember, this is an oversimplified example for demonstration purposes.