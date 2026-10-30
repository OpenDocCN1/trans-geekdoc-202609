```
default:
predictor:
custom:
container:
image: gcr.io//brain_tumor_scan/ kf_serving_braintest:v1
```

Here, in the preceding yaml file, we will give the same name which we have provided in the serving.py file having the model name (“kfserving-braintumor”), and then we will provide the namespace “kubeflow” where it will be deployed. Next, we will give the Docker image name.

![](bbox=[0.12, 0.4, 0.9, 0.56])

Figure 3.7: KF – Serving Model name match

As we can see, the line number from the left image and the 6th from the right should always be the same.

Next, run the following command from the bash where the files are kept in the Visual Studio:

Connect to the GCP cluster by using the following command: