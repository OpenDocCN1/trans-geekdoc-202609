# Kubernetes Container Orchestration Infrastructure Management

```
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

+   8. Expose the Jupyter Notebook to the internet.

At this point we have a Jupyter server running in a Docker container in a Kubernetes Pod on top of two EC2 instances in an AWS VPC but we can't get to it because the Kubernetes cluster doesn't expose a route to the container. We will create a Kubernetes service to expose the Jupyter Notebook server to the internet so it can be accessed from a browser.