access from different environments.

Figure 6.2 shows the central nature of registries in the build > ship > run pipeline.

![](bbox=[0.168, 0.287, 0.751, 0.404])

Figure 6.2

Most modern registries implement the OCI distribution-spec, and we sometimes call them *OCI registries*. Most registries also implement the Docker Registry v2 API, meaning you can use the Docker CLI and other API tools to query them and work with them in standard ways. Some offered advanced features such as image scanning and integration with build pipelines.

The most common registry is Docker Hub, but others exist, including 3rd-party internet-based registries and secure on-premises registries. However, as previously mentioned, Docker is opinionated and will default to Docker Hub unless you tell it