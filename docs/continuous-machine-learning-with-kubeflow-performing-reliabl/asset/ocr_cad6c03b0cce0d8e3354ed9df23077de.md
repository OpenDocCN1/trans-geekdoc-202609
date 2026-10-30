```
IMAGE_NAME=gcr.io/$PROJECT_ID/$IMAGE_NAME
IMAGE_TAG=latest

# build image
Docker build -t $IMAGE_NAME:$IMAGE_TAG .
# run locally to test
Docker run -it --rm -p 8888:8888 -p 6006:6006 -v $(pwd):/home/jovyan $IMAGE_NAME:$IMAGE_TAG
# authorize Docker
gcloud auth configure-Docker --quiet
# push image

Docker push $IMAGE_NAME:$IMAGE_TAG
```

So, we will use the custom Docker image in the Jupyter Notebook.

gcr.io/custom-image-1:latest

Complete the following steps:

Click on Notebook Servers on the left-hand panel of the Kubeflow UI to access the Jupyter notebook services deployed with Kubeflow:

![](bbox=[0.12, 0.82, 0.88, 0.93])