
Now the cluster is up, let's explore it a bit. Try running the following commands in the CloudShell terminal and see what is returned:

| Items to explore | kubectl command syntax |
| --- | --- |
| Get cluster info. | kubectl cluster-info |
| List all API resources. | kubectl api-resources |
| List available namespaces. | kubectl get namespaces |
| List worker nodes. | kubectl get nodes |
| List Pods in all namespaces. | kubectl get pods -A |
| List services in all namespaces. | kubectl get services -A |
| List all clusterroles. | kubectl get clusterroles |
| List all roles in all namespaces. | kubectl get roles -A |
| List all service accounts in all namespaces. | kubectl get sa -A |
| Describe admin clusterrole. | kubectl describe clusterrole admin |
| List all secrets. | kubectl get secret -A |
| List all deployments. | kubectl get deployments -A |
| List networkpolicies. | kubectl get networkpolicies -A |

Table 6.1 – kubectl commands

+ 7. Deploy a Jupyter Notebook.

Let's deploy a Jupyter Notebook server as a containerized application. Copy and run the following code block. It should create a file called `deploy_Jupyter_notebook.yaml`. We will use a container image from the Docker Hub repository:

```
cat << EOF > deploy_Jupyter_notebook.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
name: jupyter-notebook
labels:
  app: jupyter-notebook
spec:
  replicas: 1
  selector:
  matchLabels:
```

# Kubernetes Container Orchestration Infrastructure Management

```yaml
app: jupyter-notebook
template:
  metadata:
    labels:
      app: jupyter-notebook
spec:
  containers:
    - name: minimal-notebook
      image: jupyter/minimal-notebook:latest
      ports:
        - containerPort: 8888
```

EOF
Now, let's create a deployment by running the following:
`kubectl apply -f deploy_Jupyter_notebook.yaml`

Check to make sure the Pod is running by running `kubectl get pods`.
Check logs of the Jupyter server Pod by running `kubectl logs <name of notebook pod>`. Find the section in the logs that contains `http://jupyter-notebook-598f56bf4b-spqn4:8888/token-XXXXXX...`, and copy the token (XXXXXX...) portion. We will use the token for *Step 8*.

You can access the pod using an interactive shell by running `kubectl exec --stdin <name of notebook pod> -- /bin/sh.run aux` to see a list of running processes. You will see a process related to the Jupyter Notebook.

+ 8. Expose the Jupyter Notebook to the internet.

At this point we have a Jupyter server running in a Docker container in a Kubernetes Pod on top of two EC2 instances in an AWS VPC but we can't get to it because the Kubernetes cluster doesn't expose a route to the container. We will create a Kubernetes service to expose the Jupyter Notebook server to the internet so it can be accessed from a browser.

Run the following code block to create a specification file for a new Service.
It should create a file called `jupyter_svc.yaml`:

```
cat << EOF > jupyter_svc.yaml
apiVersion: v1
kind: Service
metadata:
  name: jupyter-service
  annotations:
    service.beta.kubernetes.io/aws-load-balancer-type: alb
spec:
  selector:
    app: jupyter-notebook
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8888
  type: LoadBalancer
EOF
```

After the file is created, run `kubectl apply -f jupyter_svc.yaml` to create the service. A new Kubernetes Service called `jupyter-service` object should be created. You can verify the service by running `kubectl get service`. Note and copy the EXTERNAL-IP address associated with the jupyter-service service.

Paste the EXTERNAL-IP address to a new browser window, and enter the token you copied earlier in the **Password or token** field (Figure 6.11) to log in. You should see a Jupyter Notebook window showing up:

![](img/bd21298357d8484151447cff0b2f138b_197_0.png)

Figure 6.11 – Jupyter login screen

The following diagram shows the environment that you have created after working through the hands-on exercise.

![](img/bd21298357d8484151447cff0b2f138b_198_0.png)

Figure 6.12 – Jupyter notebook deployment on the EKS cluster

Congratulations, you have successfully created a new Amazon EKS cluster on AWS and deployed a Jupyter Server instance as a container on the cluster. We will re-use this EKS cluster for the next chapter. However, if you don't plan to use this EKS for a period of time, it is recommended to shut down the cluster to avoid unnecessary costs.

## Summary

In this chapter, we covered Kubernetes, a container management platform that can serve as the infrastructure foundation for building open source ML platforms. Now, you should be familiar with what containers are and how Kubernetes works. You have also learned how to set up a Kubernetes cluster.

## Section 3: Technical Architecture and Regulatory Considerations for ML Platforms

In this section, we will discuss architecture and requirements beyond just data scientists, looking at ML platforms and governance. This section comprises the following chapters:

- Chapter 7: Open Source Learning Platforms
- Chapter 8: Building Data Science Environment Using AWS Services
- Chapter 9: Building Enterprise ML Architecture with AWS Services
- Chapter 10: ML Engineering
- Chapter 11: ML Governance, Bias, Explainability, and Privacy
- Chapter 12: Building ML Solutions Using AI Services
