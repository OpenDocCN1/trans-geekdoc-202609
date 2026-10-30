Instead, the pods are usually managed by one more layer of abstraction – the deployment.

A deployment’s primary purpose is to declare how many replicas of a pod should be running at a time. When a deployment is added to the cluster, it will automatically spin up the requested number of pods, and then monitor them. If a pod dies, the deployment will automatically re-create it.

![](bbox=[0.13, 0.36, 0.88, 0.75])

Figure 1.10: Deployment concept

Using a deployment, you don’t have to deal with the pods manually. You can just declare the desired state of the system, and it will be managed for you automatically.