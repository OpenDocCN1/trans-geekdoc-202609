# 1.1.1 Dockerfile

To get our Python or any language code running in a container is to warp it in a package as a Docker image, after that run a container based on it. The steps are sketched as follows:

![](bbox=[0.12, 0.34, 0.88, 0.48])

Figure 1.2: Docker file process

Next, for generating a Docker image, we need to create a Dockerfile which contains some set of instructions needed to build the image. The Dockerfile is then processed by the Docker builder which generates the Docker image. At last, with a simple Docker run command, we can create and run a container with the Python service.