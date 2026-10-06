# 11.3: MLOps Enabling Techniques and Contemporary Tools 381

communicate and run containers in any computing environment—for example, premise or in a commercial cloud.

While Docker allows you to create containers, another technology that has gained popularity in the ML community is Kubernetes (K8s). K8s is an orchestrator to automate the deployment, management, and scaling of applications encapsulated in containers. Containers allow you to instantiate microservices as self-contained units. Docker is a well-accepted technology to create containers. K8s facilitates the orchestration of containers on-premise or in commercial clouds.

K8s orchestration is supported by many of the MLOps platforms and cloud computing providers. K8s is well matched to ML implementations because of its scalability, extend across many types of hardware, and portability (so long as the tools and hardware support the K8s API).

K8s technology (initially introduced in 2014) was conceptualized at Google, making easier to deploy containers during the CD phase of the MLOps CI/CD cycle. Google began to develop its own container-management systems under the names of Borg and Omega [36]. Later, the company, working with the Cloud Native Computing Foundation (CNCF), made the K8s open-source to make it easier to deploy and manage complex distributed systems by application developers.

K8s employs a declarative configuration object [37]. A declarative configuration represents a desired state of a system. K8s orchestration is responsible for making sure that the actual state matches the desired. The desired state can be expressed, for example, JavaScript Object Notation (JSON) files—a human-readable format for storing data (key-value pairs), manipulating data, and defining configuration files (e.g., resources and objects).

As described by Raj, Kubeflow is a tool based on K8s enabling the orchestration of Docker-based microservices [30]. Kubeflow is a way of deploying an ML model. The container orchestration, implemented using Kubeflow, can be done by interfacing across services using the REST API (REST stands for “Representation State Transfer” as a publish-subscribe API). Zhou et al. published a more in-depth look at Kubeflow in the context of a K8s-based tool, for implementing a more of recognized deep learning algorithms within an ML pipeline, evaluating computation time (e.g., GPU usage), and memory performance [38].

Before we conclude this section, we strongly recommend that developers and integrators ensure strict security procedures. K8s can orchestrate distributed clusters. Pods are the smallest of relevant containers in a K8s cluster. A pod, with several containers uses the same underlying machine. In addition to reliable RBAC controls, there