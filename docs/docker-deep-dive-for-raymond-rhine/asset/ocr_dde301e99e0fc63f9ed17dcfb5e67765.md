Run the following command to create a new Docker Debug session that debugs the nigelpoulton/ddd-book:web0.1 image. Docker will automatically pull the image from Docker Hub if you don't have a local copy.

```
$ docker debug nigelpoulton/ddd-book:web0.1
```

![](bbox=[0.125, 0.357, 0.403, 0.413])

> Note: This is a sandbox shell. All changes will not affect the actual Version: 0. root@3f5b281b914b /src [nigelpoulton/ddd-book:web0.1] dockerer >

Notice the different message this time. Debugging images creates a sandbox shell and changes won't affect the actual image. This reminds you that debugging images and stopped containers behaves differently from debugging running containers:

+   - Changes made while debugging a live container are persisted