```
services:
  web-fe:             <----- Service name. Containers wil
  deploy:
    replicas: 1          <----- Deploy a single container fo
    build:               <----- Build from the Dockerfile in
    command: python app.py <----- Execute this command when st
    ports:
      target: 8080       <----- Map port in the contain
      published: 5001 <----- ...to port 5001 on the Docke
  networks:
    counter-net          <----- Attach containers to the "co
  volumes:
    type: volume
    source: counter-vol <----- Mount the "counter-vol" volu
    target: /app         <----- ...to "/app" in the contain
```

Let's step through it.

+   - **web-fe:** is the service’s name, and all containers created part of this service will have “web-fe” in their names.
- **deploy.replicas: 1** tells Docker to deploy a single container for this service. You can specify a different number of replicas to deploy multiple identical containers for the service. However, this won’t work on Docker installations as you only have a single Docker host, and only one container can use port 5001 on the Docker Desktop host. You’ll learn how to deploy multiple replicas for this service in the **Deploying apps with Docker stacks** chapter.