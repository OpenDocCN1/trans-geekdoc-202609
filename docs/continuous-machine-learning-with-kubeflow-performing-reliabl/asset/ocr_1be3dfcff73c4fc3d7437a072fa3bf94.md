```
gcloud config set compute/zone us-central1
```

Create a cluster by executing the following code:

```
gcloud container clusters create streamlit-computer-vision --num-nodes=2
```

![](bbox=[0.12, 0.26, 0.88, 0.3])

Figure 8.31: Cluster Creation

Connect to cluster by clicking on the Connect button.

```
gcloud container clusters get-credentials streamlit-computer-vision --region us-central1 --project
```

![](bbox=[0.12, 0.53, 0.88, 0.62])

Figure 8.32: Cluster Connect

To deploy and manage the applications on a GKE cluster, you must communicate with the Kubernetes cluster management system. Execute the following command to deploy the application:

```
kubectl create deployment computervision-streamlit --image=gcr.io/opencv-streamlit:v1
```