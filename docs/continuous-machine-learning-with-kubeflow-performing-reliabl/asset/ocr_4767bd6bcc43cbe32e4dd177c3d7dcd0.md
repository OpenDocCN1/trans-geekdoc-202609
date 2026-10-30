To get a base image. Just like you need an OS as a basis of your application.

To show the message about the author of this image.

To set an environment variable to a certain value.

To execute the command requirements file which contains the Python libraries.

To let your container listen on the specific port while running.

**WORKDIR/** To set the working directory, copy new files/directories.

To provide default actions when executing the container.

Change the permission of **heroku_startup.sh** or you will receive the permission denied error while executing

**ENTRYPOINT** To tell the Docker to execute heroku_startup.sh when starting the container.

The purpose of the second and the third RUN Command in the preceding line is to let OpenCV run normally in Docker to mitigate an issue that if we don’t install libSM.so.6 and import OpenCV when building the Docker Image, our container will