You can also connect a browser to port 5005 on your Docker host to test the app. If you're using Docker Desktop, point your browser to localhost:5005. If you're not running Docker Desktop, you may need to substitute localhost with the name or IP of the host Docker is running on.

![](bbox=[0.218, 0.318, 0.781, 0.532])

Figure 7.4 - Web app running on container

Congratulations. Docker pulled a local copy of the image and started a container running the app defined in the image.

# How containers start apps

In the previous section, you created a container running a web app. But how did the container know which app to start and how to start it?