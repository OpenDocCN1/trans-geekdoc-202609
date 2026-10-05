Notice how the pull looks the same as it did with Docker Hub. This is because GHCR supports the OCI registry-spec and implements the Docker Registry v2 API.

# Images with multiple tags

You can give a single image as as many tags as you want.

At first glance, the following output might look like it's listing three images. However, on closer inspection it's just two — the **b4210d0aa52f** image is tagged as **latest** and **v1**.

```
$ docker images
REPOSITORY             TAG      IMAGE ID        CREATED
igelpoulton/tu-demo  latest   b4210d0aa52f  2 days ago
igelpoulton/tu-demo  v1       b4210d0aa52f  2 days ago
igelpoulton/tu-demo  v2       6ba12825d092  12 minutes ago
```

This is a great example of the **latest** tag not relating to the newest image in the repo. In this example, the **latest** tag refers to the same image as the **v1** tag, which is actually older than the **v2** image.

# Images and layers