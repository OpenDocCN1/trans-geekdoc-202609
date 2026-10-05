Once the build is complete, check that you have an image called test:latest.

| REPO | TAG | IMAGE ID | CREATED | SIZE |
|---|---|---|---|---|n| test | latest | 0435f2738cf6 | 21 seconds ago | 160MB |

Congratulations, you've containerized the app. That's jargon for building it into a container image that contains the app and dependencies.

# Run the app as a container

Run the following command to start a container called web1 from the image. If you're on a Windows machine, you'll need to replace the backslashes with backticks or run the command on a single line without the backslashes.

```
$ docker run -d \
--name web1 \
--publish 8080:8080 \
test:latest
```

Open a web browser and navigate to the DNS name or IP address of your Docker host on port 8080. If you're following along on Docker Desktop, connect to localhost:8080 or 127.0.0.1:8080. If you're following along on Multipass,