> "Deep learning is an empirical science, and the quality of a group's infrastructure is a multiplier on progress. Fortunately, today's open-source ecosystem makes it possible for anyone to build great deep learning infrastructure."
> OpenAI

# # Kubernetes for Machine and Deep Learning

While the challenges faced by developers building traditional software are similar to those faced by data scientists and ML engineers, they aren't the same. In many ways, those faced by the latter are greater, significantly exacerbated by the highly iterative nature of the machine learning workflow.

Still, the capabilities provided by containers and Kubernetes can help organizations address the challenges presented by the machine learning process.

| Simplifying Data Management | Driving Efficient Resource Use | Hiding Complexity |
| :--- | :--- | :--- |
| Kubernetes provides connectors for diverse data sources and manages volume lifecycle Data workflow & pipeline abstractions (3rd party) allow complex data transformations to be executed across cluster Data fabrics (3rd party) extend scalable, multi-format storage to cluster | Kubernetes provides elasticity, allowing cluster and workloads to be easily scaled up/down Multitenancy allows multiple teams to share cluster Users can deploy workloads on-demand via CLI, API without IT intervention Users and tools can programmatically deploy and control workloads | Containers provide a convenient format for packaging workloads and declaring dependencies Kubernetes abstracts infrastructure, allowing users to think of cluster as unit of compute |

Figure 5. Containers and Kubernetes address major ML/DL challenges

# ## Data acquisition and preparation

By providing a mechanism for connecting storage to containerized workloads, the Kubernetes CSI enables support for a wide variety of stateful applications, including machine and deep learning. CSI drivers provide direct access to many different file, object, and block storage systems, as well as data fabric products which provide unified access to data stored in a variety of enterprise systems.