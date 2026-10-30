So let’s break the transformer predictor code as follows:

We kept the service account which has the storage bucket in the Docker root and then declared that folder as an environment variable to an object **model_output_base_path** for gcp bucket path.

Next, in the Load function, we loaded the model in from the TensorFlow library.

Then, in the predict method, the incoming data will come as a json format which we need to extract as a key-value pair and do the necessary prediction and return as a dictionary.

So, in the “main” function, the **KFServingSampleModel** class takes the name of that deployment; keep a note of that and apply to the yaml file; here it is "kfserving-breast-model"

Next, we will build the Docker image for our serving model.

# Docker:

```
FROM python:3.7-slim-stretch
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && \
apt-get-y install gcc mono-mcs g++ git curl bash && \
rm-rf /var/lib/apt/lists/*
RUN mkdir /app
```