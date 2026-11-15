# Getting to Know Kubernetes

Kubernetes takes a hierarchical approach to managing the various resources that it is responsible for, with each layer hiding the complexity beneath it.

The highest-level concept in Kubernetes is the **cluster**. A Kubernetes cluster consists of at least one Kubernetes **Master** which controls multiple worker machines called nodes. Clusters abstract their underlying computing resources, allowing users to deploy workloads to the cluster, as opposed to on particular **nodes**.

A **pod** is a collection of one or more containers that share common configuration and are run on the same machine. It is the basic workload unit in Kubernetes. All containers within a pod share the same context, resources, and lifecycle. Resources include local and remote storage volumes and networking. All containers in a pod share an IP address and port space. To run containers in pods, Kubernetes uses a container runtime, such as Docker, running on each node.

![](bbox=[0.2, 0.37, 0.78, 0.62])

Figure 3. Basic Kubernetes architecture

The master can be thought of as the “brain” of the cluster. It responds to cluster configuration and management requests submitted via the Kubernetes client or API. It is responsible for determining which pods are deployed to which nodes based on their respective requirements and capabilities, a process called **scheduling**. The master maintains the overall health of the cluster by re-scheduling pods in reaction to faults such as server failures.

Nodes in a Kubernetes cluster run an agent called the **kubelet** that listens for instructions from the master and creates, runs, and destroys containers accordingly. Collectively, the master and the kubelet processes govern the operation of the cluster and are referred to as the Kubernetes Control Plane.