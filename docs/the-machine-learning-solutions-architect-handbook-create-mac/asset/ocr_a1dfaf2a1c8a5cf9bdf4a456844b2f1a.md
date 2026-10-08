Now the cluster is up, let's explore it a bit. Try running the following commands in
t CloudShell terminal and see what is returned:

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

+   7. Deploy a Jupyter Notebook.

Let's deploy a Jupyter Notebook server as a containerized application. Copy and
running the following code block. It should create a file called deploy_Jupyter_notebook.yaml. We will use a container image from the Docker Hub repository:

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