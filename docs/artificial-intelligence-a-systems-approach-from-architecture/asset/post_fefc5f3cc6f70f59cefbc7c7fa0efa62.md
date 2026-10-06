
## 11.3: MLOps Enabling Techniques and Contemporary Tools

Furthermore, within the MLOps CI/CD steps, a set of ML artifacts must be tracked. These artifacts, as outlined by Treveil et al. are the following [5]:

- Model code and its preprocessing
- Model hyperparameters and associated model configurations
- Data for training and model validation
- The model after completing its testing scenarios
- Code and data for testing scenarios
- Libraries with specific versions and environment variables used in the creating of the model
- Documentation

Ormenasan et al. developed a more automated approach to logging and tracking ML artifacts at each of the stages of the ML pipeline [32]. The authors' implicit preference avoids omitting important ML artifacts while still preserving ML automation.

These artifacts must be tracked at each of the five I-V&V steps described earlier (i.e., unit-test, subsystem, single-thread, online end-to-end AI system, and inline end-to-end AI system). We reinforce the importance of this methodical approach since rushing to deploy AI capabilities will lead to mistrust, not only of the AI organization developing the AI or service, but also among the culture within the AI team.

The DevOps movement, as well as the need for an Agile methodology to enable more rapid (i.e., short turnaround time) demonstrations, led to making applications more modular. Microservices were a solution allowing a single application to be broken into small components that could be managed, administered, and deployed as a collection of smaller services instead of a large, complex, monolithic architecture [33]. Microservices conform to modern service-oriented architecture, where a publish-subscribe architecture interfacing with databases across the computational network.

For many years, with the increasing availability of large computing resources (i.e., processing nodes, memory, and high-speed interconnects), virtual machines (VMs) became vogue. However, VMs had the disadvantage of encapsulating not only the application and associated libraries, but also the operating system. VMs were difficult to migrate from one server to another. A more suitable approach for developing and deploying microservices was using containers. In the context of MLOps, this containerized approach became a way to deploy applications more rapidly within the CI/CD cycle.

Red Hat (a subsidiary of IBM) describes clearly, in a series of blogs, the differences between VMs and containers [34]:

| VM | VM | VM | Container | Container | Container |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Service | Service | Service | Service | Service | Service |
| Apps | Apps | Apps | Apps | Apps | Apps |
| Libraries | Libraries | Libraries | Libraries | Libraries | Libraries |
| Guest OS | Guest OS | Guest OS | | | |
| | Hypervisor | | Docker engine | | |
| | Host operating system | | Host operating system | | |
| | Bare metal | | Bare metal | |

Figure 11.1 Comparison between VMs and containers. Source: OS = operating system. Andrew Morgan from MongoDB [35].

Containers: A tool to power microservices by running securely isolated applications. The Docker technology is useful for creating containers, which provided a way to encapsulate executable code, libraries, third-party apps via APIs, and other resources to achieve DevOps developments. Andrew Morgan presented an illustration at the MongoDB 2016 conference [35] comparing VMs and containers, as depicted in figure 11.1.

In contrast to VMs, where the guest operating system is virtualized (making it harder to migrate across servers), containers are less coupled to the operating system. Containers source the operating system kernel from the host machine it is running on, making it easier to spin up and migrate from one server to another. Application code and libraries can be shared, if necessary, by each container conforming to well-defined APIs. Containers also enable deploying capabilities into production by automatically rebuilding the image on the target machine since all the dependencies are containerized, meaning that it enables more rapid transitioning from an online configuration to an online operational environment.

The Docker, as a tool, became the de facto containerization service, providing complete isolation from other applications and the host operating system. The technology was announced in 2013 and was released as open source in 2014. Docker, as a containerization technology, is used to create containers and configuration files identifying how the application and libraries and any of its dependencies must run. One communicate and run containers in any computing environment—for example, premise or in a commercial cloud.

While Docker allows you to create containers, another technology that has gained popularity in the ML community is Kubernetes (K8s). K8s is an orchestrator to automate the deployment, management, and scaling of applications encapsulated in containers. Containers allow you to instantiate microservices as self-contained units. Docker is a well-accepted technology to create containers. K8s facilitates the orchestration of containers on-premise or in commercial clouds.

K8s orchestration is supported by many of the MLOps platforms and cloud computing providers. K8s is well matched to ML implementations because of its scalability, extend across many types of hardware, and portability (so long as the tools and hardware support the K8s API).

K8s technology (initially introduced in 2014) was conceptualized at Google, making easier to deploy containers during the CD phase of the MLOps CI/CD cycle. Google began to develop its own container-management systems under the names of Borg and Omega [36]. Later, the company, working with the Cloud Native Computing Foundation (CNCF), made the K8s open-source to make it easier to deploy and manage complex distributed systems by application developers.

K8s employs a declarative configuration object [37]. A declarative configuration represents a desired state of a system. K8s orchestration is responsible for making sure that the actual state matches the desired. The desired state can be expressed, for example, JavaScript Object Notation (JSON) files—a human-readable format for storing data (key-value pairs), manipulating data, and defining configuration files (e.g., resources and objects).

As described by Raj, Kubeflow is a tool based on K8s enabling the orchestration of Docker-based microservices [30]. Kubeflow is a way of deploying an ML model. The container orchestration, implemented using Kubeflow, can be done by interfacing across services using the REST API (REST stands for “Representation State Transfer” as a publish-subscribe API). Zhou et al. published a more in-depth look at Kubeflow in the context of a K8s-based tool, for implementing a more of recognized deep learning algorithms within an ML pipeline, evaluating computation time (e.g., GPU usage), and memory performance [38].

Before we conclude this section, we strongly recommend that developers and integrators ensure strict security procedures. K8s can orchestrate distributed clusters. Pods are the smallest of relevant containers in a K8s cluster. In addition to reliable RBAC controls, there are tools described by Burns et al., such as the PodSecurity API and RuntimeClass [39]. We advise AI engineers who are responsible for the infrastructure to incorporate guardrails from the start of the AI development, as described earlier in this section. Commercial cloud providers offer strong security controls and policies.

## 11.4 MLOps Platforms, AutoML, and LCNC Development

In the previous section, we discussed the use of MLOps techniques and explained some of the contemporary tools found within MLOps platforms. In this section, we look at some MLOps platforms that are commercially available. Again, there is great interest among the AI community in employing MLOps platforms to use available tools and techniques within the infrastructure; a very large number of companies exists. We do not review the MLOps landscape in this discussion, but rather we refer to a number of publications that have put out more in-depth landscape reviews.

In the literature, the term "platforms" is used, spanning from implementation languages (e.g., Python, R) to multiple-billion-dollar market capitalization companies. In this section, we use the term “MLOps platform” as follows:

MLOps platform: An environment with the ability to implement the full life cycle of an AI system architecture framework shown in figure 10.3, and to meet the requirements of an AI platform with characteristics described in table 10.6, as part of the AI ecosystem illustrated in figure 10.4.

We opt for this definition since the emphasis on our discussion is an end-to-end holistic implementation, not just the ML algorithm implementation. To date, existing commercial MLOps platforms do not provide the full scope described in our definition. However, even though the MLOps discipline is nascent, several companies offer capable and comprehensive infrastructure environments. Some commercial solution providers also refer to their offerings as “AI cloud platforms.”
