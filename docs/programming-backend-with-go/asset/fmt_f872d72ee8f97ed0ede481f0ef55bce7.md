
# Docker Basics

Docker is a platform that uses containerization technology to facilitate application deployment within containers. This platform guarantees that the program will run flawlessly in every environment, whether it is a personal laptop, a test server, or a production system. To avoid the normal "it works on my machine" issue with our project, `gitforgits.com`, we must create a development environment that matches production, and understanding the fundamentals of Docker is required.

## What are Docker Containers?

Software code, libraries, configuration files, environment variables, and runtime are all contained in small, standalone executable packages called containers. Containers are segregated from one another and the host system, yet they share the OS kernel, start quickly, and consume less CPU and RAM.

## Images and Containers

The fundamental concepts in Docker are images and containers. A Docker image is a snapshot of a container, a static specification of what the program needs to run. On the other hand, a container is a runtime instance of an image—what the image becomes in memory when executed.

## Dockerfile

To create a Docker image, you start with a base image and use a `Dockerfile`. A `Dockerfile` is a text document that contains all the commands a user could call on the command line to assemble an image.

For instance, to build a simple Docker image for the `gitforgits.com` application, you might start with a basic Go image and then copy your application code into the image:

```
# Use the official Go runtime as a parent image
FROM golang:1.18
# Set the working directory
WORKDIR /go/src/app
# Copy the current directory contents into the container at /go/src/app
COPY . .
# Download all the dependencies
RUN go get -d -v ./...
# Install the package
RUN go install -v ./...
# Make port 80 available to the world outside this container
EXPOSE 80
# Run the executable
CMD ["app"]
```

This `Dockerfile` starts with a Go image, sets the working directory, copies the application directory from your project into the Docker image, installs dependencies, exposes port 80, and specifies the command to run the application.

## Building and Running Docker Containers

Once you have a `Dockerfile`, you can build the image using:

```
docker build -t gitforgits.com .
```

The above command tells Docker to build an image from the `Dockerfile` in the current directory and tag this image with the name `gitforgits.com`.

After building the image, you can run it in a container:

```
docker run -p 4000:80 gitforgits.com
```

The above command runs the image as a container, mapping port 80 of the container to port 4000 on your host, allowing you to access the application via `localhost:4000` in your web browser.

## Docker Compose

For more complex applications like `gitforgits.com`, which might require running multiple containers, e.g., one for the application server, another for the database, Docker Compose is used. `Docker Compose` is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services, networks, and volumes.

Following is an example of a `docker-compose.yml` file for `gitforgits.com`:

```
version: '3'
services:
  web:
    build: .
    ports:
      - "4000:80"
  db:
    image: postgres
    environment:
      POSTGRES_DB: gitforgits
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
```

This configuration defines two services: `web`, which builds from the current directory, and `db`, which uses a pre-built PostgreSQL image. It also sets up environment variables for the database, such as the database name, user, and password.

## Starting and Managing Project Containers

With Docker Compose, you can start all services defined in your `docker-compose.yml` with one command:

```
docker-compose up
```

And you can stop them with:

```
docker-compose down
```

## Volumes and Networks

To persist data and manage the network between containers, Docker allows you to define volumes and networks. In the `docker-compose.yml` file, you can specify volumes to persist the database data and custom networks to facilitate communication between containers.

The above well-introduced Docker covers all the essentials you need to know to begin incorporating this technology into your development projects with ease.

## Summary

We started by going over the basics of the Go programming language, focusing on how well it works and how well it fits the bill for creating solid backend systems. We gave an overview of the Go ecosystem, highlighting libraries and tools that are useful for backend development, such as `gorilla/mux` for routing, `gorm` for object relationship management, and `nsq` for message brokers. To keep things consistent, we went over how to install Go in depth and made sure to use Go `1.18` in all of our examples. After that, we used VS Code to set up the development environment, adding the required Go extensions to make coding easier and more productive. The importance of Go modules in package management was learned, with a focus on how they facilitate efficient dependency management. We also went over the components and syntax of a Go program, illustrating their practical application with our sample book selling platform, `gitforgits.com`. Writing functions, managing imports, and using variables were some of the fundamentals of Go project setup that we covered. Last but not least, we learned Git version control and its significance in managing project versions and team collaboration. At the end, we covered the basics of Docker and how containerization can be used to maintain consistent environments across development and production.

# Chapter 2: Building a Basic Web Server with net/http

## Chapter Overview

This chapter looks into the practical elements of utilizing Go's `net/http` package to create a simple web server, which is a fundamental skill for backend engineers. We will begin by looking at the capabilities and key components of the `net/http` package, which includes the tools needed to build HTTP servers and process web requests successfully. As we go, you will learn how to configure your own web server, including the basics of launching a server and handling basic HTTP requests.

The chapter continues by breaking down the structure of HTTP requests and answers, shedding light on the data exchange process between a server and a client. We will go over how to use `http.ServeMux`, Go's default multiplexer, to route requests to the appropriate handlers, allowing you to manage many URLs and pathways easily.

For the purpose of building RESTful APIs, next steps will focus on managing various HTTP methods, including `GET`, `POST`, `PUT`, and `DELETE`, among many others. You'll also learn how to employ query parameters and URL fragments to obtain information given by clients, which is required for dynamic answers based on user input.

We will go over the steps to set up your Go server to serve static files and assets, which are an essential part of any web server. This will allow your server to run a full-fledged web application by serving HTML, CSS, and JavaScript.

Finally, the chapter will walk you through the best ways to structure a Go web application project. This involves structuring your code, managing dependencies, and creating a project environment that can scale as your application grows.

By the end of this chapter, you'll have a strong grasp of how to design and manage simple web servers in Go, as well as the ability to develop more complex backend systems.
