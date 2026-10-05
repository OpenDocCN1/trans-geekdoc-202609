images, advanced caching, and more. It's been the default build client since Docker v23.0 and Docker Desktop v4.19.

You can configure Buildx to talk to multiple BuildKit instances, and we call each instance of BuildKit a *builder*. Builders can be on your local machine, in your cloud or datacenter, or Docker's Build Cloud.

If you point buildx at a local builder, image builds will be done on your local machine. If you point it at a remote builder, such as Docker Build Cloud, builds will be done on remote infrastructure.

Figure 8.7 shows a Docker environment configured to talk to a local and a remote builder.

![](bbox=[0.175, 0.615, 0.745, 0.825])

Figure 8.7 - Docker build architecture