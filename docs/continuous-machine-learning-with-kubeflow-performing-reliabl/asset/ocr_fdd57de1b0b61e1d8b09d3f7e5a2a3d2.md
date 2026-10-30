other containers in the same pod, as though they were on the same machine while maintaining a degree of isolation from the others.

Pods are used as the unit of replication in Kubernetes. If your application becomes too popular and a single pod instance can’t carry the load, Kubernetes can be configured to deploy the new replicas of your pod to the cluster as necessary. Even when not under the heavy load, it is standard to have multiple copies of a pod running at any time in a production system to allow the load balancing and failure resistance.

![](bbox=[0.13, 0.41, 0.88, 0.64])

Figure 1.8: Pod Concept

The Pods contain one or more containers, such as the Docker containers. When a Pod runs multiple containers, the containers are managed as a single entity, and share the Pod's resources. Generally, running multiple containers in a single Pod is an advanced use case.