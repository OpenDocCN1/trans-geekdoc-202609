
There have been considerable attempts to build reliable and scalable container management platforms for clusters in the research and open-source communities (Rodriguez & Buyya, 2019). These systems are responsible for managing the deployment of general-purpose applications, usually packaged in either `Docker` or `Linux cgroups`-based containers. In this section, we briefly present related works in the context of software systems and resource management algorithms for container orchestration.

## Software Systems

**Kubernetes** (Hightower, Burns, & Beda, 2017) is the leading open-source container management platform, which is derived from Google’s in-house **Borg** (Verma et al., 2015). Kubernetes orchestrates and manages the lifecycle of heterogeneous containerized applications (such as services and batch jobs) in either virtualized or physical clusters. It provides a default scheduler that assigns each container group (or `pod`) to available cluster resources filtered by user-defined requirements and ranked based on individually defined application affinities. A detailed evaluation of Kubernetes can be found in (Medel, Rana, Bañares, & Arronategui, 2016).

**Docker Swarm** (Naik, 2016) is the native clustering solution for `Docker` containers. It provides discovery services and schedules containers onto hosts using predefined strategies and filters. By default, it supports two simple strategies: i) a spread strategy that favors running new containers on least loaded hosts, and ii) a bin packing strategy that favors the most loaded hosts that have enough resources to run the containers. Docker Swarm also employs a filtering mechanism to identify the qualified resources; users can define filters regarding host statuses, health check results, and container configurations (such as resource and file affinities and dependencies to other containers).

**Apache Mesos** (Hindman et al., 2011) enables cluster sharing among various applications. Different to Kubernetes and Swarm, Mesos can be viewed as a meta-platform that operates above them. It employs a two-stage scheduling approach. In the first stage, it divides the resources of the cluster and respectively provisions resources to each application via resource offers. Once an application accepts a resource offer, it can proceed to scheduling its tasks on the obtained resources using its own scheduling logic. After that, Mesos actually launches the tasks for the application on the corresponding hosts.

**Apache Marathon** (Marathon, n.d.) and **Apache Aurora** (DelValle, Rattihalli, Beltre, Govindaraju, & Lewis, 2016) are two popular general-purpose frameworks built on top of Mesos. Marathon is designed to orchestrate long-running services. Because of this, it focuses on providing applications with fault-tolerance and high-availability; Marathon will ensure that launched applications will continue to run even in the presence of node failures. Originally developed by Twitter, Aurora is a scheduler that enables long-running services, cron jobs, and ad-hoc jobs to be deployed in a cluster. Aurora specializes in ensuring that services are kept running continuously and as a result, when machine failures occur, jobs are intelligently rescheduled onto healthy machines. It is worthwhile mentioning that in terms of functionality, Marathon and Aurora are very similar products. However, there are a few differences. The main one is that Marathon handles only service-like jobs. Furthermore, setting up and using Marathon is considered to be simpler than doing so with Aurora; Marathon includes for example a user interface through which users can directly schedule tasks.

**YARN** (Vavilapalli et al., 2013) is a cluster manager designed to orchestrate Hadoop tasks, although it also supports other frameworks such as Giraph, Spark, and Storm. Each application framework running on top of YARN coordinates their own execution flows and optimizations as they see fit. In YARN, there is a per-cluster resource manager (`RM`) and an application master (`AM`) per framework. The `AM` requests resources from the `RM` and generates a physical plan from the resources it receives. Hence, YARN’s two-level scheduling model is similar to Mesos, but instead of it offering resources to applications, applications request the needed resources from YARN.

Although most of the above systems are mature, the resource management optimization space can still be further explored. This is especially true in the era of cloud computing, as most existing frameworks ignore many of the inherent features of cloud platforms in favour of assuming a static cluster of resources. As a result, elasticity, pricing, and service heterogeneities are ignored. Rescheduling for defragmentation and autoscaling is another feature missing from the aforementioned systems. This work aims to address these gaps by exploring the benefits of considering autoscaling and rescheduling when managing the cluster’s resources.

## Resource Management Algorithms

This section discusses relevant works that focus on container-based scheduling algorithms. Xu et al. (Xu, Yu, & Pei, 2014) proposed a resource scheduling approach for container-based cloud environments to reduce the response time of requests and improve resource utilization, which can obtain an optimal mapping for containers to hosts by using stable machine theory. (Zhang et al., 2016) designed a novel video surveillance cloud platform based on containers, which applies future workload prediction to achieve fine-grained resource provisioning and ensure quality of service. (Kaewkasi & Chuenmuneewong, 2017) applied Ant Colony Optimization to allocate containers to hosts and aimed to balance the resource usage. (Kehrer & Blochinger, 2018) presented a two-phase deployment method for **Apache Mesos** to achieve a more flexible management of containers. (Guerrero, Lera, & Juiz, 2018) proposed a genetic algorithm for **Kubernetes** platform to optimize container allocation and elasticity management. Their algorithm can improve system performance and reduce network overhead. Contrary to the work presented in this chapter, the aforementioned approaches focus on the initial placement of containers (i.e., scheduling) and do not consider the rescheduling and autoscaling.

(Yin, Luo, J., & Luo, H., 2018) built a task-scheduling model by exploiting containers and developed a task-scheduling algorithm to reduce the completion time of tasks in fog computing environment. They also proposed a rescheduling approach to optimize task delays. However, the results are only validated in a simulated environment.

(Xu, Toosi,, & Buyya, 2018) proposed an approach based on containers and brownout, which can dynamically activate and deactivate optional containers to achieve an energy-efficient management of cloud resources while ensuring quality of service requirements are met. This approach applies autoscaling to reduce the active number of hosts but it doesn’t consider the initial placement and rescheduling of containers.

Table 1 summarises the comparison of related works focused on resource management algorithms.

**Table 1. Comparison of related algorithmic works**

| Work | Objective/Focus | Initial Placement | Rescheduling | Autoscaling | Platform |
| --- | --- | --- | --- | --- | --- |
| (Xu et al. 2014) | Reduce response time | √ | | | Simulation |
| (Zhang et al., 2016) | Improve resource utilization | √ | | | Docker |
| (Kaewkasi & Chuenmuneewong, 2017) | Balance resource usage | √ | | | Docker |
| (Yin et al., 2018) | Reduce task delays | √ | √ | | Simulation |
| (Guerrero et al., 2018) | Reduce network overhead | √ | | | Kubernetes |
| (Kehrer & Blochinger, 2018) | Flexible management | √ | | | Mesos |
| (Xu et al. 2018) | Reduce energy | | | √ | Docker |
| Our work (this chapter) | Reduce cost | √ | √ | √ | Kubernetes |

## Application and Resource Models
