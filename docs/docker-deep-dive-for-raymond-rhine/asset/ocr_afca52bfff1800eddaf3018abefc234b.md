Reading the spec is also a great way to learn the details.

# Installing Compose

All modern versions of Docker come with Docker Compose pre-installed, and you no longer need to install it as a separate application.

Test it with the following command. Be sure to use the `docker compose` command instead of the older `docker-compose`.

```
$ docker compose version
Docker Compose version v2.25.0
```

# The sample app

We'll use the sample app shown in Figure 9.1 with two services, a network, and a volume.

![](bbox=[0.185, 0.698, 0.722, 0.811])

Figure9.1 - Sample app