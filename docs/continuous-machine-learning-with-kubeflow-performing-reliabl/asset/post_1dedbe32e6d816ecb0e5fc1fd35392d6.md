
### Figure 8.19: Docker Activation

Heroku provides three ways to deploy your Dockerized app. We will be using the Container Registry.

![](img/8f8a671916d96b455297952d0f37b96c_519_0.png)

![](img/8f8a671916d96b455297952d0f37b96c_519_1.png)

### Figure 8.20: Heroku Deployment Method

The Heroku Deployment folder consists of the following files:

![](img/8f8a671916d96b455297952d0f37b96c_519_2.png)

### Figure 8.21: Heroku Deployment Folder

Now, let’s create the Docker file for the Heroku Deployment.

Dockerfile:

```
FROM ubuntu:18.04
# streamlit-specific commands for config
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
RUN mkdir -p /root/.streamlit

RUN bash -c 'echo -e "\
[general]\n\
email = \"\"\n\
" > /root/.streamlit/credentials.toml'
RUN bash -c 'echo -e "\
[server]\n\
enableCORS = false\n\
" > /root/.streamlit/config.toml'

RUN apt-get update && \
apt-get install -y \
python3.7 python3-pip \
libsm6 libxext6 libxrender-dev
EXPOSE 8501
# make app directory
WORKDIR /streamlit-docker
```

- 1. streamlit
- 2. black
- 3. altair
- 4. pandas
- 5. pydeck
- 6. matplotlib
- 7. numpy
- 8. Pillow
- 9. bs4
- 10. pipenv
- 11. xlrd
- 12. opencv-python==4.2.0.34
- 13. gdown

### Figure 8.22: Heroku Docker requirements File

```
COPY requirements.txt ./requirements.txt
RUN pip3 install -r requirements.txt
COPY . .
```

### Figure 8.22: Heroku Docker requirements File

```
RUN chmod +x ./heroku_startup.sh
ENTRYPOINT "./heroku_startup.sh"
```

Let's breakdown the Docker as follows:

To get a base image. Just like you need an OS as a basis of your application.

To show the message about the author of this image.

To set an environment variable to a certain value.

To execute the command requirements file which contains the Python libraries.

To let your container listen on the specific port while running.

**WORKDIR/** To set the working directory, copy new files/directories.

To provide default actions when executing the container.

Change the permission of **heroku_startup.sh** or you will receive the permission denied error while executing

**ENTRYPOINT** To tell the Docker to execute heroku_startup.sh when starting the container.

The purpose of the second and the third RUN Command in the preceding line is to let OpenCV run normally in Docker to mitigate an issue that if we don’t install libSM.so.6 and import OpenCV when building the Docker Image, our container will silently crash with the following message: segmentation fault (core dumped) when executing.

## Heroku.yml:

```
build:
docker:
web: heroku.Dockerfile
run:
web: ./heroku_startup.sh
```

Heroku needs heroku.yml to build and deploy the Docker images, so we will create one for the usage. Obviously, the build and run sections indicate what we wanted to do in build and run in the stage on Heroku, respectively.

## Heroku_startup.sh:

```
echo PORT $PORT
streamlit run --server.port $PORT Master.py
```

Heroku uses a $PORT environment variable for the port exposure. We have to set the $PORT variable to Streamlit or your app will not appear. In this case, we will expose at 8501.

## Installation:

Now download Heroku CLI :
https://devcenter.heroku.com/articles/heroku-cli#download-and-install

Install Brew: https://brew.sh/

```
brew tap heroku/brew && brew install heroku
```

```
sudo snap install --classic heroku
```

## The Component Steps are as follows:

First log in to your Heroku account and follow the prompts to create a new SSH public key.

```
$ heroku login
```

Sign in to the Container Registry:

```
$ heroku container:login
```

![](img/8f8a671916d96b455297952d0f37b96c_524_0.png)

### Figure 8.23: Heroku Login for CLI

Navigate to the app’s directory and create a Heroku app:

```
$ heroku create
```

```
Creating app... done, hidden-river-78993
https://hidden-river-78993.herokuapp.com/ | https://git.heroku.com/hidden-river-78993.git
```

### Figure 8.24: Heroku App creation

Build the image and push to the Container Registry in one command. Make sure you started the Docker. And make sure you change the app name below for your case which will be created above.

```
$ heroku container:push web -a hidden-river-78993
```

```
(base) .Heroku $ heroku container:push web -a hidden-river-78993
=== Building web (/Users//Downloads/Streamlit/ComputerVision/Heroku/Dockerfile)
Sending build context to Docker daemon 16.38kB
Step 1/14 : FROM ubuntu:18.04
18.04: Pulling from library/ubuntu
5d9821c94847: Downloading 25.57MB/26.7MB
a610eae58dfc: Download complete
a40e0eb9f140: Download complete
Successfully built 68a10f4d1819
Successfully tagged registry.heroku.com/hidden-river-78993/web:latest
```

### Figure 8.25: Heroku Container Built and Pushed message

Then release the image to our app which we have created; here it will be hidden-river-78993.

```
$ heroku container:release web -a hidden-river-78993
```

Releasing images web to hidden-river-78993... done

### Figure 8.26: Heroku Container released to App

Now, open the app in your browser or we can navigate to the website and click on Open app at the right corner.

```
$ heroku open -a hidden-river-78993
```

![](img/8f8a671916d96b455297952d0f37b96c_526_0.png)

### Figure 8.27: Heroku Website Click Open App

Now, we can see our web Application hosted in Heroku.

## Choose Computer Vision Model

Model

Pencil Sketch

Upload your Photos

Drop files here to upload

Browse Files

## Computer Vision Use Case

This Web App is to help convert your photos to realistic images

### Figure 8.28: Computer Vision App hosted in Heroku

![](img/8f8a671916d96b455297952d0f37b96c_527_0.png)

## 8.6 Deploying the Streamlit code by containerizing in Kubernetes cluster

![](img/8f8a671916d96b455297952d0f37b96c_528_0.png)

![](img/8f8a671916d96b455297952d0f37b96c_528_1.png)

### Figure 8.29: Architecture for GCP Kubernetes Deployment

Now, create the Python script for your application and containerize your whole Framework with Docker and deploy the application inside Kubernetes cluster as a deployment service and the Docker image will be exposed as a Load Balancer deploy, which will generate a host URL on port 8501:

A Container is a type of software that packages up an application and all its dependencies, so the application runs reliably from one computing environment to another.

Docker is a software used for building and managing the containers.

Kubernetes is an open-source system for managing the containerized applications in a clustered environment.

Google Kubernetes Engine is an implementation of the open source Kubernetes framework on the Google Cloud Platform.

Let’s build the Docker image with everything being the same from earlier, just remove the last two lines from the earlier Heroku Dockerfile and add one line of CMD to run the Streamlit Python script:

```
FROM ubuntu:18.04
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
RUN mkdir -p /root/.streamlit

RUN bash -c 'echo -e "\
[general]\n\
email = \"\"\n\
" > /root/.streamlit/credentials.toml'

RUN bash -c 'echo -e "\
[server]\n\
enableCORS = false\n\
" > /root/.streamlit/config.toml'

RUN apt-get update && \
apt-get install -y \
python3.7 python3-pip \
libsm6 libxext6 libxrender-dev

EXPOSE 8501
WORKDIR /streamlit-docker
COPY requirements.txt ./requirements.txt
RUN pip3 install -r requirements.txt
COPY . .
CMD streamlit run Master.py
```

Now, run the following commands in Bash to build the Docker image for your GCP deployment, assuming you have the GCP project as a pre-requisite:

```bash
gcloud init
gcloud auth configure-docker
PROJECT_ID=$(gcloud config get-value core/project)
IMAGE_NAME=opencv-streamlit
IMAGE_NAME=gcr.io/$PROJECT_ID/$IMAGE_NAME
IMAGE_TAG=v1

# build image

docker build --no-cache -t $IMAGE_NAME:$IMAGE_TAG .
docker push $IMAGE_NAME:$IMAGE_TAG
```

Let’s say our Docker image will be like the following:
**gcr.io//opencv-streamlit:v1**

Make sure you install kubectl which we have installed in Chapter 1, Introduction to Kubeflow & Kubernetes Cloud Also, go to the following link: https://kubernetes.io/docs/tasks/tools/install-kubectl/

## Create Cluster:

To setup the Kubernetes cluster, either you use Google Cloud Shell or Microsoft Visual Studio Terminal of your system. Navigate to Google Cloud Platform > Kubernetes > Cluster.

![](img/8f8a671916d96b455297952d0f37b96c_531_0.png)

### Figure 8.30: GCP Cloud Shell

Now, complete the following steps:

Set your project ID and Compute Engine zone options for the gcloud tool.

```
PROJECT_ID=$(gcloud config get-value core/project)
gcloud config set project $PROJECT_ID
```
