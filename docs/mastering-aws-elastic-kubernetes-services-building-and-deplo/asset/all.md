![](images/cover.jpg)

![Cover](images/cover.jpg)

First Edition 2025

Copyright © BPB Publications, India

ISBN: 978-93-65899-887

All Rights Reserved. No part of this publication may be reproduced, distributed or transmitted in any form or by any means or stored in a database or retrieval system, without the prior written permission of the publisher with the exception to the program listings which may be entered, stored and executed in a computer system, but they can not be reproduced by the means of publication, photocopy, recording, or by any electronic and mechanical means.

LIMITS OF LIABILITY AND DISCLAIMER OF WARRANTY

The information contained in this book is true to correct and the best of author’s and publisher’s knowledge. The author has made every effort to ensure the accuracy of these publications, but publisher cannot be held responsible for any loss or damage arising from any information in this book.

All trademarks referred to in the book are acknowledged as properties of their respective owners but BPB Publications cannot guarantee the accuracy of this information.

![](images/BPB_Catalogue_QR.png)

[www.bpbonline.com](https://www.bpbonline.com)

**Dedicated to**

My Mom, Dad, Almighty Gurunathans,  
My Wife and My kids

# About the Author

Siva Guruvareddiar is a senior specialist solutions architect at Amazon with over 18 years of extensive experience in designing, implementing, and managing cloud solutions. His expertise spans cloud computing, application development, big data, and application modernization, with particular emphasis on Kubernetes and cloud-native technologies.

Currently at Amazon, Siva designs and implements cloud-based solutions using Kubernetes, Prometheus, and AWS services, achieving significant improvements in infrastructure costs and application performance. His career includes key roles at major technology companies like Apple, where he led containerized application deployments and cloud platform development, and Oracle, where he contributed to significant enterprise solutions.

Siva holds numerous prestigious certifications, including AWS Solutions Architect Professional, AWS Big Data Specialty, and multiple CNCF Kubernetes certifications (Administrator, Developer, and Security Specialist). He has authored 20+ technical publications, including "Managing Kubernetes Control Plane Events in Amazon EKS" and "Authenticating with Grafana Using Open Source Keycloak on Amazon EKS.” etc

His combination of hands-on experience, technical expertise, and passion for mentoring makes him uniquely qualified to guide readers through the complexities of AWS EKS. Through this book, he shares practical insights and best practices gained from years of implementing cloud-native solutions at enterprise scale.

# About the Reviewers

*   Suresh Dodda commands an impressive 24-year career in technology, fortified by a Master’s degree in Computer Applications. His expertise spans Java, AWS, Spring Boot, Microservices, cloud-native solutions, and tools including AWS, Ansible, Kubernetes, Terraform, statistical learning, and data mining. He is also a technical reviewer for various books about CI/CD, Kubernetes, Java, AWS, and microservices. Suresh is an active reader and the author of the book Spring Boot Microservices Handbook Practical Guide for Developers. He is also an AI/ML researcher with many research articles published in IEEE conferences. He is a Fellow member of BCS, a Fellow member of IETE, and a Senior member of IEEE.
    
*   Nikhil Kumar is a senior software engineer at HPE. with a broad and versatile skill set encompassing development, architecture, and consultancy. Nikhil has made significant contributions across diverse domains for various clients and employers. His areas of expertise include DevOps, Python, Cloud, Kubernetes and MLOps. He holds multiple prestigious certifications from Red Hat, including Red Hat Certified Engineer (EX294) and Red Hat Certified OpenShift Administrator (EX280). As a prolific technical blogger, Nikhil shares his extensive knowledge with the broader software engineering community and serves as a technical reviewer for various books on DevOps, Cloud, MLOps, and Kubernetes.
    

# Acknowledgement

I would like to extend my heartfelt gratitude to everyone who contributed to the completion of this book.

First and foremost, I sincerely thank my family for their unwavering support and encouragement throughout this journey. Their love and motivation have been my constant source of strength.

I am deeply appreciative of BPB Publications for their invaluable guidance and expertise in bringing this book to life. Their support played a crucial role in navigating the complexities of the publishing process.

I would also like to acknowledge the reviewers, technical experts, and editors whose insightful feedback and suggestions greatly improved the quality of this manuscript.

Lastly, I am profoundly grateful to the readers who have shown interest in this book. Your support and enthusiasm mean the world to me.

To everyone who played a part in making this book a reality, thank you.

# Preface

In today's cloud-native landscape, Amazon Elastic Kubernetes Service (EKS) has emerged as a cornerstone for organizations seeking to build and scale containerized applications. "Mastering AWS Elastic Kubernetes Services" is crafted to be your comprehensive guide through the intricate world of Kubernetes on AWS, reflecting my experiences and insights gained from implementing EKS solutions at scale across various enterprise environments.

This book systematically builds your understanding through 23 carefully structured chapters. We begin with fundamental Kubernetes concepts, ensuring a solid foundation before diving into EKS-specific architectures and components. The journey progresses from basic cluster setup to advanced operational aspects, including security, monitoring, and integration with AWS services. Each chapter is designed to provide practical, hands-on knowledge that you can immediately apply in your professional role.

The middle sections of the book focus on real-world scenarios, covering crucial topics like deploying stateful applications, implementing networking solutions, and establishing robust security measures. We explore essential operational aspects such as monitoring, logging, and troubleshooting, which are vital for maintaining production-grade EKS clusters.

As we advance, the book delves into modern DevOps practices, including CI/CD pipelines, GitOps workflows, and disaster recovery strategies. The final chapters concentrate on optimization techniques and best practices, ensuring your EKS implementations are not just functional but excel in performance, security, and cost-effectiveness.

Drawing from my experience as a Solutions Architect at Amazon and previous roles at major technology companies, I've included practical examples, common pitfalls to avoid, and industry best practices throughout the book. Whether you're a DevOps engineer, cloud architect, or platform administrator, this book aims to enhance your expertise in managing containerized applications on AWS.

I hope this book serves as your trusted companion in mastering AWS EKS, helping you build and maintain robust, scalable, and secure Kubernetes environments on AWS.

[Chapter 1: Introduction to Kubernetes](#ch01.xhtml) - This chapter traces the evolution of container orchestration, starting from early virtualization to modern Kubernetes. It explores the progression from traditional virtualization to Linux containers and Docker's emergence. The chapter discusses how Kubernetes emerged as the solution to container orchestration challenges and its donation to CNCF in 2014. It examines the explosion of the cloud-native landscape and Kubernetes' journey to becoming the de facto container orchestration platform. The content covers enterprise capability maturity models and adoption patterns. Finally, it provides insights into Kubernetes' current dominance and future trajectory in the cloud-native ecosystem.

[Chapter 2: Kubernetes Architecture](#ch02.xhtml) - A deep dive into Kubernetes' fundamental building blocks and architectural components. The chapter explores core concepts including controllers, labels, selectors, and annotations that form Kubernetes' backbone. It examines various controllers like Deployments, StatefulSets, DaemonSets, and Jobs, explaining their specific use cases. The content covers configuration management through ConfigMaps and Secrets, and automatic scaling via Horizontal Pod Autoscaler. The chapter discusses storage considerations and the crucial reconciliation loop mechanism. Finally, it addresses monitoring and security aspects within the Kubernetes architecture.

[Chapter 3: Kubernetes Components](#ch03.xhtml) - Detailed examination of core Kubernetes components including kube-apiserver, etcd, and scheduler. The chapter explains the roles of critical components like kube-controller-manager, kubelet, and kube-proxy. It covers essential add-ons for container resource monitoring and cluster-level logging. The content explores networking components and their interactions within the cluster. Storage components and their integration with the core system are discussed. The chapter delves into extension components and their role. Finally, it ties together how these components work cohesively.

[Chapter 4: Introduction to Amazon Elastic Kubernetes Service](#ch04.xhtml) \- An overview of Amazon EKS and its key features including high availability and managed infrastructure. The chapter explores how EKS incorporates latest Kubernetes innovations while providing flexibility. It discusses optimized cost structures and built-in observability features. The content examines EKS's security and compliance capabilities. The chapter explains control plane management and worker node operations. Finally, it covers basic cluster administration and application deployment concepts.

[Chapter 5: Amazon Elastic Kubernetes Service Architecture](#ch05.xhtml) - Comprehensive coverage of EKS cluster components including control plane and worker nodes. The chapter explores different node types including managed, self-managed, and Fargate nodes. It examines various autoscaling options including cluster, vertical, and horizontal pod autoscaling. The content covers security best practices and VPC network policies. The chapter discusses cluster upgrade and maintenance procedures. Integration capabilities with AWS services are explored. Finally, it details creating highly available production clusters.

[Chapter 6: Setting up Elastic Kubernetes Service Prerequisites](#ch06.xhtml) - Detailed walkthrough of system requirements across Windows, macOS, and Linux platforms. The chapter covers essential IAM setup including user, group, and role creation. It explains VPC networking concepts including subnet layout and routing configuration. The content focuses on security group rules and IAM policies for CNI plugin access. Guidance on operations tool setup is provided. The chapter covers billing integration aspects. Finally, it ensures readers have all prerequisites configured correctly.

[Chapter 7: Creating Elastic Kubernetes Service Clusters](#ch07.xhtml) - Comprehensive guide to creating EKS clusters using multiple approaches and tools. The chapter demonstrates cluster creation through the AWS Console for manual control. It covers automated cluster creation using the eksctl command-line tool. The content explores infrastructure as code options using AWS CDK. Terraform-based cluster deployment strategies are explained. The chapter covers Pulumi as an alternative IaC solution. Comparison of different approaches helps readers choose the right tool. Finally, it addresses common issues and best practices.

[Chapter 8: Accessing and Configuring Elastic Kubernetes Service Clusters](#ch08.xhtml) - In-depth exploration of cluster access methods and configuration options. The chapter covers kubeconfig setup and management for CLI access. It explains Kubernetes role-based access control (RBAC) in detail. The content covers AWS IAM integration with Kubernetes RBAC. Various cluster configuration aspects including version upgrades are discussed. The chapter explores logging and secrets encryption setup. Finally, it covers add-ons management and cluster updates.

[Chapter 9: Deploying Sample Apps on AWS Elastic Kubernetes Service Clusters](#ch09.xhtml) \- Practical guide to deploying applications on EKS clusters using various methods. The chapter covers namespace isolation and pod deployment strategies. It explains service creation and Ingress configuration for external access. The content explores Helm usage for package management. Storage integration patterns are demonstrated. The chapter covers deployment rollout strategies. Finally, it introduces service mesh concepts and monitoring setup.

[Chapter 10: Managing Stateful Apps on AWS Elastic Kubernetes Service Clusters](#ch10.xhtml) \- Detailed examination of stateful application management in EKS environments. The chapter covers StatefulSets and their specific use cases. It explains persistent storage options including EBS, EFS, and S3. The content covers storage class configuration and CSI driver integration. Snapshot management and data mobility strategies are discussed. The chapter addresses security considerations for stateful workloads. Finally, it covers monitoring and maintenance aspects.

[Chapter 11: Scaling AWS Elastic Kubernetes Service Workloads](#ch11.xhtml) - Comprehensive coverage of various scaling strategies in EKS environments. The chapter explores the evolution of Kubernetes scaling mechanisms. It details Horizontal Pod Autoscaler implementation and use cases. The content covers Vertical Pod Autoscaler for resource optimization. Cluster Autoscaler configuration and management are explained. The chapter introduces Karpenter as a modern scaling solution. Event-driven autoscaling patterns are discussed. Finally, it covers best practices for implementing scalable architectures.

[Chapter 12: Networking with AWS Elastic Kubernetes Services](#ch12.xhtml) \- Deep dive into networking concepts and implementations in EKS. The chapter covers pod networking fundamentals and service networking. It explains various ingress controller options and configurations. The content explores load balancing strategies with EKS. Security group configurations for pods are detailed. The chapter covers network policy implementation. Finally, it introduces advanced concepts like prefix delegation and VPC Lattice.

[Chapter 13: Securing AWS Elastic Kubernetes Service Clusters](#ch13.xhtml) - Comprehensive guide to implementing security measures in EKS environments. The chapter covers pod and node security configurations. It explains IAM roles for service accounts integration. The content explores secrets management best practices. Amazon GuardDuty integration for EKS is detailed. The chapter covers Pod Security Standards implementation. Finally, it addresses policy management and EKS Pod Identity features.

[Chapter 14: Storage Options for AWS EKS Workloads](#ch14.xhtml) - Detailed exploration of storage solutions available for EKS workloads. The chapter covers EBS integration using CSI drivers. It explains EFS implementation for shared storage needs. The content explores FSx for NetApp ONTAP integration. S3 storage patterns and use cases are discussed. The chapter covers FSx for Lustre high-performance options. Finally, it addresses cost considerations and administrative overhead.

[Chapter 15: Monitoring AWS EKS Clusters](#ch15.xhtml) - Comprehensive guide to monitoring strategies for EKS environments. The chapter explores various monitoring options available. It details AWS console monitoring capabilities. The content covers Container Insights implementation. Kubecost integration for cost management is explained. The chapter covers monitoring metrics and alerting. Finally, it addresses performance monitoring best practices.

[Chapter 16: Logging and Troubleshooting AWS EKS Clusters](#ch16.xhtml) \- In-depth coverage of logging and troubleshooting techniques for EKS. The chapter explores control plane logging configuration. It explains CloudWatch Log Insights integration. The content covers various logging components and their setup. Common troubleshooting scenarios and solutions are discussed. The chapter addresses network and authentication issues. Finally, it covers control plane logs analysis.

[Chapter 17: Integrating EKS with Other AWS Services](#ch17.xhtml) - Comprehensive guide to integrating EKS with various AWS services. The chapter covers Lambda integration patterns. It explains RDS collaboration strategies. The content explores ECS integration scenarios. CloudWatch integration for monitoring is detailed. The chapter covers DynamoDB integration patterns. Finally, it addresses optimization strategies for AWS service integration.

[Chapter 18: Continuous Integration and Continuous Deployment Pipelines for Amazon EKS](#ch18.xhtml) \- Detailed exploration of implementing CI/CD pipelines for EKS deployments. The chapter covers source code management strategies. It explains container image management. The content explores various deployment techniques. Pipeline validation and testing approaches are discussed. The chapter covers IAM role configuration for pipelines. Finally, it addresses pipeline orchestration using AWS CodePipeline.

[Chapter 19: GitOps Workflows with Amazon EKS](#ch19.xhtml) - Comprehensive coverage of GitOps implementation in EKS environments. The chapter explores various GitOps tools and frameworks. It details Argo CD and Flux implementations. The content covers configuration management with Git. Internal Developer Platform integration is explained. The chapter addresses monitoring in GitOps workflows. Finally, it covers GitOps best practices.

[Chapter 20: Backup and Disaster Recovery with Amazon EKS](#ch20.xhtml) \- In-depth guide to backup and disaster recovery strategies for EKS. The chapter covers fundamental backup approaches. It explains application-centric data protection. The content explores infrastructure backup practices. AWS Fault Injection Simulator usage is detailed. The chapter covers various DR models. Finally, it addresses backup monitoring and testing strategies.

[Chapter 21: Amazon EKS Optimization and Best Practices](#ch21.xhtml) - Comprehensive coverage of optimization strategies and best practices. The chapter explores cost optimization techniques. It details cluster upgrade strategies. The content covers various scaling considerations. Network optimization approaches are discussed. The chapter addresses reliability improvements. Finally, it covers security best practices implementation.

[Chapter 22: Data Workloads on Amazon EKS](#ch22.xhtml) - Detailed exploration of running data workloads on EKS. The chapter covers Apache Spark deployment on EKS. It explains Jupyter Notebooks integration. The content explores Apache Trino implementation. Apache Superset deployment is detailed. The chapter addresses data workload optimization. Finally, it covers monitoring and maintenance aspects.

[Chapter 23: Generative Artificial Intelligence on Amazon EKS](#ch23.xhtml) - Introduction to running generative AI workloads on EKS. The chapter covers initial setup requirements. It explains model training approaches on EKS. The content explores model inference implementations. Monitoring strategies for AI workloads are discussed. The chapter addresses performance optimization. Finally, it covers scaling considerations for AI workloads.

# Code Bundle and Coloured Images

Please follow the link to download the

***Code Bundle*** and the ***Coloured Images*** of the book:

[https://rebrand.ly/e925kzu](https://rebrand.ly/e925kzu)

The code bundle for the book is also hosted on GitHub at  [https://github.com/bpbpublications/Mastering-Elastic-Kubernetes-Services](https://github.com/bpbpublications/Mastering-Elastic-Kubernetes-Services).  In case there’s an update to the code, it will be updated on the existing GitHub repository.

We have code bundles from our rich catalogue of books and videos available at [**https://github.com/bpbpublications**](https://github.com/bpbpublications). Check them out!

Errata

We take immense pride in our work at BPB Publications and follow best practices to ensure the accuracy of our content to provide with an indulging reading experience to our subscribers. Our readers are our mirrors, and we use their inputs to reflect and improve upon human errors, if any, that may have occurred during the publishing processes involved. To let us maintain the quality and help us reach out to any readers who might be having difficulties due to any unforeseen errors, please write to us at :

**[errata@bpbonline.com](mailto:errata@bpbonline.com)**

Your support, suggestions and feedbacks are highly appreciated by the BPB Publications’ Family.

**Join our book’s Discord space**

Join the book’s Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 1Introduction to Kubernetes](#contents.xhtml#ch01a)

[Introduction](#contents.xhtml#sc2_1a)

Once upon a time, in the vast landscape of computing, applications were confined within physical servers, each operating system hosting only a single monolithic program. However, a revolutionary idea emerged, to package applications into lightweight, self-contained units called containers, allowing multiple isolated workloads to run on a single host. These containers were like tiny shipping crates, neatly packing all the necessary components, code, libraries, and dependencies, into a portable and consistent environment. With containers, applications could be easily transported and deployed across different infrastructures, eliminating the dreaded it works on my machine dilemma.

As the popularity of containers grew, so did the need for a powerful orchestrator to manage and coordinate these workloads at scale. Enter Kubernetes, an open-source container orchestration system that quickly became the undisputed industry standard for deploying and managing containerized applications across diverse infrastructure environments.

In just a few years, Kubernetes has revolutionized application architectures towards a cloud-native paradigm centered around container-packaged microservices distributed across the infrastructure. It has emerged as the kernel orchestrating container clusters, much like Linux provides the standard operating environment on raw metal servers. In just a few years, Kubernetes has become the undisputed industry standard for deploying and managing containerized workloads across infrastructure environments. How did an open-source container orchestration system dominate the cloud native landscape? Kubernetes has revolutionized application architectures towards a cloud-native paradigm centered around container-packaged microservices distributed across the infrastructure. It has emerged as the kernel orchestrating container clusters, much like Linux provides the standard operating environment on raw metal servers.

The project’s unique origins trace back to Google’s internal cluster managers Borg and resource containers that provided concepts a decade before containers gained mainstream traction. Combining massively scalable DNA with strong open governance from the Cloud Native Computing Foundation (CNCF), Kubernetes enjoyed a meteoric rise to ubiquity since its launch just half a decade ago. An unprecedented alignment of vendors rallied around Kubernetes as the consolidation target for standardizing cloud container orchestration in a remarkable fashion.

In this chapter, we will explore the unprecedented vendor support that positioned Kubernetes as the emerging standard for multi-cloud container orchestration within a few years since its launch. Understanding Kubernetes’ history provides a crucial perspective into its architectural philosophy before diving into nuts-and-bolts technical details later in the book.

Google built specialized cluster managers and container isolation mechanisms to run Ultra Large Scale (ULS) workloads. The approaches pioneered internally foreshadowed how container technology could transform deployment models once Linux containers permeated the industry. Thus, the prescient decision to donate learnings to Kubernetes led to perhaps the most impactful open-source project from the cloud-native movement this past decade. Let us dig deeper into the roots and subsequent explosion in the adoption of cloud-native technologies symbolized by Kubernetes’ meteoric ascent to dominance.

[Structure](#contents.xhtml#sc2_2a)

This chapter covers the following topics: 

*   Early virtualization technologies
*   Origins of container technology
*   Emergence of Linux containers
*   Rise of Docker
*   Need for higher order orchestration
*   Kubernetes solves orchestration needs
*   Donating to create Kubernetes: 2014
*   CNCF driving open standards
*   Cloud native landscape explodes
*   Kubernetes domination: 2017- Current
*   Kubernetes adoption journey
*   Enterprise capabilities maturity
*   Ubiquitous Kubernetes domination
*   Looking ahead 

[Objectives](#contents.xhtml#sc2_3a)

By the end of this chapter, you will have learned about the complete history leading up to Kubernetes and its current standing as the dominant container orchestration platform. Specifically, you will understand the early virtualization concepts that enabled containers, including key Linux innovations like LXC and cgroups. You will also learn about Docker's pivotal impact on container adoption. Additionally, you will be familiar with the need for orchestration tools that led to the creation of Kubernetes, including its open-source origins donated by Google. Moreover, you will comprehend Kubernetes’ explosive growth under CNCF governance, quantifying its impressive industry adoption over the past five years. Finally, you will have insight into future innovations that will expand Kubernetes’ capabilities. Overall, you will have a comprehensive perspective of Kubernetes - from its technical underpinnings and community governance to its origins, widespread ubiquity, and continuing evolution as the standard for managing container infrastructures in the multi-cloud world.

[Early virtualization technologies](#contents.xhtml#sc2_4a)

Tracing the lineages of container technology leads us on a historical journey back to the roots of virtualization concepts, dating back to the 1960s mainframe era. During this period, IBM played a pivotal role by developing hypervisor-based virtual machines for its System/360 and CP/CMS systems. These virtual machines aimed to enable multitasking processes in isolation, laying the groundwork for the concept of containerization. However, despite these early efforts, software-based virtualization capabilities remained rather rudimentary, demanding the entire booting of guest operating systems, which limited their practicality.

Moving forward in time, a significant milestone occurred in 1979 with the evolution of Unix V7, introducing the chroot command. This command allowed the creation of jails, which effectively isolated filesystems for processes, representing a step closer to container-like environments. Despite the promise embedded in this development, it would take over two decades before Unix primitives evolved sufficiently to provide comprehensive resource governance. This evolution ultimately paved the way for the reliable spawning of containers, offering a more efficient alternative to the resource-intensive virtual machines of that time.

The transition from the chroot command to a comprehensive containerization solution was not instantaneous. It took more than two decades for Unix primitives to mature and offer robust resource governance. By the time these capabilities were sufficiently developed, it was the early 2000s, and the need for a more lightweight alternative to traditional virtual machines had become increasingly apparent. This set the stage for the emergence of container technologies, marking a transformative moment in the world of software development and deployment.

The culmination of these historical developments can be traced to the early 2000s, a period when container technologies began to gain momentum. With the foundational concepts from the 1960s, the refinement of Unix primitives, and the increasing demand for lightweight, portable solutions, containerization became a feasible and attractive option. This era saw the rise of container orchestration tools, like Docker, that further streamlined the deployment and management of containerized applications, ushering in a new era of software development and deployment efficiency.

[Origins of container technology](#contents.xhtml#sc2_5a)

Kubernetes rests on the shoulders of Linux container innovations that evolved in the late 2000s. While the theories behind operating system virtualization date back to 1979 on early Unix systems, it took until the 2000s before container implementations standardized enough to package entire application environments. The inception of modern container technology paved the path for Kubernetes by providing a universal packaging format for distributed applications. Throughout the 2000s, Linux kernel innovations specifically targeted containment and governance capabilities for processes and resources through key building blocks like LXC and cgroups. Let us take a look at them:

*   LinuX Containers (LXC) expanded on the chroot primitive to offer enhanced resource isolation for containers sharing the host operating system. Rather than emulating hardware, containers efficiently share devices managed by the host Linux kernel, cutting significant overhead.
*   Control Groups (cgroups) gave fine-grained controls for allocating computing resources like CPU cycles, memory limits, and disk I/O quotas to isolated groups of processes mapped to containers. Governance of network interfaces was later added for completeness.

Technologies like LXC and cgroups are integrated with the Linux kernel to provide reliable container life-cycle management. Containers gained operating-system level process and resource isolation without the overhead of hypervisors associated with traditional VMs. This allowed far greater efficiency than VMs by sharing the host operating system instead of booting heavy guest OS images, thus consuming fewer compute resources. Without emulated devices or drivers, containers started in seconds compared to minutes for VMs, thus accelerating deployments. Containers also provided supreme application portability with guaranteed environment consistency as teams shifted workloads between on-prem data centers and cloud vendors. Encapsulating entire runtime dependencies into immutable container images gave operations teams the confidence to manage distributed applications across infrastructures.

The emergence of Docker in 2013 brought containers into the mainstream by simplifying tooling into neatly packaged solutions loved by developers. Docker made bundling applications inside containers trivial through innovations like Dockerfile declarative syntax to describe runtimes and dependencies. Friendly commands like docker build, docker push and docker run streamlined working with containers locally and deploying to registries. Docker Hub also provided shared public container images, so teams did not have to rebuild common dependencies. These capabilities led to an explosion of companies adopting containerized packaging using Docker best practices, ushering in modern cloud-native development workflows.

[Emergence of Linux containers](#contents.xhtml#sc2_6a)

The emergence of Linux containers marked a significant milestone in the evolution of container technology. One of the key advantages that propelled the popularity of containers was their ability to start almost instantly. By eliminating the need for emulated devices or drivers, containers boasted an impressive start-up time, enabling deployments to occur in a matter of seconds compared to the minutes typically required for VMs. This accelerated deployment process proved to be a game-changer, particularly in dynamic and fast-paced development environments where quick iterations and releases were paramount.

Furthermore, the adoption of containers brought about supreme application portability. Teams could seamlessly shift workloads between different infrastructures while maintaining guaranteed environment consistency. This portability was achieved by encapsulating entire runtime dependencies into immutable container images. As a result, operations teams gained a higher level of confidence in managing distributed deployments, knowing that the containerized applications would run consistently regardless of the underlying infrastructure.

The rise of containerization also had a profound impact on the way development and operations teams collaborated. With the encapsulation of dependencies into container images, development, and operations became more aligned. Developers could create and share containerized applications with all necessary dependencies included, streamlining the deployment process and reducing potential conflicts between development and production environments.

[Rise of Docker](#contents.xhtml#sc2_7a)

Docker Hub, a centralized registry, provided a platform for sharing public container images. This meant that teams no longer needed to rebuild common dependencies, fostering collaboration and reducing redundancy in the development and deployment pipelines.

The impact of Docker on the industry was profound, sparking an explosion of companies embracing containerization for packaging their applications. This trend signaled a significant shift towards modern cloud-native development practices, where containerization became a fundamental building block. The ease of use and accessibility introduced by Docker democratized the adoption of containers, making them an integral part of the software development lifecycle.

In conclusion, Docker's emergence in 2013 revolutionized the container landscape by simplifying tooling and introducing a user-friendly approach to containerization. The use of Dockerfile and straightforward commands like docker build not only made working with containers more accessible but also paved the way for consistent application runtimes. The widespread adoption of Docker, coupled with the convenience of Docker Hub, contributed to the mainstream acceptance of container technology and fueled the transition towards modern cloud-native development practices.

[Need for higher order orchestration](#contents.xhtml#sc2_8a)

As early adopters ventured into deploying containers in production environments beyond trivial applications, a new set of challenges surfaced. These challenges extended beyond the simplicity of packaging and included critical aspects such as updates, availability, and scale. While containers had revolutionized the way applications were packaged, complexity arose when dealing with the deployment of hundreds of container instances across numerous machines and ensuring their continuous operation without efficient coordination.

In response to these challenges, a series of pivotal questions arose within the technology community. How could one effectively schedule containers across clusters? What was the seamless approach to deploying new versions of applications in a containerized environment? How could monitoring be efficiently conducted for containers dispersed across diverse infrastructure? Moreover, the dilemma of handling partial outages needed to be addressed. At this juncture, there was a glaring absence of a universal method to manage container lifecycles comprehensively, spanning on-premises data centers and public cloud regions.

The push towards comprehensive container orchestration platforms gained significant momentum around 2014, coinciding with the accelerated adoption of containers. In response to the growing demand for robust container management solutions, Kubernetes emerged as a game-changer. It provided sophisticated cluster management capabilities layered on top of raw containers, akin to how Linux establishes a standardized operating environment on bare metal. Kubernetes effectively addressed the need for orchestration, bringing a level of order and control to the increasingly complex landscape of containerized applications.

The introduction of Kubernetes marked a paradigm shift, offering a standardized and efficient solution for managing container lifecycles end-to-end. It played a crucial role in taming the complexities associated with deploying, scaling, updating, and maintaining containerized applications across diverse and dynamic environments. As a result, Kubernetes became the de facto container orchestration platform, fostering a more streamlined and scalable approach to containerized application management. To summarize, as early adopters began shifting single-tier apps and microservices into production-grade container infrastructures, new complexities emerged around managing scale, availability, networking, storage, observability needs, etc, across clusters.

Much like container technologies evolved to remove the burden from developers, the need for comprehensive container orchestration capabilities gained steam by around 2014 to truly realize the promise of cloud-native automation. Kubernetes solved this need for production-grade container orchestration.

[Kubernetes solves orchestration needs](#contents.xhtml#sc2_9a)

While organizations worked on container orchestrators and cluster managers, no clear winner emerged tailored to leverage portable Linux containers until Kubernetes arrived. The industry desperately needed an open-source answer that could tame the complexity of operating container clusters at scale while avoiding lock-in beyond ubiquitous Linux containers. Leveraging over 15 years of running containers in production, Kubernetes crystallized as that consolidated kernel for container orchestration in 2014 with the perfect timing to ride the tidal wave of containerization DevOps methodologies already underway.

So, the CNCF was formed by the Linux Foundation to steward Kubernetes as the standard open-source container orchestrator with enough vendor neutrality and community momentum to avoid the pitfalls seen in fragmented platforms like OpenStack.

While containers simplified packaging apps, questions about managing large container clusters at scale remained. Inspired by the success of running ULS clusters internally, people realized similar proven container orchestration approaches could greatly benefit container deployments in the broader industry. The seeds for donating the learnings towards a portable open standard were planted, leading to Kubernetes in 2014.

[Donating to create Kubernetes: 2014](#contents.xhtml#sc2_10a)

In mid-2014, Google made the pioneering decision to donate over a decade of its container cluster management learnings to create an open-source container orchestration system designed for cloud portability. Dubbed Kubernetes, combining the Greek word for helmsman for container, the project aimed to provide a standard container orchestration platform for the industry.

This gave users immense flexibility to deploy resilient containerized applications without fear of vendor lock-in, only relying on base Linux containers. By providing clear pathways for ecosystem vendors to plug in services, Kubernetes gained quick, widespread support just as container adoption started accelerating, fueled by DevOps practices permeating enterprises adopting cloud infrastructure. Kubernetes was designed for ultimate portability to run on any infrastructure, whether public clouds or private data centers, equally well. This boundaryless goal attracted contributors ranging from independent developers to tech giants like AWS, Microsoft, and IBM, who realized Kubernetes could provide the critical kernel for next generation cloud platforms.

Such diverse community support cemented Kubernetes as the emerging standard container orchestration platform very early on, proving vital for avoiding the fragmentation that plagued past open-source innovations like OpenStack. Kubernetes provided a clear consolidation target around which the industry could standardize for using proven container clustering patterns across cloud providers. So, Kubernetes was donated as an open-source CNCF project in 2015 to power a transformation of application architecture paradigms toward cloud-native development patterns.

[CNCF driving open standards](#contents.xhtml#sc2_11a)

The newly formed CNCF provided vendor-neutral governance stewarding Kubernetes soon after it began open-sourcing in mid-2015. CNCF hosts critical cloud native technologies as impartial standards preventing fragmentation into custom offshoots. With oversight from a CNCF governing board spanning leading technology and end user companies, Kubernetes had both the consensus and technology needed to flourish. This clear open-source governance model attracted contributors to build valuable extensions without dilution across fragmented distributions.

The project’s scope expanded as capabilities were absorbed from the fast-growing ecosystem and added to the unified CNCF landscape. Service discovery features help microservices talk to each other. Improved ingress controllers now route external traffic into the cluster. Monitoring integrations provides observability. New container networking models grant flexibility. Storage and security enhancements ready stateful applications for production reliability at scale. CNCF fosters this innovation through working groups called Special Interest Groups (SIGs). Over 100 vibrant SIGs now guide everything from cluster lifecycle to instrumenting code. Such community passion keeps innovation humming across security, networking, storage, etc. Backward compatibility policies balance stability for long-term support distros favored by enterprises along with supporting shiny new features like streaming data pipelines and event-driven scale-to-zero functions.

[Cloud native landscape explodes](#contents.xhtml#sc2_12a)

Such extensive vendor support, proven design origins, and strong open governance proved the perfect launchpad to skyrocket Kubernetes adoption as container infrastructures gained serious traction. After the Linux kernel and web servers, Kubernetes has emerged as the third great open-source movement powering a transformation in application architecture paradigms towards cloud native development patterns. Practically every aspect of the modern cloud native landscape is integrated with Kubernetes as the central nervous system coordinating container clusters. Service mesh frameworks help connect microservices to each other. Monitoring integrations gives observability. Tracing distributed systems became possible. Declarative infrastructure emerged, allowing GitOps workflow. A vibrant landscape filled gaps like storage, security, networking, data flows, etc., around Kubernetes core capabilities related to deployment, scaling, and container cluster management.

Soon industry consensus cemented Kubernetes as the convergence target for cloud and containers. Kubernetes became the fastest-growing open-source project just two years after its launch in 2016 and secured certification from the CNCF as the flagship orchestration platform shortly after. By late 2020, about 78% of global organizations reported using Kubernetes in production, including practically every hyperscale cloud provider like AWS EKS, Azure AKS, Google GKE, and traditional companies like VMware, Pivotal, SUSE, IBM who built managed Kubernetes platforms showing immense trust in its capabilities.

[Kubernetes domination: 2017-current](#contents.xhtml#sc2_13a)

Today, Kubernetes unequivocally dominates container orchestration, much like Linux dominates operating systems. Global infrastructure leaders like AWS (EKS), Azure (AKS), and GCP (GKE) offer robust, fully managed Kubernetes services, indicating tremendous trust in its capabilities for running commercial workloads.

Practically every modern cloud application adopts decentralized microservices architectures with multiple components that align well with Kubernete’s distributed coordination strengths. As open-source Linux transformed application development and deployment in past decades, Kubernetes brings that same degree of systems software innovation to orchestrate container clusters optimized for cloud infrastructure runtimes. It joins Linux and HTTP as one of the most profound open-source movements, ushering a new generation of cloud native development methodologies.

Entering 2022, Kubernetes shows no signs of slowing exponential growth as practically every aspect of the broader cloud native landscape coalesces around it as the universal control plane for modern apps. The CNCF now hosts dozens of complementary Kubernetes frameworks, cementing it as the new standard kernel for distributed applications across industries from cutting-edge Silicon Valley tech disruptors to traditional brick-and-mortar enterprises modernizing legacy Java monoliths. Let us dive deeper into what exactly Kubernetes introduced as the next-generation platform for deploying and managing containers at a massive scale across diverse infrastructure environments. The picture below shows the timeline on the evolution of Kubernetes in the past decade:

![](images/Figure_1.1.png)

Figure 1.1: Kubernetes evolution timeline

[Kubernetes adoption journey](#contents.xhtml#sc2_14a)

Kubernetes solved two fundamental challenges since becoming available in mid-2015 - providing standardization for container orchestration and an extensible platform tailored for cloud native use cases. Let us see how Kubernetes catalyzed the explosion of container usage and cloud native methodologies:

*   Orchestration consolidation: While Docker provided packaging format standardization, container usage grew uncontrolled, exacerbating complexity until Kubernetes arrived as the unified container orchestrator, avoiding fragmentation seen in PaaS and IaaS efforts.
*   Aligning DevOps and PaaS: The initial Platform as a Service (PaaS) efforts witnessed prior to Kubernetes focused too heavily on abstracting infrastructure through restrictive application runtime opinions. These limited the need for control for developers and portability across clouds. Kubernetes struck the right balance, empowering DevOps teams with a reliable platform for cloud native development while automating operational concerns internally through progressive abstractions.
*   Extensibility for cloud native innovation: Kubernetes also merged concepts from container ecosystem efforts like Docker, Mesos, CloudFoundry, and Borg into an integrated control plane with a clean separation of concerns. This enabled tremendous open-source innovation, expanding integrations across observability, security, networking, storage, etc., around a consolidated Kubernetes core. Post-launch, the CNCF brought various efforts under common governance to expand capabilities while keeping Kubernetes cloud and runtime agnostic.

These factors fueled a flywheel effect, catapulting the adoption of cloud native technologies championed by Kubernetes across every industry and role - web-scale technologists, retail giants, financial institutions, IoT manufacturers, etc.

Let us look at some adoption milestones:

*   Kubernetes became the fastest growing open-source project within 2 years of launch in 2016.
*   CNCF survey reported that 78% of organizations used Kubernetes by late 2020.
*   All major public cloud platforms (AWS EKS, Azure AKS, GCP GKE) offer managed Kubernetes services.

[Enterprise capabilities maturity](#contents.xhtml#sc2_15a)

Community adoption of Kubernetes is increasing rapidly. Developers from both startups and large enterprises tend to choose Kubernetes for new projects. The maturation of key features in Kubernetes has played a significant role in building confidence among developers. This increased confidence extends even to the most demanding use cases, which are discussed as follows:

*   Scalability to 10,000 node clusters and beyond: Leveraging the historical scale lessons and multi-cluster architecture, Kubernetes gained demonstrated abilities to coordinate 10k nodes in variants like kOps, overcoming limitations around the etcd datastore.
*   Windows support: With Kubernetes agnostic to the underlying operating system, Microsoft contributed extensive Windows node support in 2018, enabling .NET applications to leverage Kubernetes capabilities.
*   Stateful application maturity: While initially built for cloud native stateless architectures, Kubernetes grew extensive StatefulSet, Operator, and StorageClass integrations for running traditional databases, legacy apps, and batch workloads reliably at scale.
*   Global scale multi-cluster federation: Technologies like VMware's Tanzu provide standard conformance testing for creating consistent Kubernetes clusters across the underlying infrastructure. Global networks can be peered at by providing a single control plane view that hides complexities around hybrid or multi-cloud deployments.
*   Service meshes: Extending on native service discovery primitives, the service mesh pattern manages reliability, security and visibility across ephemeral microservices through standalone data planes like Linkerd and Istio popularized initially by platforms like RedHat OpenShift.
*   GitOps workflow automation: Declarative application and infrastructure definitions in source control extend Kubernetes through CI/CD event driven automation to enforce operational processes ensuring consistency between environments using frameworks like ArgoCD.

These expanding capabilities propelled Kubernetes to run financial trading systems, retail inventory pipelines, IoT telemetry processing, mobile gaming backends, media encoding platforms, and even self-driving data ingestion pipelines.

[Ubiquitous Kubernetes domination](#contents.xhtml#sc2_16a)

Just half a decade from launch, practically every aspect of the broader cloud native ecosystem gravitated around Kubernetes as the kernel managing container infrastructures. No technology has unified such an extensive landscape of tools and cloud providers so quickly under common governance and standards. Let us take a look at this domination:

*   Kubernetes usage dominates containers: Industry analyst surveys like CNCF end-user community reports show container providers adopting Kubernetes soared from just 26% in early 2017 to a whopping 78% by the end of 2020, with growth showing no signs of slowing down. Kubernetes became synonymous with container orchestration.
*   Managed Kubernetes demand explodes on public clouds: All hyperscale cloud platforms answered overwhelming customer demand by launching managed Kubernetes services in 2018 - AWS EKS, Azure AKS, and Google GKE dominate container deployments on those platforms. This freed teams from operational burdens allowing focus on workloads and application innovation.
*   CNCF projects orbit around Kubernetes core: Beyond consolidating container usage, CNCF now harbors dozens of projects cementing Kubernetes as the nucleus for the wider cloud native ecosystem spanning: 
    *   Service mesh (Istio, Linkerd): Connectivity and reliability
    *   CI/CD automation (Jenkins, ArgoCD, Flux): Application deployment
    *   Telemetry stack (Prometheus, Grafana, OpenTracing): Observability
    *   Logging/Security (Fluentd, Falco): Auditing
    *   Microservice frameworks (gRPC, CoreDNS): Service discovery

The original creators of Kubernetes possibly did not anticipate Kubernetes growing arguably into one of the most profound open-source movements in recent times. But by donating technology honed at a pioneering scale, combining it with strong vendor-neutral governance and extensible architecture, Kubernetes triggered a Cambrian explosion of cloud-native methodologies and tools catalyzed by container efficiency.

[Looking ahead](#contents.xhtml#sc2_17a)

While Kubernetes has become the control plane standard for automating container clusters on IaaS infrastructure, we are likely still early in unlocking the full productivity potentials promised by cloud native architectures. New innovations build atop Kubernetes in areas like:

*   Serverless and event-driven container scaling: Autoscaling refinements allow container instances to scale down to zero during periods of inactivity, optimizing costs while staying ready to handle traffic spikes in a serverless fashion. KNative builds on Kubernetes, helping scale event-driven containerized apps. Also, there are other open-source options available, like Kubernetes Event Driven Autoscaling (KEDA).
*   Edge and IoT infrastructure integration: K3s and other lightweight Kubernetes runtimes customized for edge devices provide centralized management of distributed edge clusters all the way down to IoT and embedded devices with consistent abstractions.
*   Everything-as-code and GitOps adoption: Declarative application and infrastructure definitions stored in source control extend Kubernetes through CI/CD automation to enforce operational processes ensuring consistency between environments at higher velocity.
*   Specialized frameworks for ML and data: While Kubernetes provides general distributed systems plumbing out of the box, domain specific frameworks tailor machine learning pipelines, big data lifecycles, and other vertical needs atop Kubernetes runtimes. This also includes the emerging GenAI technologies.
*   Unifying hybrid and multi-cloud deployments: Enterprises often choose multiple public clouds and integrate on-premises infrastructure to prevent vendor lock-in. Tools like VMware Tanzu standardize Kubernetes deployments across environments while providing unified identity, security policy and operational governance.

So, while containers efficiently package apps and microservices, Kubernetes elegantly brings order out of potential chaos coordinating container lifecycles at massive scale across the modern heterogenous enterprise cloud footprint. Kubernetes has clearly emerged as the kernel for deploying and managing containerized workloads in the multi-cloud era.

[Conclusion](#contents.xhtml#sc2_18a)

This concludes an introductory history explaining Kubernetes' unique origins and evolution as an open-source CNCF project and the factors fueling such meteoric rise to ubiquity as the standard for multi-cloud container orchestration over the past half-decade.

In the next chapter, we will dive into Kubernetes architecture, components, and other technical fundamentals underpinning this revolution in cloud native application platforms.

[Questions](#contents.xhtml#sc2_19a)

1.  What command introduced in 1979 Unix V7 was an early predecessor to containers?
2.  What technology brought containers into the mainstream by simplifying tooling in 2013?
3.  What need arose as early adopters deployed containers in production beyond trivial applications?
4.  Who donated the technology that became Kubernetes to create an open-source project in 2014?

[Exercises](#contents.xhtml#sc2_20a)

1.  List three key innovations that enabled the creation of Linux containers.
2.  Explain two factors that drove the widespread adoption of Kubernetes.
3.  Describe how the Cloud Native Computing Foundation contributed to Kubernetes becoming the standard for container orchestration.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 2Kubernetes Architecture](#contents.xhtml#ch02a)

[Introduction](#contents.xhtml#sc2_21a)

Kubernetes is an open-source system for automating the deployment, scaling, and management of containerized applications. The Kubernetes architecture consists of various components that work together to provide cluster management functionality. The core Kubernetes cluster contains the master node(s) and worker node(s), sometimes referred to as the control plane and data plane accordingly. The master node runs control plane components like the application programming interface (API) server, scheduler, controller manager, etc. It manages the overall state of the cluster. The worker nodes in the Kubernetes cluster run the actual containerized applications scheduled by master components. This separation of cluster management controls logic, and application workload provides flexibility. Additional worker nodes can be added to scale out and compute capacity for running more application instances horizontally. Compute resources can be scaled dynamically without impacting centralized control logic. Kubernetes requires networking between components and pods hosting distributed application elements. The networking model abstracts physical networks presenting Internet Protocols (IPs) of pods/services. It provides communication channels between pods across nodes and services within the cluster perimeter, along with external connectivity.

Kubernetes supports orchestration for attached storage to pods that are running clustered applications. It provides data persistence beyond container lifecycles and supports features like statefulness and data sharing across containers representing pods. The volume abstraction enables mounting storage systems into containers in pods uniformly regardless of underlying storage variety. Cluster administrators can thus integrate local storage on nodes or network storage systems and make their capacity available to application developers on-demand, avoiding infrastructure details.

[Structure](#contents.xhtml#sc2_22a)

In this chapter, we will cover the following topics:

*   Fundamentals
*   Building blocks
*   Kubernetes controllers
*   Labels and selectors
*   Reconciliation model
*   Under the hood
*   The actors
*   Monolith to microservices
*   Storage
*   Reconciliation loop
*   Monitoring
*   Security

[Objectives](#contents.xhtml#sc2_23a)

By the end of this chapter, readers will understand the Kubernetes architecture building blocks, how they work together to provide automation for containerized applications, core resources provided by Kubernetes, capabilities like storage orchestration, networking, security, multi-tenancy, customizability, and higher level controllers. Readers will gain insight into architectural attributes like loose coupling, reconciliation patterns, extensibility for extensions, and the evolution of Kubernetes for modern distributed systems.

[Fundamentals](#contents.xhtml#sc2_24a)

Fundamental Kubernetes API objects like pods often provide a hosting environment. It represents single instances of applications composed of containers. Replica sets provide template pod specifications and maintain target replicas of pod instances, managing availability. Deployments build upon replica sets, adding versioned rollout capabilities to orchestrate upgrade and downscale workflows behind updating applications declaratively. Deployments encapsulate the instance self-healing of the pod, and the application releases lifecycle management capabilities, improving automation.

Services provide an abstract access layer with local Domain Name System (DNS) resolution to find application instances backing services. Multiple services represent distributed application elements; they provide loose runtime coupling between components, allow independent scaling, and update flexibility. Namespaces, partitions, cluster-level resource quota pools, and logical clusters help the multi-tenancy support. It also accesses policy segmentation which improves security. These primitives represent fundamental building blocks for modeling applications to leverage Kubernetes.

[Building blocks](#contents.xhtml#sc2_25a)

A Kubernetes cluster consists of one or more master nodes and worker nodes. The master node runs the Kubernetes control plane components, which manage the state of the cluster and make global decisions for it. The worker nodes run the containerized applications. Key components on the Kubernetes master node are given below:

*   kube-apiserver: Exposes the Kubernetes API which is used by the client, along with command line interface (CLI) tools, and components to interact with the cluster. It validates and configures data for API objects such as pods, services, and replication controllers.
*   Etcd: Consistent and highly available key-value store, it is used as Kubernetes’ backing store for all cluster data.

*   kube-scheduler: Responsible for distributing work or containers across multiple nodes. It reads pod requirements and schedules them appropriately based on resource availability.
*   kube-controller-manager: Runs controllers that regulate the state of the cluster. For example, controllers include Replication Controller, Endpoint Controller, Namespace Controller, and Service Account and Token Controllers.

The key components of the Kubernetes worker nodes are given below:

*   Kubelet: It is an agent that runs on each node to monitor assigned pods and ensure that the containers described in those pods are healthy and running.
*   Kube-proxy: It is a network proxy and load balancer for Kubernetes, and services on each worker node. It helps make services available to external parties.

Kubernetes requires a network to communicate between various components in the architecture. This includes a pod network that enables communication between pods across clusters. A service network enables communication between Kubernetes services and pods, and an external network allows external access from/to Kubernetes services. Kubernetes supports persistent storage for containerized applications to access storage volumes independently from the container lifecycle. This includes:

*   Volumes: It is an API object that represents storage mounted into containers.
*   Persistent volumes (PVs): It is the long-lived storage that is initialized by an administrator.
*   Persistent volume claims (PVCs): It is the requests that the users make for the storage.

The Kubernetes architecture allows extensibility and customization. It includes the following components:

*   Custom resources: It extends the Kubernetes API to support custom objects.
*   Operators: It has all application-specific controllers to manage custom resources.
*   Admission controllers: It intercepts requests to enforce custom requirements.
*   Service catalog: It provisions cloud services from external brokers.

The fundamental API resources in the Kubernetes architecture include the following components. All these components provide the basic building blocks for running distributed systems on Kubernetes:

*   Pod: A pod represents a group of one or more containers and resources to run an application. Containers in a pod share an IP address, IPC, hostname, and other resources. Pods abstract the underlying infrastructure complexities.
*   Service: A Kubernetes service provides a consistent endpoint, which has been already named. It is used to access a group of pods. Kubernetes services enable loose coupling between dependent pods and provide load balancing across pods. And the service group pods provide policies to access them.
*   Volumes: A Kubernetes volume enables data to survive container restarts and upgrades via attached storage. Pod volumes outlive the executable container and facilitate data sharing between containers that are running as pods.
*   Namespaces: Kubernetes supports multiple virtual clusters backed by the same physical cluster via namespaces. Namespaces partition the cluster resources between multiple users and provide isolation between teams and applications. Resource quotas can be applied per namespace.

The following figure from CNCF shows the various components of Kubernetes:

![](images/Figure_2.1.png)

Figure 2.1: Kubernetes Architecture  
(Source: [https://www.cncf.io/blog/2019/08/19/how-kubernetes-works/](https://www.cncf.io/blog/2019/08/19/how-kubernetes-works/))

[Kubernetes controllers](#contents.xhtml#sc2_26a)

Kubernetes uses controller processes to regulate the state of the cluster. Instead of manually managing pod instances, controllers handle this automatically. Some examples are given below:

*   ReplicaSet: It ensures the running of the desired number of pod replicas.
*   Deployment: It manages ReplicaSet to roll out new software versions.

[Labels and selectors](#contents.xhtml#sc2_27a)

Kubernetes provides a flexible and powerful labeling mechanism for managing objects within the cluster. Labels are key/value pairs attached to Kubernetes objects like pods and services. Labels provide identifying attributes that can be used to group objects. Selectors then allow groupings based on labels during object creation, list, and watch operations.

[Annotations](#contents.xhtml#sc3_28a)

Annotations provide a way to attach arbitrary non-identifying metadata on objects. Tools and libraries can retrieve this metadata. Annotations do not allow object grouping like labels and selectors.

[Horizontal Pod Autoscaler](#contents.xhtml#sc3_29a)

The Horizontal Pod Autoscaler automatically scales the number of pods based on observed central processing unit (CPU) utilization. This enables supporting load changes in a CPU-bound application automatically. Autoscaling policies can be configured via object fields.

[ConfigMaps and Secrets](#contents.xhtml#sc3_30a)

Sensitive data like credentials should not be baked into container images or application code. Kubernetes provides first-class resources, such as ConfigMaps and Secrets, to externalize configuration data independently.

[Security contexts](#contents.xhtml#sc3_31a)

A pod security context applies privilege/access control settings like Linux capabilities across all containers in a pod. Additionally, security contexts can be set per container to override the pod level one, if necessary.

[Network policies](#contents.xhtml#sc3_32a)

While pods and services simplify application communication, network policies secure pod networks via rules that control ingress/egress connectivity. Network policies let Kubernetes admins enforce organizational network requirements.

[Deployments](#contents.xhtml#sc3_33a)

Kubernetes deployments provide declarative updates to applications. A desired application state is described in a deployment resource, which is asynchronously maintained by Kubernetes. This provides robust rollouts/rollbacks for software deployments.

[StatefulSets](#contents.xhtml#sc3_34a)

StatefulSets manage stateful applications like databases that require stable and persistent storage with ordinal and unique identities for each replica. It is safe to delete and reschedule pods managed by StatefulSets.

[DaemonSet](#contents.xhtml#sc3_35a)

A DaemonSet ensures that a pod runs on every node in a cluster or a selection of nodes. As nodes are added/removed, pods are automatically added/removed. They provide cluster services like log collection, monitoring agents, etc.

[Job](#contents.xhtml#sc3_36a)

A job creates one or more pods to run until successful termination. It facilitates moving batch processes once they are completed in Kubernetes clusters. Unlike long-running services via deployments, completion/fail counts of batch processes can be tracked.

[CronJob](#contents.xhtml#sc3_37a)

CronJobs provides time-based job automation. They can be scheduled to run periodically or once in the future. The uses include running backups, sending emails, etc. at designated times via Kubernetes native support instead of Cron.

[Reconciliation model](#contents.xhtml#sc2_38a)

Instead of manual container/pod instance management, Kubernetes implements a controller reconciliation approach to automation based on desired state declarations. Components like ReplicaSets and deployments will be monitored by running instances against specifications that drive current toward the desired state. This separation of desired state declaration from reconciliation logic provides hands-off and self-healing capabilities that improve resilience. Extending this control loop system via custom controllers allows modeling new abstractions for domain-specific resources to be managed similarly, promoting consistency.

Higher-level controllers, like Horizontal Pod Autoscalers, encapsulate scaling logic, allowing pod compute to be tuned automatically. This is based on usage metrics to improve efficiency. Kubernetes aims to provide out-of-the-box automation for running containerized applications while allowing controllers to be used for infrastructure elements. This controller-oriented approach makes the system more adaptive to changes in underlying infrastructure. It also provides customization mechanisms to address application areas and organization-specific concerns uniformly.

Kubernetes has rapidly evolved across major releases beyond initial versions that focused on Docker container support, basic application deployment, and scaling use cases. Expanding scope covers broader distributed systems and operational concerns and provides richer capabilities. Adding StatefulSets allows stable storage/identity needs for apps like databases. Other components are also used like DaemonSets for cluster-wide auxiliary pods, Jobs for batch workflows, and SessionAffinity/nodeSelectors for topology-aware scheduling. These exemplify increased Kubernetes abstractions, catering to real-world distributed systems topology and technologies.

Enhancements like multi-container pods and custom metrics in horizontal pod autoscalers, demonstrate greater functionality depths in core capabilities in the cluster. CustomResourceDefinitions, API aggregation, and External Admission Webhooks provide extensibility mechanisms to address customization needs across diverse use cases. Federation support across clusters, enhanced security, and data protection policies illustrate greater enterprise readiness. They take place across public and private environments as Kubernetes maturation continues across releases.

Enabling centralized visibility, control, and policies across multiple physical Kubernetes clusters and availability zones. These align with the industry trajectory on distributed systems, scaling exponentially across combinations of generic and specialized hardware and topologies.

First-class support for hardware accelerators like graphics processing unit (GPUs), CPUs, Tensor Processing Units (TPUs), and vector processing units, responds to emerging trends on much greater adoption of such technologies. They are catering to various performance and efficiency requirements seen in machine learning. Visual computing, like gaming workflows etc., underpins next-generation applications. Continued investment in installation, upgrades, application portability, storage generalization, and security auditing capabilities aim to further improve overall usability. This is done to meet higher IT operational expectations as adoption spans wider production scenarios.

These architecture attributes enable simplifying, running, and containerizing applications. Matching the velocity and variety needs of modern workloads takes place by blending intelligent, turnkey automation capabilities that minimize mundane manual tasks. Customizing paths to adapt around application/infrastructure diversity across mutable deployment environments, spanning data centers and public clouds. Kubernetes aims to serve as a solid, and foundational orchestration kernel for cloud-native application. Architects leverage their sound technical design to provide cluster management, coordination, and reconciliation. The functionality and ability to model extensions as modular controllers signifies current distributed systems. Automation intends to continue to cater to greater scales and infrastructure heterogeneity.

[Under the hood](#contents.xhtml#sc2_39a)

Kubernetes distributes management responsibilities between various master node components. The API server acts as a primary gateway exposing Kubernetes API that allows users to manipulate the desired cluster state. Etcd (distributed key value store) is a consistent, distributed data store that backs the API server providing durable storage and distribution of config across multiple masters. The scheduler assigns pods to appropriate healthy nodes to achieve balanced resource usage based on policies. Various controller processes like ReplicaSet controller actively maintain the desired state for pods, service endpoints, etc. This happens through continuous reconciliation loops closing gaps between specification and observed state.

Control plane components provide policy-driven orchestration functionality that leverages underlying cluster infrastructure. It makes you realize end-user specifications like application capacity and availability requirements with minimal manual operations involved at the individual container or host level. Custom controllers extend architecture patterns allowing new resource kinds to be managed consistently. Together these supply core orchestration capabilities via separation of concern between policy-driven desired state specifications and intelligent reconciliation implementations. A higher level of automation around application life cycles draws from these fundamental control capabilities.

The kubelet represents the node agent that runs on every node to ensure that the pod containers described by masters remain healthy and run while monitoring their state. The container runtime, for example, Docker, provides operating system-level virtualization. In this, the containerized applications are defined in pods run. Kube proxy provides basic service abstraction and virtual IP-based load, balancing and facilitating access between microservices represented via collections pods. Network plugins integrate the node's host environment with cluster networking for pod connectivity within and outside the cluster perimeter.

Addons extend nodes with other capabilities like DNS and monitoring/log agents. Nodes run control logic deployed pods, facilitating cluster management along regular application pods, and infrastructure resources get divided between them. Nodes may provide computing capacity or take additional responsibilities around storage. Networking based on topology, and agent/master separation allows adapting around infrastructure where required. Node spec details capture associated capabilities that allow scheduling constraints and tradeoffs.

[The actors](#contents.xhtml#sc2_40a)

Pods represent single instances of applications that are modeled from one or more containers sharing context and resources. Containers within pods address service packaging, while pods address deployment and execution of context definition, which improves granularity separation. ReplicaSets builts pod templates, maintains availability levels through self-healing, and provides scalability. Deployments further enhance ReplicaSets to address progression and atomicity expectations around application version upgrades. This provides rollout/rollback mechanisms that minimize downtimes. StatefulSets are built on ReplicaSets with stable ordinals/storage addressing ordering and data gravity needs for systems like databases.

DaemonSets ensure that pods run on selected or all nodes in the cluster, catering to common cluster-level service needs. Together, they enable modeling applications composed of microservices that need various automation nuances around core execution and availability concerns in the cloud's native fashion while optimizing infrastructure use. Jobs run pods that accomplish batch processes that run for completion, while CronJobs provides scheduled temporal aspects. PodPresets inject common configurations into pods during creation. Pod security policies apply access restrictions to address. Inter-pod security enhances protection across deployed applications represented via pods.

Services represent microservices that provide networking abstraction to a logical set of pods and implement service capability by improving loose coupling. Service routes the traffic to appropriate pod instances that are managed by service selector labels which transparently handle health changes. Discoverability happens over flat and local domains, with name-based DNS conventions simplifying connectivity. Ingresses build on services providing externally accessible HTTP/HTTPS L4 and L7 load-balancing endpoints. By integrating the modular ingress controller, components like software/hardware and load balancers are tailored to the infrastructure environment. Together they deliver a networking model fostering easy inter-service communication.

Network policies secure pod networks via rules that control ingress and egress connectivity, allowing administrators to enforce organizational network access policies. Webhook extensions like service injectors and validators augment API semantics further. Add-ons like CoreDNS integrate DNS with Kubernetes namespace/pod/service representing resources. Collectively, they enforce pod-based application's network security, traceability, and the traffic flexibility needed via combination load balancing and sidecars. While simplifying the pod's intercommunications and internally extending outwards securely in an agnostic fashion.

Cluster networking enables communication between all components inside Kubernetes and externally bridging applications and users. Software defines overlay networks using Virtual Extensible LAN (VXLAN), and IP addresses provide pod connectivity across nodes. These are not tied to the physical network. Services integrate with cluster networking to assign virtual IPs, enabling the external exposure of pods and load balance traffic, as well as improving scalability and loose coupling. Ingress routes use services to provide externally accessible HTTP endpoints and integrate L7 capabilities like Secure Sockets Layer (SSL) termination balancing pod traffic.

CoreDNS handles cluster DNS processing based on pod/service Kubernetes API contents. Container Network Interface (CNI) plugins extend Kubernetes networking that integrates physical networks with pods providing portability across public/private cloud networks alike. Together they deliver application access flexibility spanning internal pods, and external users while abstracting networking complexity. Service mesh solutions like Istio build on these addressing micro service tracing, and security needs as Kubernetes application architectures advance.

[Monolith to microservices](#contents.xhtml#sc2_41a)

Developers package applications as container images carrying app execution. It contains stacked libraries/binaries and configurations satisfying functional invariants. Images get materialized into running containers only at pod runtime, keeping environments decoupled and enhancing portability. Pods define application deployment boundary grouping one or more container images logically while also representing atomic, mutable deployment units that are managed by Kubernetes, improving scalability. Pod configurations encapsulate various operational policies individually and individually applied at the container collection level.

Services provide endpoint abstractions for accessing pods, containing implementations catering to discovery, loose coupling, and traffic routing needs of microservices architectures. Here, multiple groups of pods may be backing one logical service for scalability or availability. Controllers like deployments and replica sets address service level scaling, upgrades, and self-healing aspects that manage pod availability over time. Together, they foster containerized application portability with cloud native management catering to modern application environments.

Higher order controllers, like deployments, operate on PodTemplates, driving versioned application rollouts gradually across availability zones or whole clusters. Daemon controllers' conjugate infrastructure node changes with pod populating requirements and maintaining cluster-wide services. Horizontal pod auto scalers are used to dynamically tune several pods/containers, match application loads responding to core metrics like CPU, and help improve resource efficiency. Federated clusters sync resources are used across availability zones to improve high availability through smart replication.

The scheduler assigns pods to optimal healthy nodes so interdependent apps get placed together, satisfies mutual locality constraints, and maximizes chances of successful scheduling. Pod affinity/antiafinity provides application collocation mechanisms. Node selectors and node affinity provide topology awareness steering workloads. Taints and tolerations enable dedicating nodes to a particular pod group avoiding others to address trust restrictions. These needs are seen in multitenant clusters sharing underlying infrastructure. Priority and pre-emption via quality of service improve resource access fairness across teams.

Resource quotas and limit ranges constrain namespace/pod-level resources. It needs to allow capacity to partition and isolate, helping multitenancy support. Persistent storage uses the application state load separation. Pod security policies enable access control restrictions per pod, preventing privilege risks. Together they deliver application deployment personalization, access controls, and resource isolation covering various security. Customization and multi-tenancy aspects arise in production environments due to concurrent and independent application access needs.

[Storage](#contents.xhtml#sc2_42a)

Kubernetes volume abstraction allows mounting storage file systems into containers portable across environments. Pod volumes provide an application state, sharing mounted storage into all containers as a part of the pod, which is associated with lifecycles. Supported volume types range from distributed storage like Gluster to cloud solutions like AWS Elastic Block Store (EBS), reflecting the Kubernetes ecosystem's breadth. Persistent volumes provisioned by cluster operators allow binding storage volumes to clusters that are provided and consumed via persistent volume claims, dynamically decoupled and improving usability. Reclaim policies govern data retention requirements upon volume release by applications that provide safety mechanisms to avoid accidental data loss and improve robustness.

Statically provisioned persistent volumes get pre-allocated by cluster administrators, while dynamic provisioning integrates with storage classes, avoiding capacity planning burdens. It allows more automation-friendly operating models to emerge, removing procurement impediments. Together, volume orchestration provides storage abstraction, sustaining the application state across pod restarts and upgrades to address stateful application needs. This happens when underlying storage services remain implementation agnostic. Kubernetes gets deployed to boost application portability across varied environments.

[Reconciliation loop](#contents.xhtml#sc2_43a)

Federation shifts clusters from being entirely autonomous towards cooperative pools allowing the use of case-specific tunable autonomy among participating groups. With cooperation semantics versioned distinctly from cluster autoscaler semantics, it increasingly advances global orchestration patterns for massively distributed applications that share a common lifecycle. Data tier resources become more readily composable at higher levels over infrastructure.

Configuration templating via tools like Jsonnet allows declaring intent capturing parameterized application installation needs with variables and conditionals for customizing deployments. Declarative infrastructure frameworks like Terraform allow torn down and recreation of precursor resource dependencies like storage volumes and network gear during cluster turn ups. It manages Kubernetes bootstrap sequencing explicitly and provides auditability. Cluster API allows for the management of the provisioning and lifecycle needs of infrastructure providers abstractly over directly interfacing platforms through Kubernetes-style. Reconciliation patterns provide greater consistency and convenience with interface abstraction.

The operator framework combines custom resources representing external systems whose lifecycle gets managed as Kubernetes objects by associated controllers relieving bespoke automation and providing service abstraction. Together they expand infrastructure management scope and improve productivity. Multi-tenancy policies around resource quota and namespaces provide capacity partitioning, and access policy isolation across teams. Addressing shared challenges by the cluster infrastructure use securely. Fair scheduling and usage metering aid capacity optimizes over time as utilization scales up gradually in shared environments by appropriate contention mitigation.

Kubernetes allows organizations to unify application deployment flows across environments by providing consistent abstractions by insulating developers from infrastructure detail changes. Pods represent encapsulated runtime by improving portability while abstracting operational differences between various container runtimes across public clouds and on-premises environments. Volume integrations cater to storage portability needs with a variety of supported volume plugins that are mapping to public cloud storage services and equivalently available premises, as well as easing data gravity challenges. This occurs due to proprietary storage system dependencies and impeding application mobility across environments.

DaemonSets ensures that pods run on selected or all nodes catering to common cluster's service needs like log/monitoring agents, storage plugins, etc. surviving cluster scaling/upgrades. Together they expand application-supported styles.

CronJob combines time and job controllers allowing workloads to be scheduled cyclically or once in the future, expanding job patterns beyond batch use cases. Pod priority and pre-emption provide resource access differentiation ability in capacity-constrained scenarios, managing demand spikes scenarios more gracefully through controlled resource contention resolutions.

Horizontal Pod Autoscalers allow pods to be auto-provisioned/decommissioned based on CPU usage metrics temporarily expanding/shrinking deployments. This is automatically based on seasonal traffic adapting to load variability patterns and allowing applications to become more resilient to traffic fluctuations. Admission control provides a mechanism to validate, shape, or modify API requests via validator/mutating webhook handlers and allows crosscutting policies on created resources. Role Based Access Control (RBACs) focus on authorization admissions to help enforce structural invariants like schema compliance, content threat detection, and similar input sanitization concerns. This happens consistently at the scale across API operations. Initializers enable asynchronous pre-initialization logic which is injected before new resources get instantiated. Helping to normalize disparate create time workflows, needing coordination across multiple infrastructure components or external protocols when workloads get loaded into the cluster. To simplify this, clients reduce the synchronous orchestration logic embedded in them to increase separation.

[Monitoring](#contents.xhtml#sc2_44a)

Kubernetes provides health/liveness endpoint probes that allow containers to be monitored actively, supplementing static exit code styles. Readiness probes determine service capability more dynamically than just process health. Together, they improve quality detection accuracy beyond crash defaults for sophisticated applications.

[Security](#contents.xhtml#sc2_45a)

RBAC authorization model allows administrators to control access to various Kubernetes resources through effectively securing actions. User roles represented via subjects can be performed over cluster-scoped resources that are expressed as objects. They are managed through role bindings. Kubernetes secrets objects provide first-class mechanisms for securely injecting credentials like cloud API keys and database passwords into application containers managed securely via object. The access policies avoid version control storage, providing data safeguards.

Network security policies allow whitelisting application traffic between pods based on rules helping to enforce least privilege traffic flows and hardening infrastructure against attacks. Image vulnerability scanning via tools like Quay/Clair during registry pulls helps detect known threats early. This demands the developer's action on risks. Pod security policies enable cluster administrators to enforce security-sensitive topology/configurations like access rights, volume types, and host namespace access. This eliminates risks associated with uncontrolled permissions requested from applications managed via namespaces representing application boundaries.

The cloud-native landscape has catalyzed the emergence of a plethora of new open-source tools leveraging the Kubernetes ecosystem and contributing adjacent capabilities. Service meshes like Istio help manage reliability and visibility needs for microservices via capabilities like tracing. Circuit breakers are offered as infrastructure layer services improving robustness. Kubernetes brings intrinsic capabilities via controller model and architectural patterns that help simplify running containerized applications matching the velocity and variety needs of modern workloads. By blending intelligent orchestration and automation capabilities minimizing, mundane manual operations across development and deployment aspects are involved in distributed systems. It aims to provide the right abstractions representing infrastructure, policies, software delivery, and runtime concerns bridging between application needs and operational realities. This allows each stakeholder group to operate in idiomatic technology spaces while fostering closer DevOps collaboration across them.

The practicality demonstrated in being able to adapt rapidly to emerging distributed systems landscape, both at scale and functionality spans, illustrates sound and technical design foundations. This helps Kubernetes serve as a solid foundation for modeling and operating modern cloud-native applications in a reconciled, extensible fashion based on organizational needs.

In summary, fundamental Kubernetes design patterns that aim to blend in simplistic infrastructure modeling. It covers operational complexities and desired state reconciliation and provides constant auto-correction that adapts to changes. The loose coupling between microservices and extensibility allows customization. Together these attributes enable simplifying running distributed applications. By presenting the right abstractions, automation, and coordination across infrastructure, applications collectively deliver portability, reliability, and efficiency at scale.

[Conclusion](#contents.xhtml#sc2_46a)

Kubernetes aims to provide the right abstractions for infrastructure, policies, software delivery, and runtime, representing concerns between applications and operations. Its fundamental design patterns blend simplistic infrastructure modeling covering complexities and auto-correction adapting to changes. Attributes like loose coupling, microservices, and extensibility for custom needs enable simplifying running distributed, portable, reliable, and efficient applications at scale.

[Questions](#contents.xhtml#sc2_47a)

1.  What are the key components in a Kubernetes architecture? What are their responsibilities?
2.  How does Kubernetes provide networking, storage, and security for applications?
3.  What are some core Kubernetes controllers? What do they automate?
4.  How does Kubernetes support customization and multi-tenancy?
5.  What architectural attributes enable Kubernetes to simplify running containerized, distributed applications?

# [CHAPTER 3Kubernetes Components](#contents.xhtml#ch03a)

[Introduction](#contents.xhtml#sc2_48a)

Kubernetes has emerged as the leading open-source platform for orchestrating containerized applications across diverse environments. Its modular architecture comprises several core components that collectively enable efficient deployment, scaling, and management of containerized workloads. This chapter aims to provide a comprehensive understanding of the key Kubernetes components, their functionalities, and how they interoperate to deliver a robust and scalable containerized application platform. The rise of containerization has revolutionized the way applications are developed, packaged, and deployed, enabling increased portability, scalability, and efficient resource utilization. However, as applications become more distributed and complex, managing containerized workloads across multiple hosts poses significant challenges. Kubernetes addresses these challenges by providing a comprehensive orchestration platform that automates the deployment, scaling, and management of containerized applications.

Kubernetes' modular design and extensive ecosystem of components offer a flexible and extensible solution for organizations of all sizes. From small-scale deployments to large-scale, mission-critical applications, Kubernetes empowers developers and operations teams to streamline their application lifecycles, optimize resource utilization, and ensure high availability and resilience. This chapter delves into the core components that power Kubernetes, their roles, and how they interoperate to deliver a robust and scalable containerized application platform, enabling organizations to unlock the full potential of containerization.

[Structure](#contents.xhtml#sc2_49a)

This chapter covers the following topics:

*   Components
*   kube-apiserver
*   etcd
*   kube-scheduler
*   kube-controller-manager
*   kubelet
*   kube-proxy
*   Addons
*   Container resource monitoring
*   Cluster-level logging
*   Networking components
*   Cluster storage components
*   Extension components

[Objectives](#contents.xhtml#sc2_50a)

The primary objective is to equip readers with a solid grasp of the Kubernetes’ components and their respective roles in managing containerized applications. By the end of this chapter, readers should have a clear understanding of the Kubernetes master and worker node components, their responsibilities, and the overall workflow involving these components. Additionally, the chapter will shed light on various addons, networking, storage, and extension components that enhance the functionality and flexibility of Kubernetes clusters.

Mastering the Kubernetes architecture is crucial for organizations seeking to leverage the full potential of containerized application deployment and management. This chapter will provide an in-depth exploration of the core components that form the foundation of Kubernetes, including the kube-apiserver, etcd, kube-scheduler, and kube-controller-manager. Readers will gain insights into the roles and responsibilities of these components, as well as their interactions within the overall Kubernetes workflow.

Furthermore, the chapter will illuminate the components specific to Kubernetes master and worker nodes, such as the kubelet and kube-proxy. Readers will understand how these components contribute to the efficient execution and management of containerized applications across a cluster. Additionally, the chapter will explore the various addons, networking solutions, storage components, and extension mechanisms that enable organizations to tailor Kubernetes to their specific requirements, enhancing its functionality and flexibility to meet diverse operational needs.

[Components](#contents.xhtml#sc2_51a)

The core Kubernetes components provide fundamental functionality like API access, scheduling, managing application lifecycles and scaling, service discovery, and container health monitoring. The components work together to enable deploying and running containerized applications on a Kubernetes cluster. The kube-apiserver exposes the Kubernetes API, which serves as the universal access layer for users and components to communicate with the cluster. The scheduler enables intelligent placement of workloads onto optimal nodes. kubelets ensure application containers remain running properly on nodes. Proxies abstract access to them while controllers drive the desired state. A Kubernetes cluster consists of one or more master nodes and worker nodes. The master node runs the Kubernetes control plane components, which manage the state of the cluster and make global decisions about the cluster. The worker nodes run the containerized applications. The key components on the Kubernetes master node include the kube-apiserver, etcd, kube-scheduler, and kube-controller-manager.

The kube-apiserver is the central component that exposes the Kubernetes API, allowing users, tools, and other components to interact with the cluster. It acts as the main entry point for all cluster management operations, validating and configuring data for various API objects such as pods, services, and replication controllers. The kube-apiserver plays a crucial role in ensuring the overall state and configuration of the cluster are maintained consistently.

The etcd component serves as the consistent and highly available key-value store used as Kubernetes' backing store for all cluster data. It provides a single source of truth for the cluster's state and configuration, enabling reliable reconciliation and self-healing capabilities. All Kubernetes API objects are persisted in etcd, ensuring data durability and facilitating efficient coordination among various components.

The kube-scheduler is responsible for distributing workloads or containers across multiple nodes within the cluster. It reads pod requirements and schedules them appropriately based on resource availability and defined policies. The kube-scheduler plays a critical role in ensuring efficient resource utilization and balanced load distribution across the cluster, enabling optimal performance and scalability. The following diagram captures the various components:

![](images/Figure_3.1.png)

Figure 3.1: Kubernetes Components

[kube-apiserver](#contents.xhtml#sc2_52a)

The kube-apiserver exposes the Kubernetes API, which is used by the Kubernetes client, CLI tools, and components to interact with the cluster. It validates and configures data for API objects such as pods, services, and replication controllers. The kube-apiserver exposes the various Kubernetes APIs that client tools and internal components use to communicate with the cluster. It allows creating, updating, deleting, and retrieving API objects like pods, deployments, and services that represent the overall state of the system in a persistent way. The kube-API server validates operation requests to ensure correctness and updates the backend cluster store appropriately, driving any necessary reconciliations like pod creation that get triggered based on changes. The kube-apiserver serves as the central gateway for all interactions with the Kubernetes cluster, enabling users and automated processes to manage and monitor the cluster's state. It acts as the primary control plane component, processing and validating all incoming API requests before propagating them to the appropriate components or updating the cluster state in the backing data store.

One of the critical functions of the kube-apiserver is to maintain the desired state of the cluster. When users or components create, update, or delete API objects, the kube-apiserver ensures that these changes are consistently applied and reflected in the cluster's overall state. It validates the requests against defined policies and constraints, ensuring that only valid and authorized operations are executed. The kube-apiserver also plays a crucial role in driving the reconciliation process. When changes occur in the cluster's desired state, the kube-apiserver triggers the necessary actions to reconcile the actual state with the desired state. For example, if a new pod is created, the kube-apiserver will initiate the process of scheduling and deploying that pod on an appropriate node within the cluster.

The kube-apiserver's horizontal scalability allows for expanding its processing capacity to handle larger clusters by running multiple replicas behind a load balancer. This scalability feature ensures that the kube-apiserver can handle an increasing volume of API requests and manage larger clusters without performance degradation. The extensible authentication modules of the kube-apiserver allow for integration with organization-specific identity systems. This integration provides access to policy controls and ensures that only authorized users and components can interact with the cluster, enhancing security and compliance in production environments.

Together, the kube-apiserver provides a unified interaction gateway into the cluster, serving as the central orchestration point for internal automation workflows and external user-driven management operations. Its comprehensive functionality, scalability, and integration capabilities make it a critical component in the Kubernetes architecture, enabling efficient and secure management of containerized applications at scale.

[etcd](#contents.xhtml#sc2_53a)

Consistent and highly available key-value store used as Kubernetes' backing store for all cluster data. etcd is a consistent and highly available distributed key-value datastore that backs the Kubernetes cluster, representing its overall state and configuration durably, allowing reliable reconciliation and self-healing capabilities. All Kubernetes API objects get persisted into etcd providing a single source of truth across components and their automation workflows. etcd serves as the backbone of the Kubernetes control plane, acting as the centralized data store for the entire cluster's state and configuration. Its role is critical in ensuring the consistency, reliability, and durability of the cluster's data, which is essential for maintaining the desired state and enabling self-healing capabilities.

By leveraging etcd's distributed architecture and consensus algorithms, Kubernetes can maintain a highly available and fault-tolerant data store. etcd replicates data across multiple nodes, ensuring that even if one or more nodes fail, the cluster's data remains accessible and consistent. This redundancy is crucial for mission-critical applications that require uninterrupted service and data integrity. All Kubernetes API objects, including pods, services, deployments, and other resources, are persisted in etcd. This centralized storage of cluster state ensures that all components within the Kubernetes ecosystem have access to a single source of truth, facilitating efficient coordination and automation workflows across the entire cluster.

Data replication, leadership election capabilities, etc., allow Kubernetes clusters to horizontally scale control plane components, providing resilience through redundancy. Replicated masters with local etcd shards handle segments of data, lowering individual instance loads. Consensus protocols ensure replication propagation if connectivity partitions arise temporarily. Together they facilitate always-on capabilities. The ability to horizontally scale the Kubernetes control plane components, including etcd, is a crucial feature for large-scale deployments. By partitioning the data across multiple etcd instances (shards), the load on individual nodes is reduced, improving overall performance and scalability. This sharding approach, combined with replication and consensus protocols, ensures that data remains consistent and available even in the event of network partitions or node failures.

The consensus protocols employed by etcd, such as Raft, ensure that data replication and leadership changes are handled in a consistent and fault-tolerant manner. If a network partition occurs temporarily, the consensus protocols ensure that data replication continues seamlessly once connectivity is restored, maintaining data integrity and preventing inconsistencies or data loss.

[kube-scheduler](#contents.xhtml#sc2_54a)

The kube-scheduler is responsible for distributing work or containers across multiple nodes. It reads pod requirements and schedules them appropriately based on resource availability. The kube-scheduler watches the apiserver for newly created pods with no assigned nodes, and evaluates their requirements and applicable hardware/policy constraints to select an optimal node to host the pod on. This facilitates balanced resource usage driving maximum utilization and performance within a cluster's current capacity envelopes. The role of the kube-scheduler is pivotal in ensuring efficient and optimal resource utilization across the Kubernetes cluster. It acts as the orchestrator, intelligently distributing workloads (containerized applications packaged as pods) among the available worker nodes based on resource requirements and availability.

When a new pod is created without being assigned to a specific node, the kube-scheduler continuously monitors the Kubernetes API server for such unassigned pods. Upon detecting an unassigned pod, the kube-scheduler evaluates its resource requirements, such as CPU, memory, storage, and any other specified constraints or affinity rules. In addition to resource requirements, the kube-scheduler also considers various hardware and policy constraints defined within the cluster. These constraints may include factors such as node labeling, taints and tolerations, resource quotas, and other cluster-wide policies that govern workload placement. By considering all these factors, the kube-scheduler employs sophisticated algorithms to select the most optimal node for hosting the pod. This decision-making process aims to achieve balanced resource usage across the cluster, maximizing utilization while ensuring that performance remains within the cluster's current capacity envelopes.

Sophisticated scheduling logic handles bin packing of heterogeneous workloads based on declared parameter needs, allowing high densities per cluster enhancing efficiency. Integration of custom plugins allows augmenting native scheduling flows with added operational and business policy contexts that address specific topology requirements and expand placement awareness. The kube-scheduler's sophisticated scheduling logic encompasses advanced bin-packing algorithms capable of handling heterogeneous workloads with varying resource requirements. By carefully considering the declared parameter needs of each pod, the scheduler can pack multiple workloads onto the same node, maximizing resource utilization and enabling high densities within the cluster.

This efficient packing of workloads not only optimizes resource usage but also enhances overall cluster efficiency by reducing the overhead associated with managing and maintaining a large number of underutilized nodes. Furthermore, the kube-scheduler's extensibility allows for the integration of custom scheduling plugins. These plugins enable organizations to augment the native scheduling flows with additional operational or business policy context. By incorporating specific topology requirements, organizations can ensure that workloads are placed on nodes that meet their unique needs, such as regulatory compliance, data locality, or performance optimization. The ability to expand placement awareness through custom plugins empowers organizations to tailor the scheduling process to their specific requirements, ensuring that workloads are deployed in an optimal and compliant manner, even in complex environments with diverse constraints and policies.

[kube-controller-manager](#contents.xhtml#sc2_55a)

The kube-controller-manager runs controllers that regulate the state of the cluster. Example controllers include the replication controller, endpoint controller, namespace controller, and service account and token controllers. The kube-controller-manager contains controllers that drive the reconciliation of the actual cluster state toward the desired state continuously. Components like the replication controller reflect desired scale levels stated via API object creations and monitor running pods taking actions to reach specified targets. Controllers thus encapsulate resilient automation logic through such control loops, closing the gap between user specifications and system realization autonomously. The kube-controller-manager is a crucial component of the Kubernetes control plane and is responsible for maintaining the desired state of the cluster. It hosts a collection of controllers, each responsible for managing a specific aspect of the cluster's state and reconciling any deviations from the desired configuration.

One of the key controllers within the kube-controller-manager is the replication controller, which ensures that the desired number of pod replicas for a given application or service is running at all times. When a pod fails or is terminated, the replication controller automatically creates a new pod to maintain the specified replica count. The endpoint controller is another important component that manages the endpoint objects, which represent the IP addresses and ports of the pods associated with a service. It continuously monitors the state of pods and updates the endpoint objects accordingly, ensuring that service requests are routed to the appropriate pods.

The namespace controller manages the lifecycle of namespaces within the cluster, creating and deleting them as required. It also ensures that objects within a namespace are properly handled when the namespace is deleted or modified. The service account and token controllers are responsible for managing service accounts and generating and distributing access tokens to authenticate and authorize requests within the cluster. These components play a crucial role in securing and controlling access to Kubernetes resources. Controllers within the kube-controller-manager continuously monitor the actual state of the cluster and reconcile it with the desired state defined by users or other components. This reconciliation process involves creating, updating, or deleting resources as necessary to achieve the specified configuration.

Components like the replication controller reflect desired scale levels stated via API object creations and monitor running pods, taking actions to reach specified targets. Controllers thus encapsulate resilient automation logic through such control loops, closing the gap between user specifications and system realization autonomously. Controllers may handle crash-loop mitigations by slowing down restart rates or autoscaling up healthier instances in response. Rollover deployments gracefully drain workloads from terminating pods. Disruption budgets ensure workload capacity levels through taints/tolerations, carefully managing change rollout impacts. Together, they add intelligent automation, enriching basic desired state functionality and significantly improving stability. In addition to maintaining the desired state, controllers within the kube-controller-manager also implement various strategies to enhance cluster stability and resilience. For example, they may mitigate crash loops by slowing down the restart rates of problematic pods or autoscaling up healthier instances to compensate for failures.

During rollover deployments, controllers gracefully drain workloads from terminating pods, ensuring a smooth transition and minimizing service disruptions. Disruption budgets and the use of taints and tolerations help controllers manage the impact of change rollouts, ensuring that workload capacity levels are maintained throughout the process. The key components on the Kubernetes worker nodes include the kubelet and the kube-proxy.

[kubelet](#contents.xhtml#sc2_56a)

kubelet is an agent that runs on each node to monitor assigned pods and ensure containers described in those pods are healthy and running. The kubelet runs on every node, reading pod manifests using the downward API, managing container life cycles, and ensuring they keep running based on those desired state declarations from the control plane to identify faults faster. The kubelet relies on interfaces with the container runtime using runtime shims to launch, monitor, and upgrade containers, maintaining application SLAs. The kubelet is a critical component that acts as the primary node agent in a Kubernetes cluster. It is responsible for ensuring that the containers within the pods assigned to a particular node are running and healthy. The kubelet continuously monitors the state of these containers and takes corrective actions if necessary to maintain the desired state.

On each node, the kubelet reads the pod manifests, which describe the desired state of the pods and their containers. It uses the downward API to obtain these manifests and other relevant information from the Kubernetes control plane. By managing the container life cycles based on these manifests, the kubelet ensures that the actual state of the containers matches the desired state declared by the control plane. The kubelet relies on interfaces with the container runtime to perform various operations, such as launching, monitoring, and upgrading containers. It uses runtime shims to interact with different container runtimes, allowing it to work seamlessly with various container technologies while maintaining application service level agreements (SLAs). The kubelet runs readiness/liveness probes, providing deeper application health signals supplementing just crashed defaults, enabling smarter recovery actions. Log providers ship container logs, facilitating debuggability. Metrics export helps detail fine-grained resource usage for optimization. Stream processors distribute shell commands across sidecar utility containers in pods, allowing simpler scriptability.

In addition to basic container monitoring, the kubelet runs readiness and liveness probes to gain deeper insights into the health of applications running within the containers. These probes provide more granular health signals beyond just detecting crashes, enabling the kubelet to take smarter recovery actions based on the application's specific needs. The kubelet also facilitates debugging and troubleshooting by integrating with log providers that ship container logs to centralized log management systems. This integration allows developers and administrators to easily access and analyze container logs, enhancing debuggability and improving incident response times. Furthermore, the kubelet supports the export of metrics related to resource usage, providing detailed insights into the consumption of CPU, memory, and other resources by individual containers. This fine-grained resource monitoring helps optimize resource allocation and identify potential bottlenecks or inefficiencies.

The kubelet also includes stream processors that enable the distribution of shell commands across sidecar utility containers within a pod. This feature simplifies scripting and automation tasks, allowing developers and administrators to execute commands and scripts across multiple containers in a consistent and streamlined manner. The container runtime provides the operating system virtualization required to run isolated containerized applications encapsulated into pods onto nodes in a cluster. By integrating with primitives like cgroups, namespaces provided by the Linux kernel a container runtimes like Docker, containerd provides resource controlled execution sandboxes abstracting those kernel interfaces providing portability. The container runtime is a crucial component that enables the execution of containerized applications on Kubernetes nodes. It provides the necessary operating system virtualization and isolation mechanisms required to run containerized applications encapsulated within pods.

The container runtime integrates with low-level kernel features such as cgroups and namespaces provided by the Linux kernel. These primitives allow the container runtime to create resource-controlled execution sandboxes for containers, ensuring proper isolation and resource allocation. Popular container runtimes like Docker and containerd abstract away the complexities of interacting directly with these kernel interfaces, providing a more user-friendly and portable experience for running and managing containers. By supporting the OCI interface specifications for container image distribution and runtime management, additional container runtimes like CRI-O, rkt can execute the same workloads providing alternatives to Docker container dependence, improving wider compatibility across more platforms like kata containers for confidential computing expanding the scope. To promote portability and interoperability, Kubernetes supports the Open Container Initiative (OCI) specifications for container image distribution and runtime management. This support enables the use of various container runtimes beyond Docker, expanding the compatibility of Kubernetes across different platforms and environments.

Container runtimes like CRI-O and rkt, which adhere to the OCI specifications, can execute the same workloads as Docker, providing alternatives and reducing dependence on a single container runtime technology. This flexibility allows organizations to choose the container runtime that best suits their specific requirements and infrastructure. Additionally, the support for OCI specifications enables the adoption of specialized container runtimes like Kata Containers, which are designed for confidential computing scenarios. These runtimes offer enhanced security and isolation features, expanding the scope of Kubernetes deployments to meet diverse security and compliance requirements. Overall, the adherence to open standards and the ability to leverage multiple container runtimes contribute to the versatility and wide applicability of Kubernetes across various platforms and use cases.

[kube-proxy](#contents.xhtml#sc2_57a)

kube-proxy is a network proxy and load balancer for Kubernetes services on each worker node. It helps make services available to external parties. The kube-proxy runs on each node providing basic service abstraction and load balancing for applications via virtual IPs that cluster administrators can expose externally. It reflects services defined via the API server onto iptables rules, providing local endpoint connections with round-robin load spreading by dynamically mapping remote service endpoint IPs, allowing simplified application access conventions internally. With the service topology moving to CoreDNS and external cloud provider LB integrations planned longer term, kube-proxy aims to focus on last mile selection and discovery problems simplifying components while improving efficiency. The kube-proxy component plays a crucial role in enabling network communication and load balancing for services within a Kubernetes cluster. It runs on each worker node and acts as a network proxy and load balancer, facilitating access to services from both internal and external parties.

One of the primary functions of kube-proxy is to provide a basic service abstraction layer for applications running within the cluster. It achieves this by exposing virtual IP addresses that cluster administrators can make accessible to external parties, enabling communication with the services running inside the cluster. Internally, kube-proxy reflects the services defined via the Kubernetes API server onto a set of iptables rules. These rules enable local endpoint connections within the cluster, allowing pods to communicate with services seamlessly. Kube-proxy dynamically maps the remote service endpoint IPs, ensuring that requests are load-balanced across the available pods using a round-robin algorithm.

This load balancing mechanism simplifies application access conventions within the cluster, as pods can access services using a single virtual IP address, without needing to be aware of the specific endpoint IPs of the individual pods backing the service. This abstraction layer enhances flexibility and scalability, as services can be scaled up or down without impacting the clients accessing them. However, as the service topology in Kubernetes evolves, the responsibilities of kube-proxy are shifting. With the introduction of CoreDNS for service discovery and the integration of external cloud provider load balancers, the focus of kube-proxy is gradually moving towards addressing last-mile selection and discovery problems.By concentrating on the final stages of service discovery and load balancing, kube-proxy aims to simplify its components and improve overall efficiency. This approach aligns with the broader goal of leveraging more specialized and dedicated components for specific tasks, reducing the complexity and overhead associated with maintaining a monolithic proxy component. As Kubernetes continues to evolve, the role of kube-proxy is likely to adapt further, benefiting from the integration of new technologies and architectural improvements. The ultimate objective is to provide a seamless and efficient service discovery and load balancing experience while minimizing the overhead and complexity of the underlying components. By embracing modular design principles and leveraging specialized components for specific tasks, Kubernetes can better accommodate the diverse and changing needs of modern applications, ensuring optimal performance, scalability, and flexibility in service delivery.

[Addons](#contents.xhtml#sc2_58a)

Addons extend Kubernetes clusters with capabilities like CoreDNS based automated DNS naming/discovery between pods and services, Grafana/Prometheus pipelines for metrics collection/visualization, Elastic stack for log aggregation/analytics and web UIs for simplified visibility into application components running across containers and nodes in the cluster. By modeling addon capabilities also as native Kubernetes resources allow leveraging portability and orchestration capabilities like auto healing pods crashes through controllers improving reliability. Helm charts workflow installations further ease deploying complex addons using revision controlled declarative specifications applicable across environments. Operators automate lifecycle management of such addons applications. Kubernetes addons are a powerful mechanism for extending the core functionality of Kubernetes clusters. These addons provide a wide range of capabilities, from automated DNS naming and discovery to metrics collection, log aggregation, and user interfaces for simplified visibility into applications running across containers and nodes within the cluster.

One of the key addons is CoreDNS, which provides automated DNS naming and discovery between Kubernetes resources like pods and services. By leveraging standard DNS naming conventions, CoreDNS retrieves data about pods and services from the Kubernetes API and automatically programs the appropriate DNS records to serve discovery requests. The Domain Name System (DNS) cluster addon like CoreDNS provides naming and discovery between Kubernetes resources like pods and services using standard DNS naming convention by retrieving data like pods, services from the Kubernetes API and automatically programming the appropriate DNS records serving discovery requests. This makes inter pod connectivity remain abstracted from the volatility of pod Ips, allowing more reliable service orientations, simplifying architecture patterns, and reducing dependency between components across namespaces while being dynamically resolvable. Expanded DNS policies provide greater customizability over behavior.

By abstracting inter-pod connectivity from the volatility of pod IPs, CoreDNS enables more reliable service-oriented architectures. This abstraction simplifies application patterns and reduces dependencies between components across namespaces, as connectivity is dynamically resolvable. Furthermore, expanded DNS policies in CoreDNS provide greater customizability over its behavior, allowing organizations to tailor it to their specific requirements. The UI addon provides a simplified ready only general purpose web interface for visibility into applications running on a Kubernetes cluster across nodes and containers providing figurative maps. It allows managing containers, pods, services, and deployments to assemble applications leveraging Kubernetes capabilities, monitoring resource usage metrics, and improving usability. Using dashboard views to graphically visualize application workload dynamics over time helps develop intuition, accelerating learning. You can drill down from higher order workloads to individual pods helps tracing monitoring holistically during investigations. The customizable Grafana dashboards help focus metric visibility, catering to role goals, allowing noise reduction, and improving productivity.

The Kubernetes UI addon offers a user-friendly web interface that provides visibility into applications running across containers and nodes within the cluster. This interface acts as a visual map, allowing users to manage containers, pods, services, and deployments, leveraging the powerful capabilities of Kubernetes. One of the key features of the UI addon is the ability to monitor resource usage metrics, enhancing the overall usability of the Kubernetes cluster. By presenting graphical visualizations of application workload dynamics over time, the UI addon helps users develop intuition and accelerate learning about their applications' behavior. Users can drill down from higher-order workloads to individual pods, enabling holistic tracing and monitoring during investigations. This granular visibility is invaluable for troubleshooting and optimizing application performance.

Additionally, the UI addon integrates with Grafana, a powerful visualization tool for metrics. Customizable Grafana dashboards help focus metric visibility, catering to the specific goals and responsibilities of different roles within an organization. By reducing noise and presenting relevant metrics, these dashboards improve productivity and enable more effective decision-making. The Grafana/Prometheus pipeline is another essential addon for metrics collection and visualization within Kubernetes clusters. Prometheus collects and stores time-series metrics from various sources, including Kubernetes resources like pods and nodes. Grafana, on the other hand, provides a powerful visualization interface for analyzing and understanding these metrics. The Elastic stack addon enables log aggregation and analytics for Kubernetes clusters. By collecting and centralizing logs from containers and nodes, the Elastic stack simplifies log management and facilitates advanced log analysis and search capabilities. This addon is particularly valuable for debugging, security investigations, and monitoring application and system behavior.

By modeling addon capabilities as native Kubernetes resources, organizations can leverage the portability and orchestration capabilities of Kubernetes for these addons. This approach allows for auto-healing of addon pod crashes through controllers, improving overall reliability and resilience. Moreover, the use of Helm charts and declarative specifications further streamlines the deployment and management of complex addons across various environments. Helm charts provide a workflow for installing and upgrading addons using revision-controlled, declarative specifications, ensuring consistency and reproducibility. Operators, another powerful feature of Kubernetes, automate the lifecycle management of addon applications. These custom controllers encapsulate the operational knowledge and best practices for managing specific addons, simplifying their deployment, scaling, and maintenance within the Kubernetes ecosystem.

[Container resource monitoring](#contents.xhtml#sc2_59a)

The container resource monitoring addon based on Prometheus scrapes and stores operational time-series metrics like CPU, memory, filesystem, and network usages on containers, pods, and nodes across applications. Dashboard visualizations help easily correlate symptoms, improving diagnostics productivity while data feeds into cost analysis pipelines, aiding optimization. Long term metric retention allows tracking usage growth patterns, helping plan resource capacity expansion needs ahead of time based on predictive models instead of reactive models, reducing service disruption risks. Granular labeling dimensions enables queries to slice and dice data along multiple categorical vectors like namespaces, pods, containers etc, providing flexibility catering to diverse analysis needs.

By having a consolidated view of resource utilization across the container infrastructure, operations teams can quickly triage performance issues and pinpoint bottlenecks. The Prometheus data source allows the construction of advanced queries to uncover insights that may be obscured in individual component views. For example, correlating spikes in network traffic to a particular microservice can reveal potential hotspots to investigate. The metrics collected go beyond just real-time monitoring, though. Analyzing historical usage trends provides visibility into demand patterns and projecting future capacity requirements. This enables proactive scaling decisions before hitting resource constraints, minimizing the operational disruption caused by unplanned scaling events.

From a cost optimization perspective, having granular multi-dimensional data enriches analysis opportunities. Queries can accurately attribute resource consumption metrics to different organizational units, projects, or namespaces. This fine-grained visibility allows drilling down on cost drivers and identifying areas for potential efficiency improvements. The monitoring data pipelines do not operate in isolation either. Outputting utilization metrics to centralized data platforms allows for combining this operational data with other business data sources. For example, tying resourcing consumption to product metrics could reveal optimization opportunities.

Overall, having this comprehensive monitoring solution provides operations teams with a powerful tool for maintaining healthy and cost-efficient container environments. Its flexibility allows both performing laser-focused component analysis as well as stepping back to analyze holistic cross-cutting resource patterns. With prevention being better than cure, the long-term trend insights minimize disruptive firefighting.

[Cluster-level logging](#contents.xhtml#sc2_60a)

The cluster logging addon based on Elasticsearch/Fluentd aggregates logs streamed from different containerized applications across different nodes in the cluster and stores them centrally after enriching with metadata like timestamps, namespaces, pod IP etc. This helps accelerate security investigations, root cause analysis and audit reviews via high cardinality extractable searches catering to diverse debug needs. With modern distributed applications packaged as microservices spanning multiple containers, debugging issues requires stitching together logs from all these disparate components. The cluster logging solution addresses this by collecting logs from every container across the cluster into a unified data store. Enriching these logs with relevant metadata further enhances their searchability.

From an operations standpoint, having this centralized log repository enables rapidly triaging application failures and troubleshooting performance issues. Queries can quickly isolate relevant log statements based on criteria like timestamps, pod IPs, or container names. This targeted search ability reduces the mean time to resolution. The solution proves invaluable for security teams as well when investigating potential threats or misuse incidents. Analysts can construct searches to extract relevant audit logs across different data sources. The ability to correlate signals from different vantage points provides a comprehensive multi-dimensional view, aiding quicker root cause analysis.

Log data is not just invaluable for reactive purposes, though. Proactive analytics can uncover patterns and anomalies that may indicate emerging issues before they escalate. Machine learning capabilities can continuously analyze log streams to detect potential problems and trigger automated remediations. The pluggable architectures of Elasticsearch and Fluentd provide flexibility to extend logging capabilities. Custom parsers can be defined to extract app-specific semantics from unstructured logs. Data can also be seamlessly piped to other analytics platforms for wider integration with business intelligence systems.

Overall, the cluster logging solution addresses a key requirement for having cohesive visibility into operations across a disaggregated containerized application architecture. Its search speed, scalability, and enrichment features empower various stakeholders like operators, developers, and security analysts to efficiently derive insights and maintain system health.

[Networking components](#contents.xhtml#sc2_61a)

Networking components enable communication between the various elements inside a Kubernetes cluster, like pods running distributed application elements across nodes, along with external access to exposed services from users outside the cluster perimeter. A Kubernetes network model needs to balance functional needs like pod/service communications and ingress traffic routing along with operational aspects like portability across cloud providers and on-premise platforms leveraging physical network gear. The network policy engine allows administrators to enforce organizational policies governing traffic between pods more granularly. Addressing micro-segmentation needs beyond default allows all postures. Rules selection pods/IP blocks for ingress/egress connectivity constraints further harden security. Implementation portability is delivered via CNI abstractions.

Ingress controllers handle routing external users' traffic to Kubernetes cluster services by load balancing requests after TLS termination functionality into pods backing them. Controllers may balance traffic on L4 spread using available nodes or more advanced L7 content routing with blue/green deployment capabilities. CoreDNS, as the cluster DNS server, provides naming/discovery of Kubernetes resources for inter-pod connectivity by retrieving data like pods, services, and endpoints details from the Kubernetes API, automatically programming DNS records and serving them to discovery requests, improving reliability over configuration file-driven approaches. By handling cluster DNS natively as an internal addon, allows customizing DNS behavior to suit wider variety of preferences around pod domain namespace policies improving personalization catering to multiple trust boundaries emerging especially across multi-tenant clusters shared by departments with compatibly more diverse naming preferences to simplify operations.

The core Kubernetes networking model is based on a flat virtual network that groups cluster nodes into a single network space. Within this space, each pod receives a unique IP address allowing pods to communicate across nodes without requiring layer 3 routing or network address translation (NAT). While simplifying connectivity, large flat networks can raise scalability concerns as cluster sizes grow. To address these scaling challenges and enable advanced capabilities like service meshes, overlay networks built on different architectural approaches are often deployed. These overlay networks create virtual data planes on top of the underlying physical networks. Popular implementations like Calico use the BGP routing protocol to distribute routes between virtual network components efficiently.

From an operational standpoint, the pluggable Container Network Interface (CNI) abstraction allows deploying different network providers in a cloud-agnostic manner. This portability avoids vendor lock-in and simplifies migrating workloads across hybrid environments spanning public clouds and on-premise data centers. With cloud providers offering differing internal network architectures, the CNI abstraction layer eases the adoption of best-of-breed solutions.

[Cluster storage components](#contents.xhtml#sc2_62a)

Storage components help simplify persistent storage management for containerized applications on Kubernetes clusters by providing standardized mechanisms for diverse backend storage systems to be mounted into application pods transparently based on declared capacity requirements. Kubernetes storage architecture aims to foster portability, insulating applications from specifics of storage solutions, giving them independent life cycles controlled via operators. Kubernetes volumes enable attaching network or locally mounted storage devices that persist beyond container crust, allowing pods to host stateful workloads needing either data sharing across containers co-located in pods or durable storage beyond lifecycles. A variety of volume types help integrate solutions ranging from cloud disks over NFS to storage arrays.

Persistent volumes provide a mechanism for administrators to allocate storage capacity independent of application consumer pods managed through on-demand volume claims, improving productivity through the separation of duties. Reclaim policies delete or retain data on volume cleanups, adding safety against accidents. Volume expansion allows resizing allowing incremental growth. Together, Kubernetes volume management provides storage portability, orchestration, and automation capabilities covering application state management requirements consistently across environments, reducing platform dependence while coordinating lifecycle controls between infrastructure operators and application developers, improving operational agility. The core Kubernetes storage primitives like volumes and persistent volumes are designed around separation of concerns between different stakeholder personas. Application developers declare storage requirements while cluster administrators provision and configure the storage backends to fulfill those needs. This loose coupling provides flexibility to application teams leveraging diverse storage solutions chosen by operations tailored to specific cost, performance, and availability requirements.

Persistent volume claims act as a logical abstraction layer enabling portability of storage needs across different environments. They shield application teams from underlying storage implementation details. The claim is dynamically bound to a specific persistent volume provisioned by storage operators. This agnostic model simplifies application deployments and enables seamless migrations across clusters with no storage reconfiguration required. Dynamic provisioning capabilities automate on-demand allocation requests reducing operational overheads. Cluster administrators can pre-define storage classes by outlining different quality of service tiers around performance, backup policies, replication needs, etc. Applications stake claims against desired classes with volume requirements satisfied automatically by corresponding provisioners communicating with storage backends. This automation coupled with self-service improves responsiveness and reduces manual toil.

[Extension components](#contents.xhtml#sc2_63a)

Extension mechanisms like custom resources, operators, and mutating admission webhooks provide avenues for users to augment built-in Kubernetes functionality with organization-specific logic at the API server level or via custom reconciliation loops. They expand modeling vocabularies, allowing for the converging of infrastructure and app entity lifecycles. Custom resource definitions added at the API server allow introducing new resource objects that extend the Kubernetes API with user defined types representing organization specific entities on top of built-in platform abstractions. Aggregated API servers further this allowing independently managed API groups. Initializers allow coordinated cross-cutting initialization flows.

Custom controllers extend reconciliation loops to managed custom resources, providing self-service automation over them like native Kubernetes objects, promoting easier lifecycle management abstractions over external systems. Controllers' presence provides confidence in systems reliability, improving usage acceptance. Admission webhooks allow intercepting API operations to inject additional validation logic for custom schemas or mutate content consistently across object creation/updates event streams, providing centralized policy enforcement points. Webhooks can enforce config policy and inject sidecars containers consistently during pod creation etc. The extensibility models in Kubernetes provide a standardized way for integrating external systems natively into the platform control plane. Custom resources allow modeling external entities from databases, CI/CD tools, service meshes etc as first-class Kubernetes objects. This convergence simplifies application delivery as components can be packaged together cohesively.

Operators are a pattern that packages custom resources with corresponding controller logic into unified units that can be lifecycle managed using standard cluster tooling. They provide self-service automation by encoding operational knowledge as code and provide event-driven reconciliation capabilities assuring the desired state. For example, a database operator may introduce DatabaseInstance as a custom resource allowing declarative instance provisioning and management through kubectl commands. Under the hood, the operator controller would translate these into calls against the database control plane APIs. Admission webhooks enable the enforcement of organizational policies and standards consistently across the entire cluster. They provide interception points for validating and transforming resources before they persist in the datastore. Policies like network constraints, security context restrictions etc. can be coded as webhooks.

[Conclusion](#contents.xhtml#sc2_64a)

Kubernetes has revolutionized the way applications are deployed, scaled, and managed in containerized environments. Its declarative model and controller-based architecture provide a robust and scalable platform for orchestrating containerized workloads across clouds. Kubernetes abstracts away the underlying infrastructure, enabling applications to be deployed consistently across diverse environments without environment-specific refactoring. Its self-healing capabilities automatically reschedule workloads from failed nodes, ensuring high availability. Meanwhile, its horizontal auto-scaling allows for the seamless scaling of resources up or down based on demand changes. Overall, Kubernetes simplifies containerized application lifecycle management from initial provisioning and scaling to maintenance like rolling updates and node upgrades.

Its modular design and comprehensive set of components provide powerful capabilities spanning networking, storage orchestration, monitoring, logging, and more. The flexibility of Custom Resource Definitions (CRD) and Operators extend Kubernetes beyond containers into managing advanced application deployments and operating external systems' lifecycle using cloud-native principles. The robust API machinery allows declarative automation programmatically through kubectl or API calls. Meanwhile, its rich access control models and network policies enforce multi-tenant security boundaries. By understanding the roles of core components like the API server, schedulers, and controllers and how they interoperate through control loops, organizations can leverage the full potential of Kubernetes to streamline deployment processes and efficiently manage resources.

As Kubernetes continues to evolve, its extensibility through custom APIs/Controllers and the vibrant ecosystem of addons, service meshes, and extensions will further contribute to its widespread adoption. The Cloud Native Computing Foundation's governance nurtures community innovation while maintaining core architectural consistency and vendor neutrality. With major cloud providers offering managed Kubernetes services, adoption barriers are lowering for enterprises embracing hybrid and multi-cloud strategies to accelerate application modernization using containers and microservices. Kubernetes' declarative approach aligns well with DevOps principles, enabling the provisioning of self-service infrastructure. As the de-facto standard orchestrator, Kubernetes is at the forefront of containerized application platforms driving ongoing innovation in the cloud-native landscape.

[Questions](#contents.xhtml#sc2_65a)

1.  Explain the role of the kube-apiserver component and its significance in the Kubernetes architecture.
2.  What is the primary responsibility of the kube-scheduler, and how does it ensure optimal placement of workloads on nodes?
3.  Describe the function of the kubelet component and its interaction with the container runtime.
4.  How does the kube-proxy facilitate service abstraction and load balancing in a Kubernetes cluster?
5.  Discuss the purpose and benefits of using Kubernetes addons like CoreDNS, Prometheus, and the Elastic stack.

[Hands-on exercises](#contents.xhtml#sc2_66a)

1.  Explain the purpose and functionality of Kubernetes Deployments and Services. Describe how a Deployment ensures the desired number of replicas for an application and manages rolling updates. Discuss the role of Services in providing a stable network endpoint for accessing the application's pods, enabling load balancing and service discovery.
2.  Explain the concept of horizontal scaling in Kubernetes and how it allows applications to scale up or down based on demand. Describe the process of scaling a Deployment by modifying the desired replica count. Discuss how Kubernetes handles scaling operations, such as creating or terminating pods, and how the Service load balances traffic across the available pods.
3.  Describe the Kubernetes Dashboard, its purpose, and the key features it provides. Explain how the Dashboard can be used to visualize and manage Kubernetes resources, including Deployments, Services, Pods, and cluster-wide resources like nodes and storage. Discuss how the Dashboard displays resource utilization metrics and other relevant information for monitoring and troubleshooting applications running in the cluster.

For each exercise, provide a theoretical explanation of the concepts, components, and processes involved without requiring the user to perform any hands-on tasks on a computer. Focus on building an understanding of the underlying principles and mechanisms of Kubernetes rather than practical implementation steps. In the next chapter, let us get started with Amazon Elastic Kubernetes Service (EKS) architecture.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 4Introduction to Amazon Elastic Kubernetes Service](#contents.xhtml#ch04a)

[Introduction](#contents.xhtml#sc2_67a)

Amazon Elastic Kubernetes Service (Amazon EKS) is a fully managed Kubernetes service offered by Amazon Web Services (AWS). It allows organizations to deploy, manage, and scale containerized applications using Kubernetes on the AWS cloud platform. Kubernetes has emerged as the de facto open-source orchestration system for containers, automating the deployment, scaling, and management of containerized applications. However, setting up and operating a Kubernetes environment can be complex, time-consuming, and requires significant operational expertise. Amazon EKS simplifies this process by providing a managed control plane, allowing organizations to focus on their applications rather than the underlying infrastructure management.

[Structure](#contents.xhtml#sc2_68a)

This chapter covers the following topics:

*   Overview
*   High availability
*   Managed infrastructure
*   Latest innovations
*   Flexibility
*   Optimized cost
*   Observability
*   Ease of use
*   Security and compliance
*   Control plane
*   Worker nodes
*   EKS cluster administration
*   Running applications on EKS

[Objectives](#contents.xhtml#sc2_69a)

By the end of this chapter, readers should be able to understand the concept of Amazon EKS and the benefits it provides for container orchestration. They will recognize the challenges of self-managed Kubernetes environments and the value proposition of Amazon EKS as a managed service. Additionally, readers will be able to identify the key components of Amazon EKS, including the control plane, worker nodes, and other architectural elements. Furthermore, readers should appreciate the benefits of using Amazon EKS, such as high availability, managed infrastructure, flexibility, cost optimization, observability, ease of use, and security and compliance.

They will also gain knowledge about EKS cluster administration best practices, including worker node management, backups, access controls, and monitoring. Finally, readers will explore different patterns and use cases for running applications on Amazon EKS, such as microservices, serverless integration with AWS Lambda, auto-scaling, batch processing, and CI/CD pipelines. By the end of this chapter, readers should have a comprehensive understanding of Amazon EKS and its capabilities for deploying and managing containerized applications on the AWS cloud platform.

[Overview](#contents.xhtml#sc2_70a)

Amazon EKS is a fully managed Kubernetes service that allows you to easily deploy, manage, and scale containerized applications using Kubernetes on AWS. Kubernetes has emerged as the de facto open-source orchestration system for containers, automating deploying, scaling, and managing containerized applications. However, setting up and operating your own Kubernetes environment can be complex, time-consuming, and require significant operational expertise.

This is where Amazon EKS comes in - it runs the Kubernetes control plane across multiple availability zones to eliminate a single point of failure. The control plane consists of at least two API servers and three etcd datastores, with data replication across them. Amazon EKS automatically detects and replaces unhealthy control plane instances, restarting them across AZs as needed. This removes the heavy operational burden of management tasks like health checks and maintenance from the customer.

You can also integrate Amazon EKS easily with other AWS services like Elastic Load Balancing for load distribution, IAM for authentication, Amazon VPC for isolation, and AWS CloudTrail for logging. This provides flexibility and an added layer of security. Some key benefits of using Amazon EKS are discussed in the following sections.

[High availability](#contents.xhtml#sc2_71a)

Distributing the Kubernetes control plane across multiple availability zones (AZs) is a critical strategy for ensuring high uptime and fault tolerance. By spreading key components across distinct data centers, such as the API server and etcd, the architecture enhances resilience. In the event of a failure in one AZ, the system automatically shifts operations to the unaffected zones, minimizing downtime and providing robust disaster recovery capabilities.

This automatic failover and recovery mechanism ensures that your applications remain accessible and operational, even in the face of localized disruptions or outages. Amazon EKS, with its managed node groups and auto scaling groups, facilitates the seamless replacement of failed instances, contributing to a self-healing Kubernetes cluster. If a worker node fails or becomes unresponsive, EKS automatically detects and replaces it with a new, healthy instance, ensuring that your application workloads continue to run without interruption.

This approach aligns with best practices for achieving high availability, allowing users to focus on their applications while AWS handles underlying infrastructure maintenance tasks. By offloading the complexities of monitoring, failover, and instance replacement to the managed service, users can concentrate on developing and deploying their applications without being burdened by the intricacies of infrastructure management.

The result is a reliable and fault-tolerant environment for deploying containerized applications in the cloud. With Amazon EKS, organizations can be confident that their Kubernetes clusters are designed for resilience, with built-in mechanisms to handle failures and ensure continuous operation. This high availability and fault tolerance capability is particularly crucial for mission-critical applications or workloads with stringent uptime requirements, as it minimizes the risk of service disruptions and ensures a seamless experience for end-users.

[Managed infrastructure](#contents.xhtml#sc2_72a)

Within the realm of Amazon EKS, the burden of managing intricate aspects like etcd, Kubernetes networking, operating systems, and the complexities of cluster scaling and upgrades is effectively lifted. AWS takes on the responsibility of handling these components seamlessly, empowering users with a managed infrastructure experience. With EKS, users are spared from the necessity of deep expertise in these underlying technologies, allowing them to direct their focus towards application development and innovation.

Instead of grappling with the intricacies of managing the control plane components, users can concentrate their efforts on building and deploying their applications, leveraging the power of Kubernetes without the associated operational overhead. The robust integration of EKS with AWS ensures that tasks such as etcd configuration and Kubernetes networking are abstracted away, enabling a more accessible and user-friendly Kubernetes environment. This tight coupling with the AWS ecosystem ensures that essential components are managed seamlessly, reducing the complexity for users and providing a streamlined experience.

By alleviating the operational intricacies of managing operating systems, EKS streamlines the deployment process, making it easier for users to leverage the power of Kubernetes within the AWS ecosystem. Users no longer need to worry about patching, updating, or maintaining the underlying operating systems, as AWS handles these tasks behind the scenes. This managed infrastructure approach not only simplifies the deployment and management of Kubernetes clusters but also reduces the risk of misconfigurations or operational errors. With AWS taking care of the underlying infrastructure, users can focus on their core competencies, accelerating innovation and time-to-market for their applications. Furthermore, the managed infrastructure experience provided by Amazon EKS enables organizations to scale their Kubernetes clusters with ease. AWS handles the complexities of scaling the control plane components, ensuring that the cluster can dynamically adapt to changing workload demands without compromising on performance or availability. By offloading the management of these intricate components to AWS, organizations can benefit from the expertise and best practices employed by AWS, ensuring that their Kubernetes clusters are optimized for performance, security, and reliability, while freeing up internal resources to focus on delivering business value.

[Latest innovations](#contents.xhtml#sc2_73a)

Staying at the forefront of the latest Kubernetes innovations is a seamless and continuous process with Amazon EKS. The service excels in integrating the most recent features directly from the upstream Kubernetes releases, ensuring that your clusters remain consistently up to date. This proactive approach means that users benefit from the latest advancements and enhancements in the Kubernetes ecosystem without the need for manual intervention. EKS takes care of the intricate process of incorporating these innovations, allowing users to focus on leveraging cutting-edge technologies in their applications.

Users no longer need to worry about manually upgrading their clusters or ensuring compatibility with the latest Kubernetes versions, as EKS handles this seamlessly in the background. The automatic integration of the latest Kubernetes features showcases EKS as a dynamic and forward-looking managed service, providing users with a platform that evolves in sync with the rapidly advancing landscape of container orchestration. This commitment to staying current ensures that users have access to the latest features, bug fixes, and performance improvements, enabling them to take advantage of the most recent developments in the Kubernetes ecosystem.

By staying ahead of the curve and incorporating the latest Kubernetes releases, EKS empowers users to future-proof their applications and infrastructure. As new technologies and best practices emerge, users can seamlessly adopt them without the need for complex migrations or disruptive upgrades, ensuring that their applications remain modern and competitive. Furthermore, the automatic integration of Kubernetes updates by EKS minimizes the risk of falling behind on security patches or critical bug fixes. 

Users can be confident that their clusters are running on the latest, most secure, and stable versions of Kubernetes, reducing the potential for vulnerabilities or operational issues. This commitment to staying current underscores EKS as a reliable choice for those seeking a Kubernetes environment that embraces and effortlessly incorporates the latest industry advancements. Whether it is new features, performance optimizations, or security enhancements, users can trust that their EKS clusters will remain at the cutting edge, positioning them for success in the rapidly evolving world of container orchestration.

[Flexibility](#contents.xhtml#sc2_74a)

Amazon EKS stands out for its remarkable flexibility, offering users the ability to tailor essential configurations to meet specific requirements while AWS efficiently oversees the core control plane. This level of customization extends to networking, security groups, IAM roles, and various other parameters, providing users with a high degree of control over their Kubernetes environment. EKS empowers users to align the platform precisely with their organizational policies and security standards, ensuring seamless integration into existing infrastructures. This flexibility allows organizations to maintain compliance with internal governance frameworks and regulatory requirements, minimizing the need for complex workarounds or compromises.

While AWS adeptly manages the underlying Kubernetes control plane, users retain the freedom to fine-tune settings and configurations, allowing for a bespoke and adaptable container orchestration environment. This customization capability enables organizations to tailor the platform to their specific needs, whether it is optimizing for performance, security, or specific workload requirements. One area where this flexibility shines is in networking configurations. Users can customize Virtual Private Cloud (VPC) settings, define network policies, and integrate with existing networking infrastructure, ensuring that their Kubernetes clusters align seamlessly with their overall network architecture and security requirements. Furthermore, EKS allows users to define granular access controls through AWS Identity and Access Management (IAM) roles, ensuring that only authorized individuals or applications can interact with the Kubernetes cluster. This level of role-based access control (RBAC) is essential for maintaining a secure and compliant environment, particularly in regulated industries or organizations with stringent security policies.

The ability to customize security group settings also contributes to the overall flexibility of EKS. Users can define inbound and outbound traffic rules, restricting access to their Kubernetes resources based on specific IP ranges, ports, or other criteria, further enhancing the overall security posture of their deployments. This flexibility not only facilitates seamless integration with diverse enterprise architectures but also positions Amazon EKS as a versatile choice for organizations seeking a tailored and secure Kubernetes solution in the cloud.

Whether an organization has specific compliance requirements, unique networking constraints, or advanced security needs, EKS can be tailored to meet those demands. By offering a high degree of customization while managing the underlying control plane, EKS strikes a balance between flexibility and managed services, allowing users to focus on their application workloads while ensuring that their Kubernetes environment aligns with their specific requirements and best practices. This adaptability makes EKS an attractive choice for organizations across various industries and sectors, as it provides the necessary flexibility to accommodate diverse use cases, enabling them to leverage the power of Kubernetes in a way that seamlessly integrates with their existing infrastructure and adheres to their unique policies and standards.

[Optimized cost](#contents.xhtml#sc2_75a)

Cost optimization takes center stage as you pay exclusively for the resources you create, devoid of any minimum fees or obligatory long-term commitments. EKS provides a financially efficient model where resources can be effortlessly generated and decommissioned based on your dynamic requirements. This pay-as-you-go approach not only ensures that you allocate resources judiciously but also aligns seamlessly with the fluctuating demands of your containerized workloads. With EKS, organizations can enjoy the benefits of a scalable and cost-effective Kubernetes solution, providing both flexibility and economic efficiency in managing container orchestration resources in the AWS cloud.

The ability to scale resources up or down instantly, coupled with the absence of long-term commitments, empowers businesses to respond swiftly to changing market conditions and optimize resource utilization. Moreover, EKS eliminates the overhead associated with managing and maintaining the underlying Kubernetes control plane. This reduced operational burden translates into cost savings, as organizations can redirect their efforts towards developing and deploying applications instead of dedicating resources to infrastructure maintenance.

By leveraging the pay-as-you-go model, businesses can effectively manage their cloud expenditure, ensuring they only pay for the resources they consume. This approach fosters financial agility and enables organizations to align their infrastructure costs with their revenue streams, promoting sustainable growth and profitability. Furthermore, EKS integrates seamlessly with other AWS services, enabling organizations to leverage a comprehensive suite of tools and technologies to enhance the security, monitoring, and scalability of their containerized applications. This integration amplifies the overall value proposition, as businesses can optimize their investments across multiple AWS services while benefiting from the cost-effective and flexible nature of EKS.

Additionally, EKS offers advanced features such as Fargate, which enables organizations to run containers without the need to provision and manage servers. This serverless approach further simplifies infrastructure management, reducing operational costs and allowing teams to focus on delivering business value. Lastly, EKS provides granular cost monitoring and reporting capabilities, empowering organizations to gain visibility into their resource consumption and associated costs. This level of transparency facilitates informed decision-making, enabling businesses to identify areas for optimization and implement cost-saving strategies effectively. In summary, EKS offers a compelling value proposition by combining the power of Kubernetes with the cost-effectiveness and flexibility of the AWS cloud. Its pay-as-you-go model, seamless integration with AWS services, and advanced features ensure that organizations can efficiently manage their containerized workloads while optimizing their cloud expenditure, fostering agility, and driving business growth.

[Observability](#contents.xhtml#sc2_76a)

Observability becomes paramount for monitoring and understanding the performance of containerized applications. AWS EKS integrates seamlessly with various observability tools, allowing users to gain insights into the health, performance, and logs of their Kubernetes clusters. Leveraging services like Amazon CloudWatch and AWS X-Ray, users can efficiently track metrics, detect anomalies, and troubleshoot issues in real time. This observability framework enhances operational efficiency, enabling organizations to proactively manage and optimize their EKS environments, ensuring a robust and reliable container orchestration experience on the AWS platforms. In the dynamic and distributed nature of containerized environments, observability plays a crucial role in ensuring application stability, performance, and availability. EKS's integration with Amazon CloudWatch empowers users to collect and analyze metrics, logs, and events from their Kubernetes clusters, providing a comprehensive view of the entire system's health.

By leveraging CloudWatch's advanced monitoring capabilities, organizations can set alarms, create dashboards, and visualize key performance indicators (KPIs) related to their EKS clusters. This level of visibility enables proactive identification of potential issues before they escalate, allowing for timely intervention and minimizing downtime. Furthermore, AWS X-Ray simplifies the process of analyzing and debugging distributed applications by providing end-to-end tracing capabilities. This service collects data from various components of an application, including containers, services, and underlying infrastructure, allowing users to gain a holistic understanding of application performance and identify bottlenecks or latency issues.

The observability capabilities offered by EKS extend beyond monitoring and troubleshooting. By analyzing log data and performance metrics, organizations can gain valuable insights into application usage patterns, resource utilization, and user behavior. These insights can inform data-driven decisions, enabling organizations to optimize their applications, allocate resources efficiently, and deliver superior user experiences. Moreover, EKS integrates with other AWS services, such as AWS Lambda and Amazon Kinesis, enabling organizations to build robust observability pipelines tailored to their specific requirements.

This integration allows for real-time processing of log data, enabling advanced analytics, anomaly detection, and automated remediation actions, further enhancing the observability and operational excellence of containerized applications. By embracing the observability capabilities of EKS, organizations can unlock the full potential of their containerized applications, ensuring optimal performance, reliability, and scalability. With a deep understanding of their applications' behavior and the ability to quickly identify and resolve issues, businesses can deliver a superior user experience while maximizing the value derived from their AWS investments.

[Ease of use](#contents.xhtml#sc2_77a)

Amazon EKS shines in providing an ease-of-use experience for deploying and managing Kubernetes clusters on AWS. With EKS, users benefit from streamlined cluster provisioning, automatic updates, and seamless integration with other AWS services. The platform simplifies complex tasks such as node scaling, ensuring that resources align effortlessly with application demands. Additionally, EKS integrates with familiar tools like AWS IAM, making it easy to manage user access and permissions.

This focus on simplicity and integration empowers users to navigate the complexities of Kubernetes with ease, fostering a user-friendly environment for containerized application deployment on AWS EKS. One of the key advantages of EKS is its ability to streamline the process of creating and managing Kubernetes clusters. Users can provision highly available and secure clusters with just a few clicks or API calls, eliminating the need for complex setup and configuration tasks. This streamlined approach reduces the time and effort required to get started with Kubernetes, allowing organizations to focus on developing and deploying their applications.

EKS also simplifies the management of Kubernetes clusters by automatically handling software updates and security patches. This feature ensures that clusters remain up-to-date with the latest versions and security enhancements, minimizing the risk of vulnerabilities and reducing the operational overhead associated with manual updates. Scaling resources is a critical aspect of managing containerized applications, and EKS excels in this area. With its seamless integration with AWS Auto Scaling, users can automatically adjust the number of worker nodes in their clusters based on application demand. This dynamic scaling capability ensures that resources are optimized, preventing over-provisioning or under-utilization, and ultimately contributing to cost efficiency. Another key advantage of EKS is its integration with AWS IAM. This integration allows organizations to leverage familiar IAM policies and roles to control access to their EKS clusters and resources. By aligning with existing AWS access management practices, EKS simplifies the process of managing user permissions, enhancing security and compliance within the containerized environment.

Furthermore, EKS seamlessly integrates with other AWS services, enabling users to leverage a wide range of tools and capabilities for enhancing their containerized applications. For example, users can leverage AWS Load Balancing services for distributing traffic, Amazon Elastic File System (EFS) for persistent storage, and AWS CloudTrail for auditing and logging, among many other services. This tight integration with the broader AWS ecosystem empowers users to build comprehensive and robust solutions tailored to their specific needs. EKS also provides a user-friendly management console and extensive documentation, making it accessible to users with varying levels of Kubernetes expertise.

This focus on ease-of-use lowers the barrier to entry for organizations seeking to embrace containerized application deployment, promoting broader adoption and accelerating innovation. By simplifying the deployment and management of Kubernetes clusters, EKS empowers organizations to unlock the full potential of containerized applications on AWS. With its streamlined provisioning, automatic updates, seamless scaling, and tight integration with AWS services and tools, EKS delivers a user-friendly experience that fosters efficiency, scalability, and operational excellence in the containerized application lifecycle.

[Security and compliance](#contents.xhtml#sc2_78a)

EKS follows AWS security best practices and conforms to compliance standards to meet security-sensitive enterprise needs. This combination of managed infrastructure with Kubernetes' portability and extensibility makes Amazon EKS the ideal platform for running container workloads in production. Whether you need a development/test environment or a mission critical application stack, EKS allows easy Kubernetes deployment and scaling on AWS. EKS clusters consist of two main components that enable the power of Kubernetes to be leveraged at scale on AWS.

They are the control plane and worker nodes. The control plane is a set of components that manage the Kubernetes cluster, including the API server, etcd, and other control plane components. AWS manages and operates the control plane across multiple availability zones, ensuring high availability and fault tolerance. Worker nodes, on the other hand, are Amazon Elastic Compute Cloud (EC2) instances that run the actual containerized applications. Users can choose from a variety of EC2 instance types and Amazon Machine Images (AMIs) to optimize their worker nodes based on their specific workload requirements. EKS also integrates with AWS Auto Scaling, allowing users to automatically scale their worker nodes based on application demand, ensuring efficient resource utilization and cost optimization.

Security is a top priority for EKS, and AWS follows industry-leading security practices to protect customer data and applications. EKS clusters are configured with secure networking and encryption at rest and in transit, ensuring data confidentiality and integrity. Additionally, EKS integrates with AWS IAM for granular access control and permission management, enabling organizations to enforce their security policies and comply with regulatory requirements.

Moreover, EKS is compliant with various industry standards and certifications, such as SOC, PCI DSS, and HIPAA, making it suitable for deploying and running mission-critical applications in regulated industries. AWS also provides extensive documentation, best practices, and guidance to help customers secure their EKS clusters and applications. The combination of Kubernetes' portability and extensibility with AWS's managed infrastructure and security best practices makes EKS a compelling choice for organizations seeking to run containerized workloads in production environments. Whether you need a development/test environment or a mission-critical application stack, EKS allows for easy Kubernetes deployment and scaling on AWS, enabling organizations to focus on building and delivering their applications while leveraging the power and flexibility of containerization.

[Control plane](#contents.xhtml#sc2_79a)

The Kubernetes control plane handles core management functions like scheduling workloads, detecting failures, replacing unhealthy nodes, allocating resources, and more. AWS operates this control plane across multiple availability zones for high uptime. The control plane is the brain of the Kubernetes cluster, responsible for orchestrating and managing the entire cluster operation. It consists of several components, including the Kubernetes API server, etcd (a distributed key-value store), the scheduler, and the controller manager. These components work together to ensure the desired state of the cluster is maintained and that applications are running as intended.

By operating the control plane across multiple availability zones, AWS ensures high availability and fault tolerance for EKS clusters. In the event of an availability zone failure, the control plane components are automatically replicated and distributed across the remaining availability zones, ensuring uninterrupted service and minimizing downtime. This redundancy and failover capability are crucial for mission-critical applications that require high uptime and reliability.

Furthermore, AWS automatically manages and maintains the control plane, including handling software updates, security patches, and upgrades. This offloads the operational burden from users, allowing them to focus on developing and deploying their applications instead of managing the underlying infrastructure. AWS follows stringent security practices and compliance standards to ensure the control plane is secure, reliable and meets regulatory requirements.

In contrast to the control plane, worker nodes are responsible for running the actual containerized applications. Users have the flexibility to choose from various EC2 instance types and Amazon Machine Images (AMIs) to optimize their worker nodes based on their specific workload requirements. This separation of concerns between the control plane and worker nodes allows for scalability, flexibility, and efficient resource utilization, enabling organizations to tailor their Kubernetes clusters to their unique needs.

[Worker nodes](#contents.xhtml#sc2_80a)

Worker nodes are the EC2 instances that run your containerized applications and workloads. You configure, scale, and manage the worker nodes, while AWS handles provisioning the infrastructure for the control plane.

Some other key architectural components include:

*   Etcd: Distributed key-value datastore that tracks cluster state and configuration. Automatically replicated across AZs.
*   API server: Entry point for all API requests to reach Kubernetes master components for management tasks. Spread across AZs.
*   Cloud Controller Manager: Allows use of AWS services like ELBs and EBS from Kubernetes native APIs.
*   Kubelet: Runs on each worker node, receiving pod/container assignments from the control plane.
*   Container runtime: Typically, Docker pulls images and runs containers. CRI compatibility allows other runtimes.
*   Kubernetes networking: Implemented using AWS CNI plugin for pod networking and Calico for network policies.
*   IAM roles and security groups: For authentication, authorization and networking security.

In essence, you manage the worker nodes based on your application needs, while AWS handles all aspects of running the control plane reliably across availability zones. The following figure captures the EKS control plane and the data plane with varying compute options. We will dive deep into the details in the upcoming chapters.

![](images/Figure_4.1.png)

Figure 4.1: EKS compute options

[EKS cluster administration](#contents.xhtml#sc2_81a)

While Amazon EKS manages provisioning and maintaining the master nodes that make up the control plane, you have full flexibility in how you configure, scale, and manage your worker nodes. Some best practices for EKS cluster administration include:

*   Use auto scaling groups: Attach your EKS worker nodes to ASGs to allow policy-based dynamic scaling.
*   Mix spot and on-demand: Leverage spot instances for cost savings along with base on-demand capacity. The ASG will handle instance replacement if Spot nodes are reclaimed.
*   Flexible instance types: Use instance types that align to your workloads based on factors like CPU, memory, storage, GPU etc.
*   Upgrade Kubernetes versions: Stay current with Kubernetes feature updates using eksctl utils upgrade-cluster.
*   Regular backups: Back up critical cluster data and configurations in S3/EBS for restore ability.
*   IAM access controls: Limit user and application access to only necessary permissions following the principle of least privilege.
*   Monitor metrics: Use services like CloudWatch Container Insights to monitor cluster health, pod logs and resource utilization.

Applying best practices for security, reliability, cost optimization and operability will enable running EKS clusters efficiently over the long term even as application needs change.

[Running applications on EKS](#contents.xhtml#sc2_82a)

EKS provides a scalable platform for deploying, managing, and modernizing applications using Kubernetes constructs. It enables organizations to split monoliths into independent microservices that have their own release cycles, scaling, and resilience, with Kubernetes managing these complex distributed applications. EKS also allows developers to use serverless services like AWS Lambda directly from application code running on EKS, providing event-driven scaling while offloading infrastructure concerns.

Organizations can set dynamic scaling policies on workloads to match traffic patterns, combining Horizontal Pod Autoscaler (HPA) and Cluster Autoscaler (CA) to respond to business metrics and automatically scale resources based on demand. EKS also facilitates efficient handling of large parallel processing workloads through Kubernetes jobs, decoupling batch processes from frontend services for better resource utilization and scalability.

Additionally, EKS enables the use of Kubernetes native APIs for rolling updates, rollbacks, and other deployment practices from CI/CD systems, along with GitOps practices for declarative infrastructure management. These patterns represent just some of the options available on EKS, which provides a flexible foundation to run cloud-native apps following established best practices for productivity and scalability.

In summary, Amazon EKS makes it easy to reliably deploy Kubernetes at scale on AWS, reducing management burdens while providing highly available infrastructure for demanding applications. It simplifies deployment and management by abstracting away complex tasks, manages the control plane components for high availability and security, and seamlessly integrates with other AWS services. EKS enables organizations to leverage the power of Kubernetes for various use cases, fostering agility, scalability, and efficient resource utilization while prioritizing security and compliance.

[Conclusion](#contents.xhtml#sc2_83a)

Amazon Elastic Kubernetes Service (Amazon EKS) provides a fully managed Kubernetes environment on the AWS cloud platform. By offloading the management and operation of the Kubernetes control plane to AWS, organizations can focus on deploying and scaling their containerized applications without the complexities of maintaining the underlying infrastructure. With its high availability, managed infrastructure, flexibility, cost optimization, observability, ease of use, and security and compliance features, Amazon EKS empowers organizations to leverage the power of Kubernetes in a seamless and efficient manner. One of the key advantages of EKS is its high availability and reliability. AWS operates the Kubernetes control plane across multiple availability zones, ensuring fault tolerance and minimizing downtime. This redundancy and failover capability are crucial for mission-critical applications that require seamless operation and uninterrupted service delivery.

EKS provides a managed infrastructure that abstracts away many of the complexities associated with setting up and maintaining a production-ready Kubernetes environment. AWS handles tasks such as provisioning, upgrades, security patches, and scaling, allowing teams to focus on building and deploying their applications instead of managing the underlying infrastructure. The flexibility of EKS enables organizations to leverage the power of Kubernetes for various use cases, including microservices architectures, serverless computing, batch processing, and continuous integration/continuous deployment (CI/CD) pipelines.

This versatility empowers teams to build and deploy applications using modern, cloud-native patterns, fostering agility, scalability, and efficient resource utilization. Cost optimization is a key consideration for organizations adopting cloud-based solutions, and EKS excels in this area. With its pay-as-you-go model, users only pay for the resources they consume, avoiding upfront costs or long-term commitments. Additionally, EKS integrates with AWS Auto Scaling, allowing organizations to automatically scale their worker nodes based on application demand, ensuring efficient resource utilization and cost optimization.

Observability is crucial for monitoring and understanding the performance of containerized applications. EKS integrates seamlessly with various observability tools, such as Amazon CloudWatch and AWS X-Ray, enabling users to gain insights into the health, performance, and logs of their Kubernetes clusters. This observability framework enhances operational efficiency, allowing organizations to proactively manage and optimize their EKS environments. EKS prioritizes ease of use, streamlining the process of deploying and managing Kubernetes clusters. Users can provision highly available and secure clusters with just a few clicks or API calls, eliminating the need for complex setup and configuration tasks. EKS also automatically handles software updates and security patches, reducing operational overhead.

Additionally, EKS integrates with familiar tools like AWS IAM, making it easy to manage user access and permissions. Finally, security and compliance are critical considerations for organizations, especially those operating in regulated industries. EKS follows AWS security best practices and conforms to various compliance standards, such as SOC, PCI DSS, and HIPAA, ensuring that customer data and applications are protected and regulatory requirements are met. By leveraging AWS's robust security measures and integrating with IAM, organizations can enforce their security policies and comply with regulatory requirements within their containerized environments.

[Questions](#contents.xhtml#sc2_84a)

1.  What is the primary benefit of using Amazon EKS compared to self-managed Kubernetes environments?
    
2.  Explain the roles of the control plane and worker nodes in an Amazon EKS cluster.
    
3.  Describe the high availability measures implemented by Amazon EKS to ensure fault tolerance.
    
4.  How does Amazon EKS enable cost optimization for running containerized applications?
    
5.  What are some best practices for EKS cluster administration regarding worker node management and monitoring?
    

[Hands-on exercises](#contents.xhtml#sc2_85a)

1.  Research and explain the different architectural components of Amazon EKS, such as etcd, API server, Cloud Controller Manager, Kubelet, and Container Runtime.
    
2.  Investigate the integration of Amazon EKS with other AWS services, such as Elastic Load Balancing, IAM, Amazon VPC, and CloudTrail. Discuss how these integrations enhance the functionality and security of EKS.
    
3.  Explore the concept of auto-scaling in Amazon EKS. Discuss the different types of auto-scaling policies (e.g., Horizontal Pod Autoscaler, Cluster Autoscaler) and their application in managing resource allocation for containerized workloads.
    

[References](#contents.xhtml#sc2_86a)

The Amazon EKS is a managed Kubernetes service provided by AWS that simplifies the deployment, management, and scaling of containerized applications on AWS infrastructure. In writing this book, we have relied extensively on the official AWS documentation, whitepapers, and online resources to ensure the accuracy and comprehensiveness of the information presented. We would like to express our gratitude to AWS for their invaluable contributions to the field of cloud-native computing and for making their expertise and knowledge accessible through their comprehensive documentation and resources. For more info, refer [https://aws.amazon.com/eks/](https://aws.amazon.com/eks/)

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 5Amazon Elastic Kubernetes Service Architecture](#contents.xhtml#ch05a)

[Introduction](#contents.xhtml#sc2_87a)

Amazon Elastic Kubernetes Service (EKS) is a fully managed container orchestration platform enabling the deployment, operation, scaling, and management of containerized applications on Kubernetes. As an AWS native service, EKS deeply integrates with supporting AWS infrastructure for computing, storage, networking, security, logging, and monitoring.

EKS removes the heavy lifting involved with deploying and maintaining a highly available Kubernetes control plane. It also stays up to date, applying the latest Kubernetes versions and security patches automatically. This allows engineering teams to focus exclusively on building and running applications without sidetracking into distributed systems administration duties.

This chapter offers an in-depth analysis of EKS architecture and best practices for usage. It is structured to provide readers with comprehensive coverage of key concepts and components spanning EKS infrastructure, resilience patterns, scaling behaviors, security controls, and integration capabilities with the broader AWS ecosystem.

[Structure](#contents.xhtml#sc2_88a)

In this chapter, we will cover the following topics:

*   EKS cluster components
*   EKS worker nodes
*   Elastic Load Balancing and networking
*   Storage options
*   EKS cluster auto scaling
*   Security best practices
*   EKS cluster upgrades and maintenance
*   Integrations with AWS services
*   Use case examples

[Objectives](#contents.xhtml#sc2_89a)

The objectives of this chapter are multifaceted and aim to equip readers with a deep understanding of Amazon EKS and its various aspects.

Firstly, the chapter aims to provide readers with a thorough understanding of the different components that make up an EKS cluster. This includes exploring the control plane, worker nodes, networking, storage, and auto-scaling functionality. By exploring these elements and how they interconnect, readers will gain a comprehensive grasp of the underlying architecture of EKS, enabling them to make informed decisions when deploying and managing their Kubernetes environments.

Secondly, the chapter dives into the security capabilities of EKS, covering critical aspects such as network policies, pod configurations, access management, encryption, and audit logging. Readers will learn about best practices for securing their EKS deployments and ensuring the safety and integrity of their applications and data.

Thirdly, the chapter examines the pros and cons of different worker node types, including Fargate and EC2, managed node groups, and self-managed nodes. It also explores strategies for seamless version upgrades, equipping readers with the knowledge to choose the most suitable worker node configuration for their specific requirements and to effectively manage their EKS clusters over time. Furthermore, the chapter highlights the native integration between EKS and other AWS services, such as Elastic Load Balancing, CloudWatch monitoring, IAM access controls, and CI/CD deployment tools. Readers will discover how to leverage these integrations to streamline EKS management and operations, ultimately improving the efficiency and reliability of their Kubernetes-based infrastructure.

Finally, the chapter provides insights into EKS cluster designs, for example, optimizations for cost savings, high availability, machine learning workloads, and production applications. By understanding these design patterns, readers will be equipped to select and deploy the appropriate EKS configuration to meet their specific business requirements and operational needs.

By the end of this chapter, readers should have a comprehensive understanding of the EKS architecture, its security features, deployment options, and integration with other AWS services. This knowledge will empower them to make informed decisions, effectively manage their EKS clusters, and optimize their Kubernetes-based infrastructure to meet their organization's goals and requirements.

[EKS cluster components](#contents.xhtml#sc2_90a)

At the core of an EKS deployment lies the EKS cluster, which comprises several interconnected components that work together to provide a robust and scalable Kubernetes environment. The first critical element is the control plane, which is responsible for managing the overall state of the Kubernetes cluster. This includes tasks such as scheduling workloads, maintaining the desired state of the cluster, and providing the API endpoint for interactions with the cluster. As a fully managed service, Amazon manages the control plane on behalf of users, ensuring high availability, security, and seamless upgrades.

The second key component of an EKS cluster are the worker nodes, which are the compute resources that run the containerized applications. EKS supports two types of worker nodes: Fargate, which is a serverless compute option, and Amazon EC2 instances, which provide more customizable and configurable compute resources. Depending on the specific requirements of the workloads, organizations can choose the worker node type that best fits their needs, balancing factors such as cost, scalability, and operational complexity. The worker nodes are responsible for executing the application pods, exposing services, and reporting the overall health of the cluster back to the control plane.

[Kubernetes control plane](#contents.xhtml#sc3_91a)

The EKS control plane is the orchestration brain behind the cluster, handling critical management functions to keep applications and workloads running optimally. It consists of the following key components, all provisioned and operated by AWS as part of the managed service:

*   Kubernetes API server nodes: EKS configures at least three API server nodes to power the control plane for high availability and fault tolerance. The Kubernetes API receives commands and workloads (known as manifests) then processes and persists them to cluster state housed in etcd (explained below). API servers also serve responses about current resources and telemetry back to client applications or operators. The configuration of at least three API server nodes in EKS ensures high availability, allowing the cluster to remain operational in case of a failure in one of the nodes. As usage scales, the EKS service grows the API server capacity accordingly through auto scaling groups.
*   etcd key value stores: etcd nodes provide a reliable, distributed data store that serves as the source of truth for cluster configuration and declarative state. All control plane components rely on etcd for coordination, so its correct provisioning is vital for functionality. Etcd's security features, including encryption, access control, and TLS authentication, help ensure the confidentiality and integrity of the cluster's data stored in etcd. EKS rotates etcd server nodes gradually to minimize downtime and control plane side effects during upgrades.
*   Cluster lifecycle manager: This EKS component monitors control plane health, routing requests across multiple API server nodes for high throughput. It manages component auto-scaling and self-healing behaviors based on cluster usage patterns. The lifecycle manager also handles complex, multi-step processes like rotating CA certificates, restarting components, and orchestrating upgrades stemming from patching or Kubernetes evolution.
*   Control plane logs collection: Given the control plane runs across multiple isolated server nodes, aggregating and centralizing the logs consistently presents challenges for operators. EKS provides integrated log collection, pulling control plane node streams into CloudWatch Logs for storage/analysis. This crucial visibility aids in monitoring, auditing, and troubleshooting workflows.

By handling these management burdens behind the scenes, EKS empowers developers to focus on applications, not infrastructure operations. The control plane, in effect, serves the needs of other cluster components rather than itself becoming a hassle to maintain. The simplicity enriches everyone’s container strategy.

[Worker nodes](#contents.xhtml#sc3_92a)

Worker nodes execute containerized applications and workloads submitted to the cluster. EKS supports two types of worker nodes - Fargate and EC2. Fargate is serverless compute managed by AWS, while EC2 provides user configurable virtual machines. Worker node infrastructure can also be provisioned and scaled automatically via auto scaling groups. More details on worker node options will be provided later.

The control plane and worker nodes are tightly integrated to coordinate cluster state as well as accept and schedule batch jobs, long running services, and any other Kubernetes workloads. Client applications submit jobs to the control plane API. The control plane then evaluates cluster resources and schedules pods onto suitable worker nodes. Node health and status feedback to the control plane so adjustments can be made.

[EKS cluster control plane](#contents.xhtml#sc3_93a)

As mentioned, the EKS control plane handles core Kubernetes functionality like the API server, etcd key value store for configuration data, cloud controller manager, and cluster autoscaler. The control plane is provided as a managed service, relieving Ops teams from hosting and managing their own Kubernetes infrastructure. Key aspects of the EKS control plane include:

*   High availability: Multiple API server nodes ensure uptime during maintenance or failures. Control plane instances are spread across isolated infra for resilience.
*   Automated version upgrades: EKS control plane stays up to date automatically, ensuring customers benefit from the latest Kubernetes features and security patches.
*   Serverless operation: No need to provision VMs, install Kubernetes, or manage infrastructure for the control plane nodes. EKS runs this as a service.
*   Elastic scaling: Control plane capacity grows based on usage needs. No upfront selection of instance sizes. Performance metrics drive appropriate scaling out/in.
*   Security hardening: Control plane implements OIDC authentication, RBAC authorization, multi-AZ isolation, private networking, and encryption. Customers manage identity integration.
*   Observability: Control plane metrics and logs feed into CloudWatch. Alerts can warn on issues or suboptimal configs proactively.
*   Pod networking: EKS enables pod communication within the cluster using plugins like the Amazon VPC CNI plugin, ensuring efficient networking for applications.
*   Backup and restore: EKS provides automated backups for etcd and supports restore operations, ensuring data integrity and recovery options for users.

The control plane processes over 75 billion Kubernetes API requests per second at peak for all EKS customers. The automated operation of this tier is essential so users can focus exclusively on their applications and workloads.

[EKS worker nodes](#contents.xhtml#sc2_94a)

EKS worker nodes execute containerized workloads scheduled by the control plane. Customers have two options for worker node infrastructure. They are discussed in this section.

[Fargate worker nodes](#contents.xhtml#sc3_95a)

Fargate provides serverless compute for EKS worker nodes, eliminating the need for customers to provision and manage virtual servers. Instead, pods run as Fargate tasks leveraging shared underlying host infrastructure fully managed by AWS. This empowers development teams to focus on applications without server administration duties. The serverless model of Fargate relieves teams from server patching, scaling, securing, and overall lifecycle management. Tasks automatically scale up and down at the individual pod level based on real-time usage metrics. New tasks start and stop in sub-second timeframes as demand fluctuates.

When pods complete work successfully, the corresponding Fargate tasks rapidly halt and free up reserved resources. This achieves fast scale to zero capacity when workloads finish. For cost savings, users pay for only active execution time used. Unlike servers, which can take minutes to bootstrap and initialize, Fargate tasks launch immediately as the shared infrastructure remains ready perpetually. This removes cold start delays when work spikes, providing instant scaling. Behind the scenes, Fargate runs EKS pod workloads securely on shared AWS host infrastructure. Multi-tenant isolation, encryption, and network policies maintain security boundaries between customers. No hosts are dedicated per account.

With precise per second billing, users pay exclusively for the exact wall clock duration of active Fargate tasks associated to workload pods. This cost model incentivizes applications to scale down when idle, only using what they need. In summary, Fargate shines for event-driven and intermittent workloads able to benefit from instant scaling, micro-billing, and serverless operations. Since Fargate abstracts away the underlying infrastructure, users have limited control over networking, storage, and other aspects that they might have more control over with traditional EC2 instances. But on the flip side, this limited operational burden allows teams to focus on applications first.

[EC2 worker nodes](#contents.xhtml#sc3_96a)

EC2 worker nodes offer EKS clusters with customizable virtual machine-based computing that is fully controlled by customers. Users can tune CPU, memory, storage, operating systems, and networking to match application needs. EC2 nodes give lower level infrastructure access compared to Fargate's serverless abstraction. Configuring EC2 worker pool capacity as auto scaling groups, capacity scales elastically. The EC2 instances run Docker plus Kubernetes components to communicate with the control plane, executing pod-defined workloads.

EC2 offers flexible instance family options from general purpose to memory optimized all the way to GPU/TPU machine learning specialty chips. This customization suits applications requiring specific infrastructure configurations. Dedicated EC2 hosts provide reliable, consistent performance characteristics without noisy neighbor interference issues occasionally plaguing shared public cloud hosts. Workloads demanding stable benchmarks prefer EC2.

Administrators can port their VM image management skills to worker nodes. Creating optimized machine images, patching, configuring bootstrap processes, and managing upgrades leverage existing AWS skills. Cost optimizing options like spot instance support, reserved capacity discounts, and auto scaling groups minimize waste, only paying for resources used. Batch workloads or periodic jobs especially benefit. In summary, EC2 worker nodes best suit applications needing configurable, dedicated compute versus sharing underlying infrastructure. The programmatic control allows administrators to architect worker pools aligned to application needs.

[Elastic Load Balancing and networking](#contents.xhtml#sc2_97a)

Services running on an EKS cluster can benefit greatly from Elastic Load Balancing (ELB) to distribute demand across pods and enable high availability across Availability Zones (AZs). As an AWS managed service, ELB offers tight integration with EKS worker nodes and the virtual private cloud (VPC) networking layer.

There are three types of load balancers useful for EKS: Application Load Balancer, Network Load Balancer, and Classic Load Balancer. Each balances connections among pods based on HTTP requests, TCP sessions, or just network packets, respectively.

ELBs provide a resilient way to route inbound traffic to stateless application services across worker nodes, avoiding downtime during maintenance events. Integrating ELBs with Kubernetes Ingress rules and Service objects simplifies configuration through automation. Load balancing leverages AZs to remain online despite data center failures. EKS worker nodes should span AZs to achieve full high availability architecture patterns. For production scenarios, at least two public subnets should host load balancers to handle elastic IP failover capabilities across subnets. Similarly, worker nodes must run in private subnets with flow logs enabled for security best practices. There are three types of load balancers useful for EKS:

[Network Load Balancer](#contents.xhtml#sc3_98a)

Network Load Balancers (NLB) operate at the TCP/IP connection level for ultra-fast throughput and extremely low latency. NLB scales massively to handle spikes without degradation, which is useful for HTTP/S and TCP protocols. It integrates with static IP addresses. By operating at Layer 4, Network Load Balancers route connections based on IP protocol data maximizing performance. NLBs handle volatile traffic shifts adaptively, auto scaling capacity using exponential smoothing forecasts.

Useful for large scale HTTP services, NLBs bind to pre-allocated Elastic IP addresses providing static endpoint URLs. Compared to Application Load Balancers, NLBs drop connection context focusing exclusively on raw throughput. Microservices transmitting state in requests rather than sessions suit NLBs. Integrating NLBs with Kubernetes Services exposes TCP/UDP ports, Consul clusters, RabbitMQ streams, and SQL database replicas.

[Application Load Balancer](#contents.xhtml#sc3_99a)

Application Load Balancers (ALB) route requests to services based on HTTP headers like URIs, cookies, and host fields so different apps can be served behind a shared domain. Content aware routing happens at Layer 7. ALB can invoke lambda triggers executing custom actions during the routing process. As intelligent Layer 7 load balancers, ALBs inspect HTTP requests at the packet level to distribute traffic across registered targets.

ALBs support host or path based routing, sending requests to specific endpoints based on subdomain, URL path, or query string values. This allows a shared load balanced cluster to serve multiple applications isolated logically at the edge. ALBs integrate with identity providers, enabling authentication and access policies at the LB tier before reaching the application code. Invoking Lambda@Edge functions during request processing offloads custom preprocessing logic like verification, enrichment, or header rewrites.

[Classic Load Balancer](#contents.xhtml#sc3_100a)

Legacy Classic Load Balancers (CLBs) provide basic listen and forward load balancing without deeper packet inspection. CLBs operate on Layers 3 and 4 and handle volatile workloads not requiring advanced functionality. They offer simple round robin TCP connection distribution lacking advanced traffic steering based on HTTP attributes or session stickiness. Operating at Layers 3 and 4, CLBs forward packets based on IP protocols and port numbers.

If an application only requires simple SPI load distribution, CLBs suffice with basic routing tables and health checks. They scale massively, suiting highly volatile workloads and network patterns, unlike ALB, which throttles connection spikes. CLBs integrate with AutoScaling groups to adapt capacity targeting CPU load metrics. If an application does not mandate identity-aware authentication or full end-to-end encryption, CLBs save costs over ALBs.

All three balancer types can be integrated with EKS Services via Kubernetes Ingress rules mapped to ELB target groups. This simplifies config and draws full capabilities from AWS managed load balancing tied to worker auto scaling groups.

[Storage options](#contents.xhtml#sc2_101a)

Stateful EKS applications like databases, caches, and file sharing tools often require persistent storage. Kubernetes abstracts physical storage from the pods that utilize it via volume attachments. There are several storage options for EKS clusters, which will be discussed in this section.

[Elastic Block Store volumes](#contents.xhtml#sc3_102a)

Elastic Block Store (EBS) offers persistent block storage that can be seamlessly attached to EC2 instances. This storage solution is designed to retain its state even beyond the lifecycles of containers, making it particularly well-suited for applications with demanding I/O requirements, such as databases, analytics platforms, and other distributed applications that rely heavily on input and output operations. By providing a reliable and durable storage option, EBS ensures that data integrity is maintained, allowing for consistent and efficient performance across various workloads.

This capability makes it an essential component for applications that demand consistency and reliability in handling storage, enabling seamless and robust operations for a wide range of use cases within the Amazon Web Services (AWS) environment. EBS volumes play a crucial role in enhancing the scalability, resilience, and overall performance of EC2 instances, contributing to the flexibility and effectiveness of cloud-based computing solutions.

[Elastic File System](#contents.xhtml#sc3_103a)

Elastic File System (EFS) provides a managed Network Attached Storage solution that is accessible through mount points for EKS pods deployed across worker nodes, AZs, and VPC subnets. This scalable storage service is designed to support thousands of concurrent connections, with the added advantage of configurable throughput to meet specific performance requirements. Widely utilized by significant data applications, media processing workflows, and content management systems, EFS plays a pivotal role in facilitating seamless and efficient storage for distributed and containerized environments.

Its ability to span across multiple nodes and subnets enhances its versatility, making it a preferred choice for applications demanding high-performance storage with dynamic scalability. The managed nature of EFS simplifies storage administration, allowing users to focus on optimizing their applications rather than worrying about storage infrastructure. With its adaptability and robust features, EFS contributes significantly to the reliability and scalability of storage solutions within the EKS ecosystem.

[S3 buckets](#contents.xhtml#sc3_104a)

Amazon S3 stands out as a highly versatile and cost-effective object storage solution, offering virtually unlimited storage capacity. Kubernetes applications seamlessly integrate with S3 through the native SDK or s3fuse drive mounts, ensuring easy accessibility and compatibility. S3's strength lies in its suitability for a diverse range of use cases, excelling in handling immutable data, supporting analytics data lakes, serving as a reliable scratch space for batch workloads, facilitating log aggregation, and efficiently delivering image and video content through content delivery networks (CDNs).

The scalability and durability of S3 make it an ideal choice for applications that require extensive storage without compromising on performance. Its ability to adapt to various workloads and its compatibility with Kubernetes applications contribute to its widespread adoption across different industries. With its affordable pricing model and robust features, Amazon S3 empowers businesses to store, manage, and retrieve data seamlessly, making it a cornerstone for scalable and reliable object storage in cloud-based environments.

Storage options each serve different purposes, performance profiles, and architecture patterns. Proper storage selection ensures apps run optimally within EKS.

[EKS cluster auto scaling](#contents.xhtml#sc2_105a)

The control plane is responsible for managing the overall state of the Kubernetes cluster, handling tasks such as scheduling workloads, maintaining the desired state, and providing the API endpoint. The worker nodes, which can be either Fargate (serverless compute) or Amazon EC2 instances (customizable compute), are the compute resources that run the containerized applications, executing the application pods, exposing services, and reporting on the cluster's health.

In addition to the cluster components, EKS also provides comprehensive auto-scaling capabilities through the integration of three key features: the cluster autoscaler, the Vertical Pod Autoscaler, and the Horizontal Pod Autoscaler. These auto-scaling capabilities allow EKS clusters to dynamically adapt to changes in resource requirements, enabling efficient and cost-effective utilization of the underlying infrastructure.

By understanding the various components that make up an EKS cluster and the auto-scaling functionality provided, organizations can build highly scalable and efficient Kubernetes-based applications that can automatically adapt to changing resource requirements.

[Cluster autoscaler](#contents.xhtml#sc3_106a)

In EC2-based clusters, the cluster autoscaler (CA) serves as a crucial component, diligently monitoring the resource requests of pods within the cluster. This dynamic functionality enables the autoscaler to efficiently scale the worker node auto scaling groups, adjusting their capacity either up or down based on the observed workload requirements. By closely aligning the cluster's resources with the demands of the running pods, the cluster autoscaler optimizes resource utilization, enhancing efficiency and responsiveness.

This automated scaling process is particularly beneficial for maintaining an optimal balance between resource availability and application demands, ensuring that the cluster can seamlessly adapt to varying workloads. The integration of the cluster autoscaler within EC2 clusters contributes to their resilience and scalability, allowing organizations to efficiently manage resources and deliver consistent performance for their applications. This responsive scaling mechanism is a key element in the orchestration of EC2-based clusters, providing a dynamic and adaptive infrastructure that can effectively meet the evolving needs of diverse workloads.

[Vertical Pod Autoscaler](#contents.xhtml#sc3_107a)

The Vertical Pod Autoscaler (VPA) plays a pivotal role in optimizing resource utilization within Kubernetes clusters by autonomously adjusting both CPU and memory requests and limits for pod containers. This adjustment is dynamically performed based on real-time usage metrics obtained from the kubelet stats pipeline. By constantly analyzing live metrics, the VPA ensures that pod resource allocations align precisely with the current workload demands, effectively preventing both underutilization and overutilization of resources. 

This automated fine-tuning contributes significantly to right-sizing pods, enhancing efficiency and cost-effectiveness in resource allocation. The VPA's ability to adapt dynamically to changing workloads promotes optimal performance and responsiveness, making it a valuable tool for organizations seeking to maximize the efficiency of their containerized applications. This intelligent autoscaling capability not only streamlines resource management but also facilitates a more responsive and resilient Kubernetes environment, ensuring that resources are allocated judiciously to meet the varying demands of different workloads.

[Horizontal Pod Autoscaler](#contents.xhtml#sc3_108a)

The Horizontal Pod Autoscaler (HPA) is an essential component in Kubernetes orchestration, designed to dynamically scale the number of pod replicas deployed within a cluster. It achieves this by continuously monitoring key metrics, such as CPU utilization, and triggering scaling actions when predefined thresholds are exceeded. When the observed metrics indicate that the CPU utilization has surpassed the configured thresholds, the HPA efficiently replicates pods to accommodate the increased demand. This automated scaling mechanism ensures that the cluster adapts in real-time to the evolving resource needs of the applications it hosts.

By replicating pods based on observed metrics, the HPA enhances the responsiveness and scalability of Kubernetes deployments, allowing organizations to efficiently handle varying workloads without manual intervention. The HPA's ability to dynamically adjust the number of replicas contributes to optimal resource utilization, preventing both under-provisioning and over-provisioning of resources. Overall, the Horizontal Pod Autoscaler is a valuable tool for maintaining performance and stability in Kubernetes environments by ensuring that the number of pod replicas aligns closely with the demands of the hosted applications. Auto scaling capabilities help EKS clusters size correctly as apps grow and shrink, eliminating overprovision.

[Security best practices](#contents.xhtml#sc2_109a)

Amazon EKS provides a robust set of security features and capabilities to ensure the protection of Kubernetes deployments within the AWS ecosystem. Firstly, the VPC networking configuration plays a crucial role, allowing administrators to define granular network policies, leverage private subnets, and utilize VPC endpoints to control the flow of traffic and maintain a secure communication infrastructure. This strategic use of VPC components enhances the overall security posture by limiting direct internet access and optimizing data transfer within the AWS backbone.

Additionally, EKS leverages the power of IAM and Kubernetes Role-Based Access Control (RBAC) to govern and manage access within the cluster. By aligning IAM roles with RBAC, administrators can implement the principle of least privilege, granting users and workloads only the necessary permissions to fulfill their responsibilities. This granular approach to permissions management reduces the risk associated with unnecessary access rights and privileges, further strengthening the security of the Kubernetes environment. EKS also offers pod security policies, which allow administrators to define criteria for pod configurations, ensuring that only approved and secure pods are allowed to launch. Furthermore, the implementation of comprehensive TLS encryption across all components, along with the robust auditing capabilities provided by the Kubernetes API auditor and CloudWatch Logs, contribute to a resilient and protected Kubernetes infrastructure.

[VPC network policies](#contents.xhtml#sc3_110a)

Deploying EKS clusters within an Amazon VPC grants users the flexibility to define networking rules. Through the strategic use of subnets, Network ACLs, security groups, and route tables, administrators can precisely control the flow of traffic within the cluster. The implementation of private subnets ensures the removal of direct internet access, enhancing the security posture of the EKS environment. Additionally, the utilization of VPC endpoints plays a crucial role in channeling traffic within the AWS backbone for specific services like S3 and DynamoDB, optimizing data transfer, and maintaining a secure communication infrastructure within the Amazon cloud environment.

[IAM roles and policies](#contents.xhtml#sc3_111a)

Adhering to the principle of least privilege is imperative when assigning permissions to EKS administrators, human users, and workloads. This security principle ensures that access is granted at the minimal level necessary for individuals and processes to fulfill their roles effectively. Identity and Access Management (IAM) roles intricately tied to Kubernetes Role-Based Access Control (RBAC) play a pivotal role in governing and managing access within EKS clusters. By aligning IAM roles with RBAC, administrators can finely control and restrict capabilities, allowing users and workloads to execute only the actions essential to their specific responsibilities. This granular approach to permissions enhances overall security by mitigating the risk associated with unnecessary access rights and privileges within the Kubernetes environment.

[Pod security policies](#contents.xhtml#sc3_112a)

EKS pod security policies play a crucial role in specifying the criteria that pods must meet before launching, taking into account attributes such as user ID, approved namespaces, container registries, volume types, and network accessibility. By defining these conditions, the security policies enforce stringent controls to ensure that pods adhere to secure configurations. This proactive approach contributes significantly to maintaining a robust security posture within the EKS environment, mitigating potential vulnerabilities. The ability to tailor security policies based on various attributes allows administrators to implement a fine-grained security model, addressing specific requirements and minimizing risks associated with insecure pod configurations. Overall, EKS pod security policies enhance the security landscape of Kubernetes deployments by providing a customizable framework for enforcing and maintaining secure pod behaviors. Pod security policies in EKS offer administrators the flexibility to create customized security policies tailored to their environment, addressing specific requirements and minimizing risks.

[Transport layer security](#contents.xhtml#sc3_113a)

Facilitating robust security practices, it is essential to enable TLS encryption across all components in a Kubernetes environment, encompassing the control plane, etcd data stores, worker node kubelets, and containerized applications. This comprehensive encryption ensures a secure communication channel, safeguarding sensitive data and interactions within the cluster. Cert manager, a pivotal component in this security framework, efficiently manages the lifecycle of TLS certificates, automating tasks related to their issuance, renewal, and revocation. By leveraging cert-manager for TLS certificate handling, administrators can streamline the implementation of strong encryption practices, contributing to a resilient and protected Kubernetes infrastructure.

[Audit logging](#contents.xhtml#sc3_114a)

The Kubernetes API auditor module plays a crucial role in enhancing security by logging all API requests, responses, and associated resources to CloudWatch Logs for comprehensive monitoring. This meticulous logging process creates an immutable trail of access and changes within the Kubernetes environment, providing a transparent and traceable record. By utilizing CloudWatch Logs, administrators gain valuable insights into the Kubernetes API activities, enabling prompt detection and response to any unauthorized or suspicious actions. This robust auditing mechanism contributes to the overall security posture of the Kubernetes cluster by ensuring visibility and accountability for API interactions.

[EKS cluster upgrades and maintenance](#contents.xhtml#sc2_115a)

EKS control plane upgrades happen automatically, keeping Kubernetes patched, stable, and up to date. For worker nodes:

*   Managed node groups: Managed node groups streamline the process of coordinating version upgrades within AWS, providing a simplified and efficient approach. The AWS site discontinuation handler, a key feature, ensures a seamless transition during node termination by gracefully draining nodes before the actual termination occurs. This thoughtful approach prevents abrupt capacity drops, thereby avoiding downtime and maintaining the availability of resources. The combination of managed node groups and the discontinuation handler contributes to a smooth and uninterrupted upgrade experience, enhancing the overall operational reliability of AWS environments.
*   Self-managed nodes: In scenarios involving user-managed EC2 instances, the upgrade planning process includes cordoning worker nodes to halt the scheduling of pods. Subsequently, a phased approach is adopted, wherein old instances are gracefully drained and deleted in small batches, concurrently replaced with new nodes running the target AMI and Kubernetes versions. This strategic upgrade methodology ensures a smooth transition with minimal disruption. Furthermore, Route 53 health checks play a crucial role, allowing load balancers to seamlessly shift traffic and maintain continuous application availability throughout the upgrade process.

[Integrations with AWS services](#contents.xhtml#sc2_116a)

The CloudWatch container insights feature allows for the efficient management of cluster metrics, application logs, and pod logs, providing a centralized platform for monitoring and analyzing the performance and behavior of the Kubernetes environment, with the ability to set up alarms to proactively address any potential issues. Further, the integration of AWS CodeCommit, CodeBuild, and CodeDeploy empowers teams to oversee CI/CD pipelines and streamline the application deployment process, leveraging blue/green deployment methods to enhance reliability and minimize downtime, while the Secrets Manager service securely stores and injects credentials, API keys, and other sensitive information into pods as environmental variables, safeguarding confidential data and facilitating easy management and rotation of credentials.

Additionally, AWS Config and Control Tower enable a centralized approach to enforcing security, compliance, and operational best practices across the EKS clusters and associated workloads, ensuring adherence to established standards and mitigating risks, providing a unified framework for robust management and oversight of the Kubernetes environment. By leveraging these AWS service integrations, organizations can enhance the security, monitoring, and deployment capabilities of their EKS clusters, ensuring a robust, secure, and well-governed Kubernetes infrastructure.

[CloudWatch container insights](#contents.xhtml#sc3_117a)

Efficiently manage cluster metrics, application logs, and pod logs by storing, monitoring, analyzing, and querying them within CloudWatch. This centralized platform facilitates a comprehensive overview of the cluster's performance and application behavior. To proactively address issues, set up alarms in CloudWatch that promptly notify stakeholders of any potential issues, allowing for timely intervention and ensuring the continuous health and functionality of the Kubernetes environment.

[CodeDeploy and CodePipeline](#contents.xhtml#sc3_118a)

Effectively oversee CI/CD pipelines by utilizing AWS CodeCommit, CodeBuild, and CodeDeploy to streamline the application deployment process. These integrated services provide a seamless end-to-end solution for managing code repositories, building artifacts, and orchestrating deployments. Additionally, leverage blue/green deployment methods to enhance deployment reliability and minimize downtime, ensuring a smooth transition for applications in production environments. The combination of CodeCommit, CodeBuild, and CodeDeploy empowers teams to achieve efficient and controlled continuous delivery. AWS CodeCommit manages source code, CodeBuild builds artifacts, and CodeDeploy orchestrates deployments, collectively automating the CI/CD pipeline for efficient software delivery.

[Secrets manager](#contents.xhtml#sc3_119a)

Enhance security practices by securely referencing credentials, API keys, and other sensitive information within Kubernetes environments. Adopt a secure approach by injecting these credentials into pods as environmental variables, avoiding the pitfalls of hard-coding confidential data directly into the application code. This methodology not only safeguards sensitive information but also facilitates easier management and rotation of credentials without necessitating changes to the application codebase. By employing environmental variables, teams can maintain a robust security posture while ensuring the flexibility to manage and update sensitive data seamlessly.

[AWS config and control tower](#contents.xhtml#sc3_120a)

Implement a centralized approach to enforce security, compliance, and operational best practices for EKS clusters and associated workloads through the use of native AWS governance tools. By leveraging these tools, administrators gain the capability to set and enforce policies consistently across the entire Kubernetes environment, ensuring adherence to established standards. This centralized governance model enhances visibility and control, allowing organizations to mitigate risks, maintain compliance, and uphold operational excellence seamlessly within their EKS clusters. The integration of native AWS governance tools provides a unified framework for robust management and oversight of EKS environments.

[Use case examples](#contents.xhtml#sc2_121a)

EKS provides a flexible foundation that enables organizations to run a variety of cloud-native applications following established best practices for productivity and scale, including optimizing costs for environments with intermittent traffic by incorporating cost-effective EC2 spot instances and leveraging the flexibility of cluster and horizontal pod autoscalers to dynamically adjust resources in response to demand fluctuations, enhancing the resilience and fault tolerance of production infrastructure by leveraging multi-AZ worker auto scaling groups, scalable EFS storage, advanced load balancing with NLB and ALB, tightly controlled IAM access, and DevSecOps practices to embed security throughout the deployment lifecycle, and enabling data scientists to optimize model deployment by packaging models in containers hosted on GPU-powered nodes, efficiently storing model artifacts in S3, and auto-scaling inferencing capacity dynamically in response to streaming data sources to ensure efficient and responsive real-time predictions, all of which empower organizations to reliably deploy Kubernetes at scale on AWS, reducing management burdens while delivering highly available infrastructure to support their most demanding cloud-native applications. Below are three common EKS deployment patterns:

[Burstable development cluster](#contents.xhtml#sc3_122a)

Optimize costs in environments with intermittent traffic by incorporating EC2 spot instances, leveraging the flexibility offered by both cluster and horizontal pod autoscalers. This strategic combination ensures efficient scaling based on demand, allowing organizations to pay for compute capacity only when needed. EC2 spot instances, known for their cost-effectiveness, provide an economical solution for workloads with variable resource requirements, further enhancing the overall efficiency of the Kubernetes environment. By dynamically adjusting resources through autoscalers and integrating spot instances, organizations achieve a balance between performance and cost savings in response to fluctuating demand.

[Highly available production cluster](#contents.xhtml#sc3_123a)

Enhance the resilience of your infrastructure by leveraging multi-AZ worker auto scaling groups, which distribute resources across different zones for increased fault tolerance. Utilize EFS storage to provide scalable and durable file storage across your applications. Enhance load balancing capabilities with NLB and ALB to ensure optimal distribution of traffic. Secure the environment by restricting administrative access through tightly controlled IAM roles, enforcing a least privilege principle. Embrace a DevSecOps approach by integrating AWS CodeSuite tools into your workflows, ensuring security practices are embedded throughout the development and deployment lifecycle.

[Machine learning serving](#contents.xhtml#sc3_124a)

Data scientists optimize model deployment by packaging models in containers hosted on GPU-powered nodes. Model artifacts are efficiently stored in S3, streamlining access and management. Leveraging batch transform output in conjunction with S3 facilitates seamless processing and storage of results. The system's inferencing capacity auto-scales dynamically, responding to SageMaker and Lambda triggers triggered by streaming data sources, ensuring efficient and responsive real-time predictions.

These represent just some of the pattern options: EKS provides the flexible foundation to run cloud-native apps following established best practices for productivity and scale. In summary, Amazon EKS makes it easy to reliably deploy Kubernetes at scale on AWS, reducing management burdens while providing highly available infrastructure for your most demanding applications. EKS supports model versioning, enabling data scientists to manage and deploy multiple versions of their models concurrently, ensuring flexibility and scalability in machine learning deployments.

[Conclusion](#contents.xhtml#sc2_125a)

EKS delivers a fully managed Kubernetes control plane, simplifying lifecycle maintenance for containerized applications. Tight integrations across complementary AWS services enable high scale, maximum resilience, easier security controls, cost efficient infrastructure sizing, and comprehensive visibility into cluster health and logs.

Common use cases outlining development, production, and ML workloads demonstrate the versatility and capabilities of EKS in action. With this architectural overview, readers should feel equipped to plan and operate EKS to unlock its full potential based on application needs.

In the next chapter, we will look at the prerequisites for setting up an EKS cluster.

[Questions](#contents.xhtml#sc2_126a)

1.  What two main components make up an EKS cluster?
    
2.  How does Fargate differ from EC2 worker node infrastructure?
    
3.  What load balancer type operates at Layer 7 vs Layer 4?
    
4.  When might you select Amazon EFS over EBS volumes?
    
5.  What auto scaling capabilities optimize resource usage?
    

[Exercises](#contents.xhtml#sc2_127a)

1.  Build an EKS cluster with IAM integrations.
    
2.  Configure pod security policies to enforce namespace restrictions.
    
3.  Launch sample apps showcasing blue/green deployments with CodeSuite.
    

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 6Setting up Elastic Kubernetes Service Prerequisites](#contents.xhtml#ch06a)

[Introduction](#contents.xhtml#sc2_128a)

Amazon Elastic Kubernetes Service (EKS) simplifies deploying and managing containerized applications using Kubernetes on AWS. However, effectively operating EKS relies on configuring various permissions, network constructs, and integrations in advance.

This chapter outlines the steps and best practices to prepare essential infrastructure, policies, roles, VPCs, and supporting services to then enable a smooth EKS cluster creation process. Defining prerequisites streamlines control plane and node provisioning while also hardening security, compliance, and observability early on.

[Structure](#contents.xhtml#sc2_129a)

In this chapter, we will cover the following topics:

*   Operating system requirements
*   IAM user, group, role creation
*   VPC networking and subnet layout
*   Route table and internet gateway setup
*   IAM policy and CNI plugin access
*   Node security group rules
*   Ops tool and billing integration

[Objectives](#contents.xhtml#sc2_130a)

This chapter covers the necessary areas to establish key Amazon EKS prerequisites. These include the operating system requirements, creating an IAM user, group, and role, setting up VPC networking and subnet layout, configuring the route table and internet gateway, ensuring IAM policy and Container Network Interface (CNI) plugin access, defining node security group rules, and integrating operations tools and billing.

By the end of this process, you will have built a solid foundation to tackle the EKS cluster installation, confident that the right access controls, network topology, and supporting capabilities are already in place. Specifically, you will have ensured that your operating system meets the requirements for running EKS, created the necessary IAM user, group, and role to manage your EKS cluster, established a VPC networking and subnet layout that aligns with EKS best practices, configured the route table and internet gateway to enable connectivity to your EKS cluster, granted the appropriate IAM policy and CNI plugin access to your EKS resources, defined the necessary node security group rules to secure your EKS cluster, and integrated your operations tools and billing systems to monitor and manage your EKS deployment effectively.

[Operating system requirements](#contents.xhtml#sc2_131a)

You can interact with EKS clusters from any modern computer or laptop where you have access to install the required command line tools, regardless of whether you are using Windows, macOS, or Linux distributions. Specifically, interacting with EKS clusters requires:

*   AWS CLI: Command line utility for AWS services
*   Kubectl: Kubernetes CLI to manage cluster resources
*   eksctl: EKS cluster manager CLI (alternative to AWS console)

These tools run on the most common operating systems that technical users rely on day to day. Let us discuss how this can be approached with various Operating systems. The Reference section below has the links to discuss the installation steps.

[Windows](#contents.xhtml#sc3_132a)

The AWS CLI MSI installer is compatible with Windows 7, 8, and 10+. Kubectl is distributed as an MSI package, while eksctl provides a standalone binary. Users can install these tools either through the package manager Chocolatey or by direct installation methods. This flexibility allows seamless integration into various Windows environments, catering to different preferences and system requirements.

[macOS](#contents.xhtml#sc3_133a)

For Mac users, installing the AWS CLI is convenient through native options such as Homebrew or by downloading the PKG file. Similarly, kubectl is available as a Homebrew formula, simplifying the installation process. Eksctl further enhances convenience by providing Darwin AMIs.

Since macOS is commonly used by developers, these installation methods cater to the preferences of users accessing Mac laptops running the macOS operating system, ensuring a seamless experience for AWS tooling.

[Linux](#contents.xhtml#sc3_134a)

Linux administrators, regardless of their distribution choice—be it Debian, Ubuntu, RHEL, or CentOS—can easily obtain the AWS CLI, kubectl, and eksctl from standard repositories using familiar package management tools like yum or apt.

Additionally, users can install these tools through alternative packaging systems such as snap and flatpak packages, providing diverse options for customization and ease of integration into various Linux environments. This ensures a streamlined process for administrators, allowing them to leverage the package management channels they are most accustomed to for efficient installation and management of AWS tools.

So, all major desktop operating systems interoperate smoothly with Amazon EKS, requiring only a modern OS able to install the latest CLI toolchain. Most access happens through bash terminals as kubectl and eksctl issue commands to deploy manifests and operate resources. With the core CLIs established, any common laptop or workstation provides a suitable control point for Amazon EKS management duties, giving admins the flexibility to use their preferred machine OS.

[IAM user, group, role creation](#contents.xhtml#sc2_135a)

The initial phase involves setting up IAM structures to manage identity, permissions, and access controls effectively. It is crucial to create distinct users for administrators and developers, ensuring a clear segregation of roles and responsibilities.

Additionally, implementing groups and roles further refines the access management framework, allowing for fine-grained control over AWS resources. This organized IAM setup lays the foundation for a secure and well-structured environment, aligning with best practices in identity and access management on the AWS platform.

[VPC networking and subnet layout](#contents.xhtml#sc2_136a)

For optimal performance and high resiliency in production environments, setting up an Amazon EKS necessitates the creation of a virtual private cloud (VPC). This VPC should be configured with both public and private subnets strategically distributed across multiple availability zones.

By employing this architecture, EKS ensures redundancy and fault tolerance, mitigating the impact of failures in a single availability zone. The use of public subnets allows for external communication, while private subnets enhance security by restricting direct access. This well-structured VPC aligns with best practices, providing a robust foundation for deploying and managing Kubernetes clusters with Amazon EKS.

[Route table and internet gateway setup](#contents.xhtml#sc2_137a)

After defining VPC resources, the next crucial step involves configuring route tables and internet gateways. This configuration facilitates the connection of private subnets to the internet through network address translation (NAT).

By establishing this link, resources within private subnets gain controlled access to external networks while maintaining an additional layer of security. Properly configured route tables and internet gateways ensure a seamless flow of traffic between private subnets and the internet, enhancing the functionality and connectivity of the overall Amazon VPC infrastructure.

[IAM policy and CNI plugin access](#contents.xhtml#sc2_138a)

Kubernetes relies on CloudFormation templates, which require specific IAM permissions for seamless operation. These permissions become vital during the initiation of cluster creation calls, particularly in creating worker node stacks. Users play a pivotal role in ensuring a smooth and secure deployment process by granting the necessary IAM permissions.

This integration of IAM permissions with CloudFormation templates is essential for Kubernetes to effectively orchestrate the deployment of worker nodes, streamlining the overall setup and management of clusters on the AWS platform. The careful alignment of IAM permissions and CloudFormation templates enhances the security and efficiency of Kubernetes clusters, establishing a robust foundation for containerized applications in the AWS environment.

[Node security group rules](#contents.xhtml#sc2_139a)

In the context of Amazon EKS, security groups function as virtual firewalls, playing an important role in managing inbound and outbound traffic for both EKS node groups and pods. These security groups enforce fine-grained control by specifying protocols, ports, and source/destination IP addresses, ensuring a secure networking environment.

By regulating communication at this level, administrators can implement necessary access restrictions, enhancing the overall security posture of EKS clusters. This robust control mechanism adds an additional layer of protection, contributing to the safeguarding of resources within the Kubernetes clusters on AWS.

[Ops tool and billing integration](#contents.xhtml#sc2_140a)

For comprehensive monitoring of Amazon EKS, administrators can integrate AWS Cost Explorer with budget alerts, CloudWatch container insights, and SNS topics. This multi-faceted approach allows for real-time tracking of EKS spending, enabling better financial management.

CloudWatch container insights provide valuable health metrics, offering insights into the performance of EKS clusters. By coupling these metrics with SNS topics, administrators can set up customized notifications to proactively respond to any anomalies or critical events, ensuring the continuous health and optimal cost management of their EKS infrastructure on AWS. This integrated monitoring solution enhances visibility and responsiveness for maintaining a robust and cost-effective EKS environment.

[Conclusion](#contents.xhtml#sc2_141a)

Establishing the foundational prerequisites for Amazon EKS streamlines the deployment process, minimizing launch friction and allowing users to concentrate on application development rather than dealing with ancillary infrastructure. Robust access controls and well-defined network topologies contribute to a strong security posture, safeguarding EKS environments from potential threats.

The integration of management tools lays the groundwork for optimization, enabling administrators to fine-tune performance and resource utilization. With these essential components in place, users are well-prepared to effortlessly spin up their Amazon EKS cluster, leveraging a well-architected and secure foundation for the deployment and management of Kubernetes workloads on AWS. This approach not only enhances operational efficiency but also ensures a resilient and scalable environment for running containerized applications.

In the next chapter, we will learn about setting up an EKS cluster and start deploying applications.

[Review questions](#contents.xhtml#sc2_142a)

1.  Why separate VPC public and private subnets for control plane vs. workers?
    
2.  How do route tables connect private subnets to the Internet?
    
3.  What IAM capability allows cross-account EKS access?
    
4.  Why do we create individual IAM users over just using the root credentials?
    
5.  What tools can be used to monitor EKS spend and performance?
    

[Exercises](#contents.xhtml#sc2_143a)

1.  Configure an EKS admin IAM policy granting full access.
    
2.  Launch a multi-AZ production VPC with proper subnets.
    

[Reference](#contents.xhtml#sc2_144a)

Use the following links to get started on the installation of these tools:

*   AWS CLI: Command line utility for AWS services [https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) 
*   Kubectl: Kubernetes CLI to manage cluster resources [https://kubernetes.io/docs/tasks/tools/](https://kubernetes.io/docs/tasks/tools/) 
*   eksctl: EKS cluster manager CLI (alternative to AWS console) [https://eksctl.io/installation/](https://eksctl.io/installation/) 

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 7Creating Elastic Kubernetes Service Clusters](#contents.xhtml#ch07a)

[Introduction](#contents.xhtml#sc2_145a)

Amazon Elastic Kubernetes Service (EKS) is a managed Kubernetes service provided by AWS that makes it easy to deploy, manage, and scale containerized applications using Kubernetes. EKS removes the burden of administering complex Kubernetes control plane configurations by provisioning, upgrading, and securing the control plane for users.

In this section, we will cover different options and methods for creating EKS clusters on AWS. We will start with using the AWS Management Console, then look at infrastructure as code (IaC) options like Terraform and CDK for TypeScript. We will also cover a Kubernetes native tool called Plum that simplifies EKS cluster creation and configuration.

[Structure](#contents.xhtml#sc2_146a)

This chapter contains the following topics:

*   Understanding EKS cluster
*   Creating an EKS cluster via the AWS Console
*   Creating an EKS cluster using eksctl
*   Creating an EKS cluster using AWS CDK
*   Creating an EKS cluster using Terraform
*   Creating an EKS cluster using Pulumi

[Objectives](#contents.xhtml#sc2_147a)

By the end of this section, you should: understand the different options for creating EKS clusters, including using the AWS Console, provisioning IaC with Terraform and CDK, and simplifying cluster management with Kubernetes-native tools like Plum; be able to create an EKS cluster via the AWS Console through its graphical user interface for getting started quickly; be familiar with IaC tools like Terraform and CDK for cluster creation which allow automating provisioning of clusters and related resources; know how to use Plum to simplify cluster creation and configuration as it handles much of the complexity behind configuring Kubernetes; and finally have hands-on experience creating clusters through different methods ranging from manual click-through UIs to fully automated cluster deployment options.

[Understanding EKS cluster](#contents.xhtml#sc2_148a)

An Elastic Kubernetes Service (EKS) cluster is a managed Kubernetes service provided by Amazon Web Services (AWS). It allows users to run and orchestrate containerized applications using Kubernetes without managing the underlying infrastructure. EKS automates the deployment, scaling, and management of Kubernetes control plane components, such as the API server and etcd database, while providing high availability and security features. Users can easily integrate EKS clusters with other AWS services and tools, making it a popular choice for organizations looking to deploy and manage containerized workloads in the cloud. Refer to the following figure:

![](images/Figure_7.1.png)

Figure 7.1: EKS cluster architecture

Amazon EKS offers several key benefits for containerized application deployment and management. It provides a fully managed Kubernetes control plane, eliminating the need to install and maintain your own Kubernetes management infrastructure. EKS integrates seamlessly with other AWS services, enabling easy scaling, load balancing, and security features. It ensures high availability by running across multiple availability zones and automatically detects and replaces unhealthy control plane instances. EKS also simplifies cluster upgrades and patches, reducing operational overhead. With its native support for AWS identity and access management (IAM), it offers fine-grained access control. Additionally, EKS is a certified Kubernetes conformant, ensuring compatibility with existing Kubernetes applications and tools.

[Creating an EKS cluster via the AWS Console](#contents.xhtml#sc2_149a)

The AWS Console provides a user interface to guide you through the steps of creating an EKS cluster. When you log into your AWS Console and get into Amazon EKS console, you will be welcomed with a page like the following figure. Click on Add Cluster and Create.

![](images/Figure_7.2.png)

Figure 7.2: Amazon EKS Welcome page

This will start the wizard to create the cluster with a series of steps. You can start configuring your cluster by providing a name, Kubernetes version (1.28 is the latest version at the time of writing this), cluster role, etc. In EKS, a cluster service role plays a crucial role in managing the interaction between the EKS control plane and the resources within the cluster. This role is responsible for granting necessary permissions to EKS to perform tasks such as creating and managing worker nodes, networking, and load balancing. It ensures secure communication and coordination between different components of the EKS cluster. Then you should be able to choose the cluster access being administrator access and without that. You should also be able to select the encryption as well. The following figure shows the cluster configuration page with varying options for the user to choose from:

![](images/Figure_7.3.png)

Figure 7.3: Cluster configuration page

After this step, you can configure your networking for the cluster. Here, you should be able to select your VPC, Subnets both public and/or private, security group settings as below. After this you could select the IP address family either as IPV4 or IPV6. Amazon EKS supports both IPv4 and IPv6 addressing. While IPv4 is the traditional and widely used protocol, IPv6 offers a larger address space, promoting scalability and accommodating the growing number of connected devices in EKS clusters. EKS users can leverage IPv6 to future-proof their infrastructure and address the limitations of IPv4 address exhaustion. In Amazon EKS, cluster endpoint access is essential for communication between the Kubernetes control plane and worker nodes within the cluster. This endpoint allows secure interactions for tasks such as deploying and managing applications. Users can configure and manage the cluster endpoint access to ensure proper connectivity and security within their EKS environment. The following figure shows the networking options the user can choose from:

![](images/Figure_7.4.png)

Figure 7.4: Networking configurations page

The next section covers the observability. Here, you could choose to send your metrics to Amazon Managed Service for Prometheus. Also, you could enable control plane logging to choose the various components as shown:

![](images/Figure_7.5.png)

Figure 7.5: Observability configuration page

The next step talks about EKS add-ons. Amazon EKS add-ons are pre-configured extensions that simplify the deployment and management of essential Kubernetes components on an EKS cluster. These add-ons cover functionalities such as monitoring, networking, and security, providing a streamlined approach to enhance the cluster's capabilities. Examples of add-ons include the AWS Load Balancer Controller for automating load balancing, Amazon VPC CNI for efficient networking, and Cluster AutoScaler for dynamic node scaling based on resource demands. EKS add-ons enable users to easily integrate and leverage AWS services to optimize their Kubernetes workloads. The following figure shows the various add-on options available when you configure your cluster:

![](images/Figure_7.6.png)

Figure 7.6: EKS add-on options page

After selecting the various add-on options, you should be able to configure the selected add-on settings, as shown in [Figure 7.7](#ch07.xhtml#fig7-7). You should be able to choose the various versions that you want to use. Additionally, if you do not want to use any of the add-ons, there is an option to remove the add-ons as well.

![](images/Figure_7.7.png)

Figure 7.7: Configuring selected add-ons

The last step offers to review your configuration and create the cluster, as shown in the following figure:

![](images/Figure_7.8.png)

Figure 7.8: Review page before cluster creation

[Creating an EKS cluster using eksctl](#contents.xhtml#sc2_150a)

eksctl by Weaveworks provides a convenient way of declaring and provisioning EKS clusters and their associated Kubernetes worker nodes. To get started, we first ensure eksctl is installed on our local machine. We can install on Linux/macOS by running:

\`\`\`

curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl\_$(uname -s)\_amd64.tar.gz" | tar xz -C /tmp

sudo mv /tmp/eksctl /usr/local/bin

sudo chmod +x /usr/local/bin/eksctl

\`\`\`

This will grab the latest release, extract it, and move the binary to our path. On Windows we can use Chocolatey to simplify the installation via \`choco install eksctl\`.

With eksctl installed, we create a configuration file to define our desired EKS cluster details. This includes specifications like Kubernetes version, instance type and sizes for node groups, VPC networking changes, IAM permissions to be configured, availability zones, and more.

An example config file is shown below, which sets up two node groups, three availability zones, and custom IAM policies:

\`\`\`yaml

apiVersion: eksctl.io/v1alpha5

kind: ClusterConfig

metadata:

name: cluster-demo

region: us-east-1

AvailabilityZones: \["us-east-1a", "us-east-1b", "us-east-1c"\]

managedNodeGroups:

\- name: nodegroup1

desiredCapacity: 4

instanceType: m5.large

volumeSize: 80

volumeType: gp3

iam:

withAddonPolicies:

imageBuilder: true

autoScaler: true

\- name: nodegroup2

desiredCapacity: 2

instanceType: c5.large

privateNetworking: true

iam:

withAddonPolicies:

externalDNS: true

\`\`\`

This config just shows a subset of the options available. We can customize VPCs, subnet CIDRs, endpoint access, secrets encryption, Kubernetes version, labels, taints, and far more in this file. With our config defined as cluster.yaml, we pass this file to eksctl via the create command:

\`\`\`

eksctl create cluster -f cluster.yaml

\`\`\`

Eksctl will now read all parameters and settings from cluster.yaml and handle provisioning the management plane, worker node groups and instances, networking rules and routes, IAM policies, and any other declared configuration.

We can watch as eksctl outputs logs for each step, from validating parameters to creating CloudFormation stacks for various cluster components:

\`\`\`

\[![](images/eq-1.jpg)\] eksctl version 0.118.0

\[i\] using region us-east-1

\[i\] setting availability zones to \[us-east-1a us-east-1b us-east-1c\]

...

\[![](images/eq-1.jpg)\] EKS cluster "cluster-demo" in "us-east-1" region is ready

\`\`\`

Once all steps are complete, our EKS cluster will be fully provisioned and configured based on cluster.yaml. We can verify access and check the status of our connected worker nodes by running kubectl commands:

\`\`\`

kubectl get nodes # view worker nodes

\`\`\`

Just like that, eksctl has automated the entire EKS bootstrapping process, including setting up networking, permissions, node groups, and Kubernetes installation. We can now start deploying applications using this managed Kubernetes environment with the assurance that EKS will handle ongoing control plane maintenance and management behind the scenes.

[Creating an EKS cluster using AWS CDK](#contents.xhtml#sc2_151a)

The AWS Cloud Development Kit (CDK) provides a way to model infrastructure through code using familiar languages. To leverage CDK for provisioning our solutions, we first ensure the core runtimes are set up. We will install Node.js and npm, which powers the CDK toolkit:

\`\`\`

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash

. ~/.nvm/nvm.sh

nvm install --lts

node -v

npm -v

\`\`\`

This grabs the latest Node LTS release. We then install the CDK toolkit globally:

\`\`\`

npm install -g aws-cdk

cdk --version

\`\`\`

The AWS CDK cli allows deploying our infrastructure stacks. Next, we bootstrap a CDK environment in AWS for housing deployed assets:

\`\`\`

cdk bootstrap \\

\-c cloudformationExecutionPolicies=arn:aws:iam::aws:policy/AdministratorAccess

\`\`\`

This sets up the CDK toolkit stack. Now, we can create a new CDK project:

\`\`\`

mkdir cdk-eks-demo

cd cdk-eks-demo

npm init -y

npm install aws-cdk aws-eks

\`\`\`

We initialize a Node.js project and install the AWS CDK and EKS modules from NPM. Within this project, we can create our stack:

\`\`\`

touch cdk-eks-stack.ts

\`\`\`

We define our EKS resources like VPC, clusters, nodegroups:

\`\`\`typescript

import { Cluster, KubernetesVersion } from "aws-eks";

import { Construct } from "constructs";

export class CdkEksStack extends Stack {

constructor(scope: Construct, id: string) {

super(scope, id);

 new Cluster(this, "EksCluster", {

version: KubernetesVersion.V1\_21

});

}

}

\`\`\`

We wire up the stack in index.ts:

\`\`\`typescript

import { App } from "aws-cdk-lib";

import { CdkEksStack } from "./cdk-eks-stack";

const app \= new App();

new CdkEksStack(app, "eks-stack");

app.synth();

\`\`\`

We could configure advanced networking, access policies, and node configurations here. Finally, we can deploy through the CDK CLI:

\`\`\`

cdk deploy

\`\`\`

This will compile and deploy our TypeScript declaration of EKS infrastructure to an AWS environment. The full lifecycle is facilitated from installing CDK to modeling stacks in code to bootstrapping and deploying them.

[Creating an EKS cluster using Terraform](#contents.xhtml#sc2_152a)

Terraform is an IaC tool that allows us to define, provision, and manage infrastructure in a declarative fashion using code. This differs from the traditional approach of manually configuring resources in the AWS Console.

With Terraform, we write configuration files using HashiCorp Configuration Language (HCL) that describe the infrastructure we want to build. Terraform supports provisioning infrastructure across public clouds like AWS, Azure, GCP, and on-prem solutions. To install Terraform, we visit the downloads page at [https://www.terraform.io/downloads.html](https://www.terraform.io/downloads.html) and grab the appropriate package for our operating system. We can also install via package managers like apt, yum or homebrew. The other option is to install Terraform on our local machine, which we will execute commands from:

\`\`\`

curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -

sudo apt-add-repository "deb \[arch=amd64\] https://apt.releases.hashicorp.com $(lsb\_release -cs) main"

sudo apt-get update

sudo apt install terraform

terraform -v

\`\`\`\`

This gets Terraform in our path for executing commands. Next, we set up AWS access credentials so Terraform can interface with AWS APIs on our behalf:

\`\`\`

aws configure

\# Enter access key, secret, region, output format

\`\`\`

After installing, we validate it is in our path by running:

\`\`\`

terraform -v

\`\`\`

With Terraform set up, we begin authoring IaC configurations to model our desired EKS cluster. Terraform uses .tf files for declaring resources. First, we configure the AWS provider, which handles authentication under the hood and exposes resources to provision:

\`\`\`

\# eks-cluster.tf

provider "aws" {

 region = "us-east-1"

}

\`\`\`

Next, we describe the EKS cluster. Terraform has AWS resources available as plugins, including managed Kubernetes offerings like EKS:

\`\`\`

eks-cluster.tf

\# EKS cluster

resource "aws\_eks\_cluster" "my-eks" {

 name = "my-cluster" 

role\_arn = aws\_iam\_role.eks-cluster.arn

 vpc\_config {

 subnet\_ids = \[

aws\_subnet.private-a.id,

aws\_subnet.private-b.id

\]

}

}

\# Permissions

resource "aws\_iam\_role" "eks-cluster" {

 \# role policy for EKS service access

}

resource "aws\_vpc" "eks-vpc" {

 \# networking config

}

resource "aws\_subnet" "private-a" {

 \# private subnet A

}

resource "aws\_subnet" "private-b" { 

 \# private subnet B

}

node-group.tf

\# MANAGED NODE GROUP

resource "aws\_eks\_node\_group" "demo-ng" { 

cluster\_name = aws\_eks\_cluster.my-eks.name

 node\_group\_name = "managed-ondemand"

 instance\_types = \["t3.medium"\]

 subnet\_ids = \[

aws\_subnet.private-a.id

\]

 \# launch template configs

 \# update policy etc

}

\`\`\`

This declares an EKS cluster resource. We reference networking components and IAM roles that grant the cluster access to AWS APIs. With our cluster spec authored, we initialize Terraform, which downloads providers:

\`\`\`

terraform init

\`\`\`

We execute a plan to preview changes before applying:

\`\`\`

terraform plan

\`\`\`

If the plan looks good with our EKS resource being added, we apply to provision real infrastructure:

\`\`\`

terraform apply

\`\`\`

Terraform will call AWS APIs to create networking components, IAM roles and policies, and activate the managed control plane. Soon, we have a running EKS cluster. We could enhance this example to add managed node groups, customize VPN access, integrate other AWS services, leverage Kubernetes providers and more.

An advantage of Terraform is the ability to adjust and recalculate changes. If we update eks-cluster.tf with additional node groups:

\`\`\`

resource "aws\_eks\_node\_group" "demo-nodes" {

\# ...

}

\`\`\`

If we run terraform plan again, it will analyze differences and preview exactly what changes: adding a managed nodegroup. We apply changes to add this group. Terraform manages resource lifecycles and dependencies automatically. We simply modify configs and Terraform handles orchestrating cloud updates.

We walked through authoring, provisioning, and managing cloud infrastructure using HCL configuration files through Terraform. This enables IaC - mitigating reliance on UIs and manual processes. Terraform facilitates declaring desired infrastructure states. It is cloud and provider agnostic, supporting multi-cloud and hybrid environments via plugins. We can enhance this example with modules, automation, resource imports, and more.

[Creating an EKS cluster using Pulumi](#contents.xhtml#sc2_153a)

Pulumi is an open-source IaC platform that makes it easy to create, deploy, and manage cloud infrastructure and applications. Pulumi allows defining infrastructure in regular programming languages like Python, TypeScript, Go, and .NET instead of using a custom domain specific language like with tools such as Terraform or CloudFormation. This brings all the benefits of programming languages and modern software development to infrastructure automation. Pulumi programs deploy to and integrate deeply with cloud services like AWS, Azure, and GCP but run anywhere with very little modification.

Some key benefits of using Pulumi over Terraform include the ability to leverage existing languages and tools, better support for configuration and secret management, reusable and shareable components, testing frameworks, and superior programming models. The Pulumi engine also handles all resource diffs and dependency tracking automatically rather than needing manual state management. The use of standard languages makes Pulumi easy to learn for most developers and brings infrastructure closer to application development teams and workflows.

To get started with Pulumi, you will first need to install the Pulumi CLI on your local machine. The latest versions are available on Pulumi's website ([https://www.pulumi.com/docs/get-started/install/](https://www.pulumi.com/docs/get-started/install/)), as well as popular package repositories such as Homebrew, Chocolatey, and Snap. Simply choose the appropriate installer for your operating system and run it to install the CLI. Once Pulumi is installed, you can login and connect it with your cloud provider account:

\`\`\`

$ pulumi login

\`\`\`

This will guide you through linking Pulumi with your AWS, Azure, or GCP account. Next, create a new project:

\`\`\`

$ pulumi new aws-typescript -s dev

\`\`\`

This initializes a TypeScript project configured for AWS. You can use your preferred supported language instead of TypeScript if you wish. This template includes configuration settings as well as some basic resource definitions to get you started. You will need to install the required packages for working with EKS:

\`\`\`

$ npm install @pulumi/kubernetes @pulumi/aws @pulumi/eks

\`\`\`

Now, we can define our EKS cluster and related resources in code. Edit index.ts and add:

\`\`\`typescript

import \* as awsx from "@pulumi/awsx";

import \* as eks from "@pulumi/eks"; 

const cluster = new eks.Cluster("my-cluster", {

 vpcId: awsx.ec2.Vpc.getDefault().id,

 desiredCapacity: 2,

 minSize: 1,

 maxSize: 2, 

});

\`\`\`

This will create a basic EKS cluster called my-cluster using our AWS account and default VPC settings. We can customize all aspects of the cluster using additional configuration. Once code is ready, we can preview the deployment and then run pulumi up which will display a preview and prompt before actually deploying the EKS cluster. Pulumi handles all provisioning, config and ensures everything is deployed in the right order. The cluster can then be accessed and managed as usual.

This demonstrates the basics of creating and deploying cloud infrastructure using Pulumi code. Combined with standard programming concepts like functions, classes, modules etc. Pulumi makes it very productive for development teams to define and manage infrastructure alongside their application code.

[Conclusion](#contents.xhtml#sc2_154a)

In this guide, we covered several different options for creating production-ready EKS clusters, ranging from the AWS Console to IaC tools to Kubernetes native tools. The AWS Console provides an easy click-through UI to create a basic cluster. Terraform is a flexible IaC tool for configurable cluster creation. CDK for TypeScript allows the creation of clusters through code in TypeScript.

Pulumi makes cluster lifecycle management easier for developers by simplifying Kubernetes native APIs. We looked at manual point-and-click creation, fully automated provisioning through code, and developer focused abstractions. Whichever option you choose, EKS handles much of the Kubernetes complexity and allows you to run container workloads easily by managing the control plane. By leveraging EKS, you can focus on your applications rather than cluster infrastructure.

[Questions](#contents.xhtml#sc2_155a)

1.  What two main advantages does EKS provide over running your own Kubernetes control plane?
2.  What tool provides a simple click-through UI for creating an EKS cluster?
3.  Which IaC tool uses TypeScript for defining cloud resources like EKS clusters?
4.  What open-source tool by Fairwinds helps simplify the management of EKS clusters?
5.  True or False: An EKS cluster can only be created using the AWS Console.

[Exercises](#contents.xhtml#sc2_156a)

1.  Use the AWS Console to create an EKS cluster with default settings for learning purposes. Delete when done.
2.  Write a Terraform configuration to create an EKS cluster across two availability zones for high availability.
3.  Use CDK for TypeScript to create an EKS cluster with managed node groups for running pods.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 8Accessing and Configuring Elastic Kubernetes Service Clusters](#contents.xhtml#ch08a)

[Introduction](#contents.xhtml#sc2_157a)

Amazon Elastic Kubernetes Service (EKS) serves as a fully managed Kubernetes environment, simplifying the deployment and operation of containerized applications. Beyond the creation of EKS clusters, a critical consideration lies in effectively accessing and tailoring configurations to align with specific application requirements.

This section is dedicated to elucidating diverse approaches for gaining access to EKS control planes, addressing authentication procedures against clusters, implementing access controls, and tailoring configurations. It spans the exploration of various tools, including CLI tools and AWS APIs, along with the utilization of Kubernetes primitives such as kubeconfig files. IAM policies and cluster settings are also delved into, providing a comprehensive understanding of the multifaceted methods available for fine-tuning the EKS environment to suit the needs of deployed applications.

[Structure](#contents.xhtml#sc2_158a)

This chapter covers the following topics:

*   Accessing the EKS cluster via the AWS Console
*   Kubeconfig for CLI access
*   Understanding Kubernetes role-based access control
*   Working with AWS IAM policies and roles
*   Customizing cluster configurations
*   Updating cluster Kubernetes version

[Objectives](#contents.xhtml#sc2_159a)

By the end of this section, readers will be equipped with the knowledge and skills to effectively access and manage Amazon EKS clusters. They will learn how to view and retrieve cluster details from the AWS Console, download kubeconfig files, and use kubectl to manage clusters from their local machines. The section will cover Kubernetes role-based access control (RBAC), AWS Identity and Access policies and roles for granting access to EKS actions, and configuration settings for EKS clusters, including updates, logging, and operational behaviors.

Additionally, readers will understand how to upgrade the Kubernetes version running on their EKS clusters, ensuring access to the latest features, security patches, and enhancements. Through hands-on exercises, they will gain practical experience in accessing and customizing a live EKS cluster, solidifying their understanding and proficiency in managing these powerful Kubernetes environments within the AWS ecosystem.

[Accessing the EKS cluster via the AWS Console](#contents.xhtml#sc2_160a)

The AWS Management Console provides a graphical interface to view details and configurations of our provisioned EKS clusters. After logging into the AWS Console, we can navigate to the EKS service. This will display a list of all EKS clusters in our account along with high level metadata like Kubernetes versions, VPC IDs, and regions. The following screenshot shows the cluster overview:

![](images/Figure_8.1.png)

Figure 8.1: EKS clusters overview page

Clicking into a specific EKS cluster provides additional tabs with further configurations including the status, cluster, service role ARNs used, etc, as shown:

![](images/Figure_8.2.png)

Figure 8.2: EKS cluster - Details view

The Resources tab allows for the viewing of workloads, node information, etc. In the following sample, we can see the running pods:

![](images/Figure_8.3.png)

Figure 8.3: EKS cluster – Resources view

Compute tab shows the different types, including node groups and Fargate profiles. You could run EKS clusters using multiple ways, including:

*   Running with managed node groups where the patching and maintenance of EC2 instances i.e. the undifferentiated heavy lifting is handled by AWS.
*   Running with Fargate profiles is a server less option and you do not have to worry about any of the underlying infrastructure.

The following sample snapshot shows this cluster is using Node groups with two t3.medium in it. Remember, you could run the cluster with a mix of multiple node groups and one or more Fargate profiles targeting various workloads to various compute types.

![](images/Figure_8.4.png)

Figure 8.4: EKS cluster – Compute view

The Networking tab shows the VPC, Subnet, and security group details. You could run your Amazon EKS cluster with IPV4 or IPV6. We will cover more information on this in our Networking chapter. The following screenshot shows the networking view, which captures the various details like VPC, Subnet, Security Group, etc.:

![](images/Figure_8.5.png)

Figure 8.5: EKS cluster – Networking view

Add-ons show any AWS integrated services like load balancing controllers, container insights, or VPC networking plugins, as shown:

![](images/Figure_8.6.png)

Figure 8.6: EKS cluster – Add-ons view

The Access tab shows the various access configurations, including the AWS IAM access entries, as follows:

![](images/Figure_8.7.png)

Figure 8.7: EKS cluster – Access configuration view

The Observability tab shows the logging of various control plane components like API server, scheduler, audit log, etc. This is disabled by default, and you can plan on enabling some or all of them depending on your business needs. The following screenshot shows the various control plane logging options which are disabled. You can click on the Manage logging link to enable the logs of your choice.

![](images/Figure_8.8.png)

Figure 8.8: EKS cluster – Observability view

The recently added Upgrade insights tab shows the readiness of your cluster for any upgrades. The Update history tracks the history of updates to your cluster components. Tags allow attaching metadata key-value pairs to our EKS clusters, as shown:

![](images/Figure_8.9.png)

Figure 8.9: EKS cluster – Tags view

Through the AWS Console, we have an easy way to visually inspect various EKS cluster details from summary information to configurations to running compute. Settings can be adjusted as needed for different access controls, Kubernetes versions, logging levels, etc. Next, we look at command line kubectl access.

[Kubeconfig for CLI access](#contents.xhtml#sc2_161a)

The kubectl command-line tool stands as a crucial instrument for administrators, facilitating the seamless management of Kubernetes clusters, including those on Amazon EKS, directly from their local machines. This tool establishes communication with the Kubernetes API server, relying on credentials specified in a kubeconfig file. To ensure proper connectivity, it is imperative to download an authenticated kubeconfig specific to each EKS cluster. Streamlining this process, the AWS Console proves to be a valuable resource, offering user-friendly features that simplify the retrieval and integration of authenticated kubeconfig files. Through this approach, administrators can efficiently harness the capabilities of kubectl, empowering them to navigate and administer EKS clusters with enhanced ease and precision. We can retrieve a working kubeconfig file for an EKS cluster using the AWS CLI:

aws eks --region us-west-1 update-kubeconfig --name my-cluster

This writes the EKS credentials into the default kubeconfig path. With an updated kubeconfig referencing our cluster, we can now run administrative kubectl commands like:

kubectl get nodes

kubectl describe deployments

kubectl logs pod/my-app

By writing the EKS credentials into the default kubeconfig path, seamless integration is established, enabling administrators to execute essential kubectl commands for effective cluster management. With an updated kubeconfig accurately referencing our cluster, a spectrum of administrative actions becomes accessible, including commands like kubectl get nodes, kubectl describe deployments, and kubectl logs pod/my-app. This not only facilitates crucial operational insights but also empowers developers to programmatically access the cluster, whether for automation scripts or workload management following the initial setup of EKS environments by infrastructure teams.

It is essential to highlight that periodic updates to the kubeconfig are necessary, especially when credentials expire or when there are alterations in access permissions. This ensures the continuous and secure functioning of administrative commands. Moreover, beyond the initial setup phase, this seamless access to kubectl commands becomes instrumental for ongoing development and operational tasks.

Looking ahead, we will delve into the configuration of more granular access controls, shedding light on methods to refine and tailor access permissions for various users and roles within the EKS environment. This not only enhances the security posture of the cluster but also ensures that access is precisely tailored to the unique requirements of different stakeholders operating within the Kubernetes ecosystem.

[Understanding Kubernetes role-based access control](#contents.xhtml#sc2_162a)

As our interaction with EKS clusters evolves, whether through direct use of kubectl or programmatically, the implementation of robust access controls becomes paramount to secure and regulate permissions among various entities. The imposition of access restrictions serves as a critical mechanism to thwart any inadvertent or unauthorized modifications to vital components within the cluster.

Kubernetes, recognizing the significance of access management, incorporates RBAC, a specialized framework tailored to administer permissions concerning Kubernetes resources and API access. RBAC policies delineate the authority bestowed upon principal entities, which may include users, developers, or applications, dictating their capability to perform actions such as reading, writing, or deleting collections of resources within the EKS environment.

For instance, RBAC allows us to configure a CI/CD pipeline with read access, enabling it to list pods for health checks while curtailing delete privileges to mitigate any risk of inadvertent tampering. Similarly, an application deployer could be granted permission to create ingresses while being restricted from altering networking configurations, ensuring granular and secure management of access privileges within the EKS cluster. This nuanced control over permissions not only fortifies the security posture of the cluster but also aligns access with the specific needs and responsibilities of diverse entities within the Kubernetes ecosystem.

RBAC authorization in EKS uses 4 main objects. We will discuss them in this section.

[Roles and ClusterRoles](#contents.xhtml#sc3_163a)

When establishing access controls in Kubernetes involves defining explicit permission rules for resources. Roles play a crucial role by limiting permissions to a specific namespace, creating a scoped approach that enhances security and isolation. These roles allow for fine-tuning access at the namespace level, tailoring permissions to the unique requirements within that specific context.

On the other hand, ClusterRoles extend this capability by applying permissions cluster-wide. This means that entities granted ClusterRoles have authority across all namespaces within the entire Kubernetes cluster. This broader scope is beneficial for scenarios where global or cluster-wide access is necessary, offering a versatile approach to managing permissions on a larger scale.

In essence, the combination of roles and ClusterRoles provides Kubernetes administrators with a flexible and scalable means of orchestrating access controls. Whether the need is for precise, namespace-specific permissions or broad, cluster-wide authority, these mechanisms afford a nuanced and powerful approach to governing resource access within the Kubernetes environment.

[Subjects](#contents.xhtml#sc3_164a)

In Kubernetes, principals refer to entities such as users, groups, or service accounts, each matched to specific roles that define their access privileges. These roles dictate the level of permissions granted to the associated principals, creating a structured and secure access framework. Users or service accounts, when designated as subjects, can be effectively tied to roles, ensuring that they inherit the specified permissions.

This linkage between principals and roles is a fundamental aspect of RBAC in Kubernetes. It allows administrators to tailor access rights with precision, aligning permissions with the roles assigned to different users, groups, or service accounts. This modular and customizable approach contributes to the robustness of access management within Kubernetes, ensuring that only authorized entities possess the necessary privileges based on their assigned roles.

[RoleBindings and ClusterRoleBindings](#contents.xhtml#sc3_165a)

In Kubernetes, RoleBindings and ClusterRoleBindings play a pivotal role in access control by binding subjects, such as users or service accounts, to corresponding roles or cluster roles. This binding operation effectively aggregates the permissions outlined in the associated role, thereby granting the user or service account-specific privileges defined by that role.

For instance, consider a scenario where a role is configured with rules allowing ConfigMap lookup and creation exclusively in the 'dev' namespace. To operationalize this, a developer IAM user can be bound as a subject to this role using a RoleBinding. As a result, the developer gains the ability to manipulate ConfigMaps within the 'dev' namespace, while being restricted from interacting with other namespaces or resources.

This fine-grained RBAC approach, when coupled with resource quotas, provides a secure means of partitioning teams and workloads within Amazon EKS across centralized clusters. It ensures that each entity has precisely the required access permissions, contributing to a robust and secure Kubernetes environment. In the subsequent exploration, we will delve into the integration of AWS IAM with access control, further enhancing the security and versatility of Kubernetes deployments on EKS.

[Working with AWS IAM policies and roles](#contents.xhtml#sc2_166a)

When humans interact with Amazon EKS through various channels such as AWS APIs, kubectl, CLI, or SDKs, the oversight of permissions diverges from Kubernetes RBAC to AWS Identity and Access Management (IAM) roles and policies. Unlike Kubernetes RBAC, IAM takes charge of high-level access control, regulating the ability to execute actions against EKS, while RBAC concentrates on the finer details of Kubernetes resource operations within the cluster.

IAM roles play an important role in this context by delegating access to AWS services, including EKS, contingent upon the attached managed and custom policies. This delegation empowers organizations to meticulously define and allocate permissions based on the principle of least privilege. Consequently, users and teams within organizations managing multiple EKS clusters can assume distinct IAM roles aligned with their specific job functions.

This role-based approach enhances security and governance, allowing organizations to tailor access rights for different roles within the EKS environment. For instance, an operations team might assume a role with permissions to modify cluster configurations, while developers could be granted a role focused on deploying and managing applications within the EKS clusters. Such flexibility, coupled with the robustness of IAM policies, contributes to a well-structured and secure access management paradigm for human interactions with EKS across diverse use cases.

For example, an EKS administrator role can utilize wide privileges to create and configure clusters through policies like:

*   AmazonEKSAdminPolicy
*   AmazonEKSFullAccess 
*   AmazonEKSClusterPolicy

Developers assume more restrictive roles, only allowing interaction with deployed workloads:

*   AmazonEKSStepFunctionsIngressPolicy
*   AmazonEC2ContainerRegistryReadOnly
*   AmazonEKSClusterPolicy

IAM roles are locally attached, either via the AWS CLI or AWS Console, before users’ issue kubectl commands to interact with Amazon EKS. The permissions associated with these IAM roles follow a cascading model, allowing for a granular approach that tailors access rights from broad EKS administrative capabilities down to more focused permissions for application developers, aligning with their respective identities and responsibilities.

IAM authorization integrates with various identity management systems, including LDAP, SAML providers, and identity federation. This integration simplifies associating organizational users with specific AWS permissions, offering a unified approach to access control. Multiple authentication methods, such as SAML, external credentials, or role assumption, provide a flexible framework for access delegation, accommodating diverse user requirements.

The combination of IAM and RBAC delivers a comprehensive access control strategy for EKS operations and in-cluster resource configurations. IAM governs access to AWS services, while RBAC ensures the precise management of Kubernetes resources within the cluster. In the subsequent sections, we will delve into common EKS cluster configurations, further enhancing the understanding of optimal practices for managing and securing EKS environments.

[Customizing cluster configurations](#contents.xhtml#sc2_167a)

Amazon EKS provides extensive customization options for managing Kubernetes clusters, including version upgrades, logging, secrets encryption, networking, updates and recovery, scaling, IAM roles, and add-ons. Administrators can tailor these settings to align with their organization's operational preferences, security requirements, and workload demands. The platform integrates with various AWS services, enabling seamless interactions and optimized performance for containerized workloads. EKS add-ons further extend the functionality, offering tools and services that complement the core Kubernetes capabilities. Let us explore the key options available in this section.

[Version upgrades](#contents.xhtml#sc3_168a)

Customizing the upgrade behavior for Amazon EKS Kubernetes versions involves configuring specific settings that dictate how managed node groups respond to updates. These settings encompass the automatic updating of minor versions and preferences for notifications.

Administrators have the flexibility to define whether managed node groups should undergo automatic updates when newer minor versions are available. Additionally, the notification preferences can be tailored to provide timely alerts or updates regarding the upgrade process. This level of configuration empowers EKS users to align upgrade practices with their operational preferences, ensuring a seamless and controlled evolution of the Kubernetes environment.

[Logging](#contents.xhtml#sc3_169a)

In Amazon EKS, administrators have the ability to fine-tune control plane logs by enabling or disabling them for specific audit events or authenticator patterns. This customizable feature allows organizations to tailor their logging strategy based on specific requirements. The log data can be directed to Amazon CloudWatch or Amazon S3, offering flexibility in choosing the storage solution that aligns with organizational preferences and compliance needs.

Furthermore, administrators can delineate additional log types, such as API server audit logs and authenticator logs, providing a comprehensive view of the activities within the EKS environment. This nuanced control over logging mechanisms contributes to robust monitoring and auditing practices, enhancing overall visibility and security.

[Secrets encryption](#contents.xhtml#sc3_170a)

In Amazon EKS, administrators can enhance security by configuring envelope encryption using AWS Key Management Service (KMS) for sensitive information, such as access tokens within the EKS cluster. This approach involves encrypting the secrets with KMS, providing an additional layer of confidentiality protection. By leveraging AWS KMS, organizations can enforce secure encryption practices, safeguarding sensitive data against unauthorized access.

This configuration ensures that access tokens and other critical information remain confidential, contributing to a robust security posture for EKS clusters. The integration with AWS KMS aligns with best practices in data protection, offering a streamlined solution for encryption management within the EKS environment.

[Networking](#contents.xhtml#sc3_171a)

In Amazon EKS, administrators have the flexibility to tailor networking features according to specific requirements. This customization extends to features such as cross-zone load balancing, enabling efficient distribution of traffic across availability zones. Additionally, administrators can leverage Container Network Interface (CNI) plugins to enhance and customize networking configurations, ensuring optimal performance for containerized workloads.

The customization also encompasses VPC endpoint access, allowing controlled and secure communication between EKS clusters and other AWS services. Furthermore, administrators can configure both public and private access for scaling pod network connectivity, providing a versatile approach to meet different use cases. This level of customization empowers organizations to optimize networking features in alignment with their unique operational and security needs within the EKS environment.

[Updates and recovery](#contents.xhtml#sc3_172a)

In Amazon EKS, administrators have granular control over the management of control plane updates, including the ability to configure update frequency, maintenance windows, and auto-recovery mechanisms. This level of control empowers organizations to tailor the update process based on their operational preferences and downtime considerations. Administrators can define how frequently control plane updates are applied, set specific maintenance windows to minimize disruption and implement auto-recovery mechanisms to facilitate self-healing in case of unexpected issues.

This comprehensive control over update parameters ensures a proactive and customized approach to maintaining the EKS control plane, handling patches, and upgrading Kubernetes versions. Such capabilities contribute to a robust and resilient EKS environment, aligning with best practices in ensuring continuous availability and self-healing capabilities within the Kubernetes ecosystem.

[Scaling](#contents.xhtml#sc3_173a)

Amazon EKS provides administrators with the ability to set auto-scaling thresholds for the cluster autoscaler, which efficiently manages worker node pools. This dynamic capability enables the system to respond dynamically to fluctuating pod demands, optimizing resource utilization. Administrators can establish auto-scaling thresholds based on various metrics, such as CPU thresholds, to ensure that the cluster can efficiently scale in or out in response to workload changes.

This level of customization allows organizations to align the scaling behavior with specific performance indicators, enhancing the overall responsiveness and efficiency of the EKS cluster. By leveraging auto-scaling thresholds, administrators can automate the adjustment of worker node pools, ensuring a seamless and cost-effective scaling experience that is well-aligned with the evolving demands of containerized workloads.

[IAM roles](#contents.xhtml#sc3_174a)

In Amazon EKS, administrators have the capability to attach IAM roles specifically designated for pod execution. This facilitates the granting of granular, pod-level permissions, enhancing the security and control of interactions between pods and other AWS services. By attaching IAM roles or utilizing service accounts, organizations can seamlessly integrate their EKS clusters with various AWS services, ensuring a secure and streamlined communication channel. This integration supports a wide range of use cases, allowing pods to interact with other AWS resources with the appropriate level of access permissions. This granular approach to IAM roles for pod execution enhances flexibility and security, aligning with best practices for managing permissions within the EKS environment.

[Add-ons](#contents.xhtml#sc3_175a)

Amazon EKS add-ons provide additional functionalities and features to enhance the management and operation of Kubernetes clusters on the EKS platform. These add-ons are designed to simplify and extend key aspects of EKS, offering tools and services that complement the core Kubernetes functionality. Examples of EKS add-ons include the Amazon VPC CNI plugin, which optimizes networking performance for containerized workloads, and the AWS Load Balancer Controller, streamlining the integration of Amazon EKS with AWS Load Balancers.

Other EKS add-ons include the Amazon EBS CSI Driver for seamless integration with Elastic Block Store volumes, the Amazon EFS CSI Driver for efficient utilization of Elastic File System storage, and the CoreDNS add-on, enhancing DNS management within EKS clusters. These add-ons contribute to a more comprehensive and efficient EKS ecosystem, addressing various operational needs.

EKS add-ons are continuously evolving, reflecting AWS's commitment to providing a robust and extensible Kubernetes experience. They empower users to tailor their EKS clusters to specific requirements, ensuring a flexible and scalable Kubernetes deployment on the AWS platform.

These setting areas allow customization for security, access, scaling, auditing, and other operational policies. Additional integrations are available too for observing clusters using Prometheus or extending functionality with other AWS managed solutions around machine learning, data workflows, application integration, and more.

[Updating cluster Kubernetes version](#contents.xhtml#sc2_176a)

A key aspect of managing EKS clusters long term is staying up to date with Kubernetes versions. New upstream Kubernetes releases add features, security patches, bug fixes, and other enhancements.

EKS supports simple upgrades of control plane Kubernetes versions. Upgrades patch the cluster without impacting running applications or worker nodes. This allows accessing the latest stability fixes and Kubernetes API additions in the control plane.

We perform version upgrades via AWS Console or eksctl tooling:

[AWS Console](#contents.xhtml#sc3_177a)

Navigate to cluster. From here, you can update various components. Let us start with EKS add-ons updates. When you get into the Add-ons tab, you will be able to see how many add-ons are available for update. The following screenshot shows the Add-ons view, which specifically lists the CoreDNS add-on details. From here you can click on the update version link to update the add-on:

![](images/Figure_8.10.png)

Figure 8.10: EKS cluster – CoreDNS add-on details view

You could choose, for example, the CoreDNS add-on and update to the latest version as shown:

![](images/Figure_8.11.png)

Figure 8.11: EKS cluster – Choosing the version of CoreDNS

Also, you could try to update the cluster’s Kubernetes version. For example, in the following snapshot, we have two clusters named demo2 and demo3 which are running Kubernetes version 1.27. At the time of writing, the latest version available was 1.29. Hence, under the Kubernetes version column, you can see the Update now link as shown:

![](images/Figure_8.12.png)

Figure 8.12: EKS cluster – Overview page showing the version upgrade options

Whilst the above tab helps in upgrading the Kubernetes version for the control plane components, you can get into the Compute tab and update your compute instances’ Kubernetes version as well. For example, in the following figure, the data pane components of your cluster are running 1.27. From here, click on the Update now link to enable your data plane components to be up to date.

![](images/Figure_8.13.png)

Figure 8.13: EKS cluster – Compute view showing updating Node group options

Amazon EKS has the Upgrades insights tab which shows the insights for your cluster focusing on upgrades. In the following snapshot, the upgrade insights show the deprecated APIs that are scheduled to be removed to the latest 1.29 version. This gives an idea of what changes need to be made before you can start updating your cluster components.

![](images/Figure_8.14.png)

Figure 8.14: EKS cluster – Upgrade insights view

[eksctl](#contents.xhtml#sc3_178a)

The second option is to use the eksctl command line to upgrade your cluster. For example, use the upgrade cluster subcommand specifying target Kubernetes release:

eksctl upgrade cluster --name my-cluster --kubernetes-version 1.29

In addition to the automatic updates initiated by Amazon EKS, it is crucial to ensure version alignment between the control plane and worker node groups. This synchronization helps maintain a cohesive and well-coordinated Kubernetes environment. To stay current with the latest features and enhancements, it is advisable to diligently test clusters on new versions, closely monitor Kubernetes release notes, and establish a routine for upgrading production environments. EKS provides backports for certain fixes, but opting for the latest versions ensures access to the most up-to-date patches and advancements in Kubernetes.

By actively participating in version testing and keeping abreast of Kubernetes developments, organizations can proactively address potential issues and leverage the latest capabilities offered by EKS. Regular upgrades not only enhance security and performance but also contribute to a more resilient and efficient operation of EKS clusters within the AWS environment.

[Conclusion](#contents.xhtml#sc2_179a)

In this section, we explored the breadth of capabilities around accessing, integrating with, and customizing EKS clusters beyond just initial provisioning. We used the AWS Console to visually inspect clusters, downloaded authenticated kubeconfig files for CLI kubectl usage, configured fine-grained access with RBAC and IAM, tuned settings to scale and update behavior, and upgraded Kubernetes versions.

EKS provides many integrations, configurations, and tools for managing the entire cluster lifecycle. Between Console UIs, SDK APIs, CLI tooling, and Kubernetes native tooling, there are diverse options to fit administrative needs and automation requirements. Practices like controlling access, upgrading versions, and monitoring logs and health help maintain robust, production-grade EKS environments.

Other capabilities like EKS Distro, EKS add-ons, and EKS Anywhere further expand on-premises to multi-cloud Kubernetes management under a single control plane. With modular access controls, upgrades, and config combined with expanding hybrid/multi-cloud management, EKS provides a reliable Kubernetes platform for both infrastructure architects and application developers.

[Review questions](#contents.xhtml#sc2_180a)

1.  What two main advantages does EKS provide over running your own Kubernetes control plane?
2.  What tool provides a simple click-through UI for creating an EKS cluster?
3.  Which infrastructure as code tool uses TypeScript for defining cloud resources like EKS clusters?
4.  True or False: An EKS cluster can only be created using the AWS Console.

[Answers](#contents.xhtml#sc3_181a)

1.  Automated patching, upgrades and scaling of the Kubernetes control plane and Integrations with complementary AWS services like load balancing, auto scaling etc.
2.  The AWS Management Console.
3.  AWS Cloud Development Kit.
4.  False. EKS clusters can be created through CloudFormation, Terraform, Kubernetes YAML, AWS CLI, etc.

[Exercises](#contents.xhtml#sc2_182a)

1.  Use the AWS Console to access an existing EKS cluster and view current configurations and details of compute like node groups.
2.  Download an updated kubeconfig file for an EKS cluster and confirm kubectl access by listing pods.
3.  Create an IAM policy granting permissions to list cluster details and attach it to a demo IAM user. Confirm user can view cluster metadata.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 9Deploying Sample Apps on AWS Elastic Kubernetes Service Clusters](#contents.xhtml#ch09a)

[Introduction](#contents.xhtml#sc2_183a)

Amazon EKS stands as a comprehensive solution, offering a fully managed Kubernetes environment that simplifies the deployment and operation of containerized applications. After the initial creation of an EKS cluster, a crucial progression involves the deployment of sample workloads to validate the functionality and connectivity of the cluster.

Within this chapter, our focus extends to diverse methodologies for running demonstration applications on Amazon EKS. These methods are instrumental in testing essential capabilities such as auto-scaling, service networking, and load balancing in a secure and isolated environment. The exploration encompasses the utilization of namespaces, fundamental Kubernetes primitives, and Helm charts, providing a versatile toolkit for launching and evaluating applications within the EKS environment. This hands-on approach not only validates the integrity of the cluster but also empowers users to gain practical insights into the dynamic functionalities offered by Amazon EKS, enhancing their proficiency in managing containerized workloads within a Kubernetes framework.

[Structure](#contents.xhtml#sc2_184a)

This section is structured into several pivotal sections as below:

*   Namespace isolation
*   Deploying pods
*   Creating services
*   Configuring Ingress
*   Leveraging Helm
*   Integrating storage
*   Managing rollouts
*   Using service mesh
*   Horizontal pod autoscaling
*   Exploring monitoring

[Objectives](#contents.xhtml#sc2_185a)

Upon completion of this module, you will have a comprehensive understanding of essential concepts in managing Kubernetes deployments on Amazon EKS. This includes grasping the significance of namespace isolation for effectively partitioning applications. You will also gain proficiency in deploying containerized pods on EKS, enabling seamless execution of workloads.

Furthermore, the module will equip you with the skills to establish networking capabilities through Kubernetes services and efficiently route traffic using Ingress resources. The use of the Helm package manager will be demystified, allowing you to streamline application launches effectively. Understanding how to provide stateful storage for applications will enhance your capability to manage data persistence.

The module covers the intricacies of performing rolling updates to applications, ensuring smooth transitions and minimal disruptions. Security aspects are addressed through insights into securing application networking with service mesh, along with guidelines on safely exposing applications externally.

Automation takes center stage with the module providing knowledge on automating pod scaling based on metrics. Additionally, you will learn to visually track the status of applications and the environment, enhancing your ability to monitor and maintain a healthy deployment. Ultimately, the module ensures hands-on experience, enabling you to deploy fully operational applications confidently.

[Namespace isolation](#contents.xhtml#sc2_186a)

Namespaces in Amazon EKS serve as a critical component, offering logical separation to efficiently partition applications, teams, or environments that coexist within the same EKS cluster. This logical separation extends to the point where different namespaces can house workloads sharing the same physical infrastructure, ensuring isolation and minimizing interference.

A practical application of this is evident when running both production and development environments within separate namespaces on the same EKS cluster, denoted as prod and dev namespaces. By associating resources such as pods, services, and Ingress objects with specific namespaces, resource usage quotas can be implemented. This segregation facilitates the sharing of an EKS cluster among multiple teams without encountering contention, ensuring that each namespace operates independently within its defined boundaries.

This organizational structure enhances collaboration and flexibility, allowing teams to coexist within the same EKS cluster without compromising the integrity and performance of their respective workloads. The utilization of namespaces is a powerful tool in optimizing resource allocation and fostering a well-organized and efficient Kubernetes environment within Amazon EKS.

We create a namespace for our demo via YAML:

apiVersion: v1

kind: Namespace

metadata:

name: demo

Apply with kubectl:

kubectl apply -f namespace.yaml

In establishing a dedicated environment for our demonstration within the Amazon EKS cluster, we initiate the process by crafting a namespace using YAML configuration. This YAML file, denoted as 'namespace.yaml,' is structured to define the desired namespace characteristics, including its name ('demo' in this instance). Once the configuration is finalized, the 'kubectl apply' command is employed to execute the deployment, specifying the YAML file as the input. This action sets the stage for a logical partition within the EKS cluster, ensuring that any subsequent resources created within the environment default to this designated namespace.

The creation of a dedicated namespace holds strategic importance, particularly for isolating the demo application and preventing any inadvertent interactions or conflicts with other components within the EKS cluster. This logical segregation serves as a crucial organizational element, providing a clear and distinct boundary for the isolated demo app.

With the namespace in place, the subsequent step involves deploying sample pods, which will inherently inherit the properties of the designated namespace. This systematic approach to namespace creation and resource allocation contributes to a well-organized and secure deployment of our demonstration within the broader EKS environment. The use of YAML configuration in tandem with kubectl commands offers a streamlined and repeatable process for establishing these foundational elements within the Kubernetes ecosystem on Amazon EKS.

[Deploying pods](#contents.xhtml#sc2_187a)

In the Kubernetes ecosystem, pods serve as the fundamental building blocks, representing the smallest deployable units for containerized applications within a cluster. These pods encapsulate not only the application containers but also encompass additional components, including storage resources, network configuration, and runtime specifications. The design philosophy behind pods is rooted in the notion of grouping closely related containers, fostering collaboration and efficient communication among them.

Within a pod, containers share the same network namespace, allowing them to communicate seamlessly over the localhost interface. This shared network context enhances the coordination and integration of multiple containers within the same pod. Moreover, pods possess a shared storage volume, enabling data sharing among co-located containers. This co-location of containers within a pod facilitates the creation of tightly coupled and interdependent application components, contributing to streamlined communication and resource utilization.

The concept of pods in Kubernetes aligns with the microservices architecture, promoting modular design and scalability. Each pod encapsulates a cohesive set of functionalities, and their isolation ensures that individual containers within a pod can be independently scaled or managed. This design principle of pods encapsulating containers, storage, and network configurations exemplifies Kubernetes' approach to orchestrating containerized applications, fostering flexibility, and ease of management within the cluster. We deploy pods to execute demonstration workloads. A simple pod definition for an Nginx server looks like:

apiVersion: v1

kind: Pod

metadata:

name: my-nginx

namespace: demo

labels:

app: nginx

spec:

containers:

\- name: my-nginx

image: nginx

This pulls a container image for the open-source Nginx web server and runs it in a pod instance. We create the pod on EKS:

kubectl apply -f pod.yaml

kubectl get pods -n demo

In the operational lifecycle of a pod within the Amazon EKS environment, the runtime status undergoes a series of transitions, commencing with 'Pending' and progressing to 'Running.' This transition signifies the successful initialization of the container encapsulated within the pod structure on EKS worker node resources. At this stage, the pod operates in isolation, functioning as a standalone unit within the cluster.

To enhance application reliability and availability, a strategic next step involves scaling pod instances to create a clustered environment. Scaling facilitates the deployment of multiple instances of the pod, distributing the application workload and providing redundancy. This not only augments performance but also fortifies the system against potential failures.

Additionally, to expose and manage networking for these scaled pod instances, various Kubernetes mechanisms such as services and Ingresses can be employed. Services act as stable network endpoints, allowing external or internal access to the pods, while Ingresses provide a robust solution for routing and load balancing incoming traffic to the relevant pod instances. These networking components play a pivotal role in extending the reach and accessibility of applications running within the EKS cluster, contributing to a resilient and scalable deployment infrastructure.

[Creating services](#contents.xhtml#sc2_188a)

In the Kubernetes ecosystem, services play a crucial role in establishing stable networking and load balancing mechanisms, facilitating streamlined access to pods through dynamic cluster endpoints. These services act as abstraction layers, grouping together replicas of pods under a unified internal DNS addressing scheme. This addressing system enhances the manageability and accessibility of pod instances within the cluster.

The primary function of services extends beyond mere addressing. They incorporate load balancing capabilities. As multiple pod replicas can exist to ensure redundancy and scalability, a service efficiently distributes incoming traffic among these replicas, thus balancing the load across the entire application. This load balancing mechanism not only enhances the overall performance of the application but also ensures optimal resource utilization.

The grouping of pod replicas within a service introduces a level of abstraction that shields external entities from the underlying complexities of the dynamic pod environment. This abstraction ensures that clients interacting with the application can rely on a consistent and stable interface provided by the service, promoting reliability and continuity.

Furthermore, services in Kubernetes are categorized into different types, including ClusterIP, NodePort, and LoadBalancer, each serving distinct purposes. These types afford flexibility in choosing the most suitable networking configuration based on specific application requirements and deployment scenarios. Overall, Kubernetes services emerge as a cornerstone for efficient and scalable networking, essential for the seamless functioning of containerized applications within a dynamic and distributed environment like Amazon EKS. We create a service manifest for our Nginx deployment:

apiVersion: v1

kind: Service

metadata:

name: nginx-service

namespace: demo

spec:

 ports:

 - port: 80 

 selector:

app: nginx

The provided YAML snippet defines a Kubernetes Service named nginx-service. This service specification includes details such as the service type, which, in this case, is ClusterIP (default), and port configuration, where it is set to listen on port 80. The 'selector' field indicates that this service is intended to route traffic to pods labeled with app: nginx.

Upon applying this service configuration using the kubectl apply command, the Kubernetes cluster gains a networking abstraction layer. This layer enables communication with pods labeled as app: nginx, allowing seamless access to instances of the Nginx application. The service automates the discovery and load balancing of pods, ensuring that any new pod additions with the specified label dynamically join the service pool. Apply the following service:

kubectl apply -f service.yaml

In essence, this service declaration simplifies the networking complexity by abstracting the underlying pod details. It acts as a centralized entry point for accessing instances of the Nginx application, handling the distribution of incoming requests across relevant pods. As a result, this not only facilitates scalability by supporting the addition of new pod instances but also streamlines the routing of traffic, contributing to the overall efficiency and reliability of the containerized application within the Kubernetes environment. For external access, we set up Ingress routing.

[Configuring Ingress](#contents.xhtml#sc2_189a)

In the orchestration of containerized applications within Amazon EKS, the role of services extends beyond managing internal communications among application components. Here, the spotlight shifts to Ingress resources, which are pivotal components responsible for efficiently handling external traffic routing from the cluster perimeter to the internal services.

In the Kubernetes architecture, Ingress operates as an HTTP router positioned at the edge of our EKS environment. It serves as a gateway, diligently observing external requests directed at the cluster and orchestrating the routing of this traffic based on defined rules to the relevant cluster services. Unlike services, which primarily focus on internal communication, Ingress steps into the realm of external access, bridging the gap between the outside world and the internal components of the Kubernetes cluster.

Configuring Ingress involves specifying rules that dictate how incoming requests should be directed, often based on URL paths, hostnames, or other criteria. This fine-grained control allows for efficient management of external access points, ensuring that requests are directed to the appropriate services within the cluster. Additionally, Ingress can be integrated with TLS termination, enabling secure communication by handling SSL/TLS certificates.

The deployment of Ingress resources within the EKS environment significantly enhances the external accessibility and manageability of applications, providing a centralized and flexible mechanism for handling external traffic. This strategic utilization of Ingress, in conjunction with internal services, contributes to a comprehensive and well-architected solution for handling both internal and external communication within the Kubernetes ecosystem. A sample Ingress for our pods is as follows:

apiVersion: networking.k8s.io/v1

kind: Ingress

metadata:

name: my-ingress

spec:

rules:

\- host: my.app.com

http:

paths:

\- pathType: Prefix

path: "/"

backend:

service:

name: nginx-service

port:

number: 80

In the orchestration of containerized applications within Amazon EKS, Ingress plays a crucial role in facilitating external access by observing a specified domain, such as my.app.com. This component serves as a gateway, efficiently forwarding incoming requests that match the defined criteria to a pre-specified backend, typically a service within the cluster, such as the Nginx service listening on port 80.

Deploying Ingress involves applying a configuration, often defined in a YAML file (for example, ingress.yaml), using the kubectl apply command. This configuration outlines the rules and conditions for directing external traffic, establishing a seamless link between the external domain and the internal services. Creating the Ingress applies the configuration:

kubectl apply -f ingress.yaml

Once the Ingress is applied, external clients gain the ability to access the application through my.app.com. The Ingress resource, acting as an intelligent traffic director, ensures that incoming requests are efficiently routed to the appropriate pod service, in this case, the Nginx service on port 80. This not only streamlines the external accessibility of the application but also centralizes the management of routing rules, providing a versatile and scalable solution for handling external traffic within the Kubernetes ecosystem. The utilization of Ingress further underscores the adaptability and efficiency of EKS in managing diverse and dynamic application scenarios. For simplified application deployment, we look at using Helm next.

[Leveraging Helm](#contents.xhtml#sc2_190a)

Helm, in the realm of Kubernetes orchestration, stands out as a sophisticated package manager, offering a native and streamlined experience for the deployment of applications and their dependencies through entities known as charts. These charts serve as comprehensive packages that encapsulate the essential elements needed for deploying a particular application, including pod templates, services, and Ingress configurations, while also incorporating parameterized deployment variables for enhanced flexibility and customization.

The bundling nature of charts ensures that all the installation configurations required for a specific application are encapsulated within a single, cohesive package. This approach simplifies the deployment process, making it more efficient and reducing the likelihood of errors. Installing a Helm chart translates to orchestrating the entire setup of a fully defined application in a single, consolidated step.

Helm further augments its utility by offering versioning, templating, and dependency management features. With versioning, users can track and manage different iterations of their application configurations, promoting efficient version control. Templating enables the reuse of configurations across diverse environments, enhancing the portability and consistency of deployments. Meanwhile, Helm's dependency management ensures that all necessary components and resources are seamlessly integrated, fostering a reliable and comprehensive deployment experience. The utilization of Helm charts underscores its role as a pivotal tool in simplifying and standardizing the deployment lifecycle of applications within Kubernetes environments. For example, the Nginx chart allows declaring config like replica counts, node selectors, resources limits, and an entire Nginx deployment is created:

helm repo add bitnami https://charts.bitnami.com/bitnami

helm repo update

helm install my-nginx nginx \\

\--set=replicaCount=3 \\

—set=resources.limits.cpu=200m

The Helm command, exemplified by helm install my-nginx nginx --set=replicaCount=3 --set=resources.limits.cpu=200m, demonstrates the versatility of Helm charts in streamlining the deployment of complex applications like MySQL, MongoDB, Jenkins, and countless others accessible through public Helm repositories. This approach allows users to specify deployment configurations, such as the replica count and CPU resource limits, directly within the Helm install command, simplifying the customization and scaling of applications.

Helm's methodology is particularly advantageous for managing intricate workloads within Kubernetes environments, providing a structured and parameterized way to define pod replicas and allocate resources. By utilizing Kubernetes features such as namespaces, pods, services, and Ingress in conjunction with Helm, users can create a robust and flexible environment for launching diverse workloads on Amazon EKS. This facilitates efficient testing of application functionality and ensures a seamless deployment experience.

Beyond deployment, the next critical step involves addressing stateful data persistence, a crucial aspect for applications like databases. Helm's comprehensive approach, encompassing not only the deployment but also the ongoing management and customization of workloads, solidifies its role as an indispensable tool for managing the intricacies of applications within the dynamic Kubernetes ecosystem. Next, we will ensure stateful data persists.

[Integrating storage](#contents.xhtml#sc2_191a)

In the realm of Kubernetes, containers and pods excel in creating computational environments, yet the challenge arises when there is a need to preserve stateful data, such as database contents or uploaded files, beyond the lifecycle of individual containers. Addressing this requirement necessitates external persistence mechanisms that can endure the dynamic nature of containerized workloads.

This is where Kubernetes StorageClasses play a pivotal role. StorageClasses serve as declarative configurations that define various storage providers, catering to diverse environments, including public clouds, on-premises solutions, and virtualized setups. These StorageClasses act as a bridge between Kubernetes clusters and the underlying storage infrastructure, providing a standardized way to request and allocate persistent storage dynamically.

Dynamic volume provisioning is a key capability enabled by StorageClasses. This feature automates the allocation of storage resources based on predefined policies and requirements, ensuring that stateful workloads have access to the appropriate storage assets. This dynamic provisioning not only streamlines the management of persistent storage but also enhances the scalability and adaptability of Kubernetes clusters, catering to the varying needs of stateful applications across different storage backends. In essence, the integration of StorageClasses in Kubernetes adds a layer of abstraction, simplifying the orchestration of persistent storage resources for stateful workloads within the dynamic and evolving containerized ecosystem. For example, to run MySQL on EKS, we need durable space for the database itself. We create a StorageClass targeting EBS volumes:

apiVersion: storage.k8s.io/v1

kind: StorageClass

metadata:

name: ebs-sc

provisioner: ebs.csi.aws.com

This provides managed EBS volumes to our cluster. We next author a PersistentVolumeClaim requesting storage from this class:

apiVersion: v1

kind: PersistentVolumeClaim

metadata:

name: mysql-pv-claim

spec:

accessModes:

\- ReadWriteOnce

storageClassName: ebs-sc

resources:

requests:

storage: 10Gi

We allocate 10 GB of space. A MySQL StatefulSet can mount this volume for durable storage:

volumes:

\- name: mysql-data

persistentVolumeClaim:

claimName: mysql-pv-claim

In summary, the provided Kubernetes manifest illustrates the creation of a StorageClass named ebs-sc that utilizes the AWS EBS CSI provisioner. This StorageClass definition establishes a framework for dynamically provisioning managed EBS volumes within our Kubernetes cluster. Subsequently, a PersistentVolumeClaim (PVC) named mysql-pv-claim is authored, explicitly requesting storage from the previously defined ebs-sc StorageClass. In this case, we allocate 10 gigabytes of space.

This PersistentVolumeClaim is designed to cater to the storage requirements of a MySQL StatefulSet. The MySQL StatefulSet can then mount the requested volume (mysql-data) for durable storage, ensuring that the MySQL data persists across container lifecycles.

The integration of EBS volumes into the Kubernetes lifecycle allows MySQL to run seamlessly on Amazon EKS, leveraging the reliable and performant storage provided by EBS. This native integration simplifies the management of storage resources, offering a robust and scalable solution for containerized workloads within the Kubernetes ecosystem. We next look at application updates leveraging storage.

[Managing rollouts](#contents.xhtml#sc2_192a)

Kubernetes, with its robust orchestration capabilities, facilitates the incremental updating of applications using managed rollouts, a feature particularly well-suited for this purpose is StatefulSets. This functionality empowers operators to update applications in a controlled manner, ensuring a seamless and zero-downtime transition during the deployment of changes. The StatefulSets mechanism provides a structured approach to managing the rollout of updates, enabling phased launches and effectively mitigating risks associated with changes to applications.

Through StatefulSets, Kubernetes ensures that each replica of a pod in the deployment has a unique and persistent identifier. This unique identity is crucial for maintaining stateful workloads, such as databases, where preserving data and identity across updates is paramount. StatefulSets bring order to the update process by sequentially updating each pod instance, minimizing disruptions and potential impact on the overall application.

This approach aligns with best practices in software deployment, allowing operators to verify the stability and health of each updated pod before proceeding to the next. By employing managed rollouts with StatefulSets, Kubernetes empowers users to confidently evolve their applications, embracing change with a structured and controlled methodology that prioritizes reliability and minimizes any adverse effects on ongoing operations. For example, we may modify our Nginx container image to a new 1.21.x tag and need to push the update. A rolling update slowly cycles pod instances behind the service endpoint to the new version:

apiVersion: apps/v1

kind: Deployment

metadata:

name: nginx

spec:

replicas: 10

strategy:

type: RollingUpdate

rollingUpdate:

maxSurge: 3

maxUnavailable: 2

selector:

matchLabels:

app: nginx

template:

metadata:

labels:

app: nginx

spec:

 containers:

\- name: nginx

image: nginx:1.21.1

The provided Kubernetes deployment manifest exemplifies a strategy for managing the incremental update of the 'nginx' application. The specification indicates the desired state, with 10 replicas of the 'nginx' container. The rollout strategy is defined as a RollingUpdate, configured with parameters like maxSurge (3) and maxUnavailable (2). These settings dictate how Kubernetes should manage the transition during the update process, ensuring a balanced approach.

By setting maxSurge, Kubernetes allows for the creation of a specified number of additional pods beyond the desired replica count during the update. Simultaneously, maxUnavailable specifies the maximum number of pods that can be unavailable during the update. This careful orchestration ensures that the capacity requirements are met throughout the transition, preventing disruptions and maintaining the desired level of availability.

Upon initiating this manifest change using kubectl apply, Kubernetes takes charge of the upgrade process behind the scenes. The deployment orchestrates the rolling update, seamlessly transitioning from the previous image to the new 'nginx:1.21.1' across all 10 replicas. This approach prioritizes a smooth and controlled application transition, exemplifying Kubernetes' capability to efficiently manage updates while maintaining the desired state and availability of the application. For more reliability between pod communication, we explore service meshes next.

[Using service mesh](#contents.xhtml#sc2_193a)

Service meshes, a crucial component in modern microservices architectures, introduce embedded proxies alongside application code to facilitate advanced communication, observability, and control between services. Esteemed options in the realm of service meshes, such as Istio, Linkerd, and Consul Connect, play a pivotal role in orchestrating and managing service-to-service connectivity within complex distributed systems.

Istio, a prominent service mesh solution, integrates seamlessly with Kubernetes, offering features like traffic management, security, and observability. Linkerd, another popular choice, focuses on simplicity and reliability, providing lightweight and transparent proxying to enhance communication reliability between services. Consul Connect, part of the Consul service mesh, excels in delivering secure service-to-service communication with features like automatic TLS encryption and identity-based access controls.

These service mesh solutions significantly alleviate the challenges associated with communication in microservices architectures. By embedding proxies alongside application code, they enable functionalities like load balancing, circuit breaking, and retries, enhancing the reliability and resilience of service-to-service communication. Additionally, service meshes provide robust observability tools, allowing for detailed insights into the performance and behavior of microservices, thereby streamlining troubleshooting and optimization efforts within dynamic and distributed environments. For example, Istio injects an Envoy proxy container into each pod:

apiVersion: apps/v1

kind: Deployment

metadata:

name: myapp-deployment

spec:

template:

metadata:

annotations:

sidecar.istio.io/inject: "true"

spec:

containers:

\- name: myapp

image: myapp:1.0

This transparently adds functionality like mutual TLS authentication, failure recovery, circuit breakers, routing rules and metrics telemetry between pods wrapped by the service mesh. Platform reliability capabilities become baked into applications themselves.

Istio simplifies managing pod communication with intelligent proxying. Next, we explore options for safely exposing apps externally to clients while maintaining control.

[Horizontal pod autoscaling](#contents.xhtml#sc2_194a)

Kubernetes horizontal pod autoscaling (HPA) represents a crucial feature in the dynamic orchestration of containerized applications, enabling the automatic adjustment of pod replicas based on real-time demand metrics, commonly measured through factors like CPU utilization. This intrinsic capability empowers Kubernetes clusters to autonomously scale resources up or down, ensuring that the application environment aligns with the fluctuating demands imposed by varying workloads.

By leveraging HPA, organizations can achieve optimal resource utilization and cost efficiency. When demand surges, HPA dynamically increases the number of pod replicas, effectively distributing the workload and preventing resource constraints. Conversely, during periods of lower demand, HPA scales down the number of replicas, freeing up resources and optimizing operational costs.

This self-adjusting nature of HPA streamlines the management of containerized workloads, allowing Kubernetes to respond to changes in demand without manual intervention. Metrics such as CPU utilization serve as the indicators for triggering scaling actions, providing a reliable mechanism for adapting the infrastructure to the evolving needs of the application. In essence, Kubernetes HPA embodies the principles of elasticity and efficiency, fostering a dynamic and responsive ecosystem for containerized applications within the Kubernetes framework. In addition to Horizontal Pod Autoscaler, there are other types like Vertical Pod Autoscaler, event driven autoscaling etcetera. We will dive into this topic in the upcoming [Chapter 11](#ch11.xhtml), Scaling EKS workloads. Our Nginx deployment can scale using HPA:

apiVersion: autoscaling/v2beta2

kind: HorizontalPodAutoscaler

metadata:

name: nginx-hpa

spec:

scaleTargetRef:

apiVersion: apps/v1

kind: Deployment

name: nginx

minReplicas: 3

maxReplicas: 10

metrics:

\- type: Resource

resource:

name: cpu

target:

type: Utilization

averageUtilization: 50

Here CPU averaging over 50% triggers adding pod instances up to a maximum of 10. The cluster adjusts to maintain utilization targets.

Observability tooling helps visually track infrastructure impact from autoscaling next.

[Exploring monitoring](#contents.xhtml#sc2_195a)

Observability platforms play a pivotal role in the realm of Kubernetes by offering comprehensive insights into various facets of cluster management and application performance. These platforms serve as essential tools for debugging issues, tracking environments, and ensuring the robustness of containerized applications within dynamic Kubernetes ecosystems. Prominent options in the observability landscape include Prometheus, Grafana, the Elastic Stack, Datadog, and more, each specializing in different aspects of monitoring and analytics. Integration with these platforms allows for the digestion of metrics and activity data, providing a consolidated view of the cluster's health and performance.

Dashboards, a key feature in observability platforms, enable the visualization of critical information. By breaking down resource usage, application performance, and other metrics, these dashboards offer actionable insights that aid in proactive management and troubleshooting. Tagging metadata, especially through pod labels, facilitates a granular breakdown of usage and status based on workload, namespace, node, and other criteria, moving beyond opaque cluster-level aggregation to enhance precision in analysis.

Kubernetes supports the native exposure of pod metrics through the adoption of the stats endpoint standard. This standardized approach enables monitoring systems to scrape detailed container telemetry encompassing networking, CPU, memory, and more. Rich metrics and logging, obtained through these observability practices, contribute to heightened awareness, allowing for informed decision-making in managing scale, optimizing performance, and ensuring the reliability of containerized applications within the dynamic and ever-evolving Kubernetes environment.

[Conclusion](#contents.xhtml#sc2_196a)

In this section, we explored an extensive set of technologies for deploying sample applications on EKS to demonstrate capabilities from stand-alone pods through robust, production-grade platforms leveraging Ingress, service mesh, autoscaling and monitoring. Kubernetes provides declarative APIs and resource model abstractions simplifying infrastructure management necessary for hosting applications from compute provisioning to storage allocation through networking.

Helm streamlines packaging all components together in versioned bundles enabling reproducible installations. Mature open source and managed add-ons for monitoring, security, routing take advantage of native integration while simplifying operations. With Amazon EKS providing auto scaled control planes combined with mature open source tools coming together under Kubernetes standards, organizations benefit from integrated platforms simplifying running applications reliably in production without extensive infrastructure expertise.

[Questions](#contents.xhtml#sc2_197a)

1.  What Kubernetes primitive allows scaling pod replicas behind a common endpoint?
    
2.  What resource observes external traffic and routes requests to internal cluster backends?
    
3.  What tool simplifies deploying applications through packaging Kubernetes manifests?
    
4.  What provides isolation between application environments on a shared EKS cluster?
    
5.  Can we run stateful databases like MongoDB on EKS using persistent volumes? 
    

[Exercises](#contents.xhtml#sc2_198a)

1.  Create a new namespace and deploy the Kubernetes Guestbook application segmented from other environments.
2.  Configure API gateway rules for the Guestbook frontend to restrict access to authenticated users.
3.  Instrument the Guestbook backend with a service mesh like Istio enabling failure recovery between pods.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 10Managing Stateful Apps on AWS Elastic Kubernetes Service Clusters](#contents.xhtml#ch10a)

[Introduction](#contents.xhtml#sc2_199a)

Deploying and managing stateful applications, such as databases or cache stores, on Kubernetes introduces complexities related to data persistence, high availability, and storage management. Amazon Elastic Kubernetes Service (Amazon EKS) addresses these challenges by offering mature integrations with AWS storage services and supporting open-source methodologies. This strategic integration streamlines the deployment and management of stateful workloads within the Amazon EKS environment.

The capabilities provided by Amazon EKS for managing stateful applications include a robust set of features such as persistent volumes, provisioning flows, snapshots, tools, and best practices. Persistent volumes offer a mechanism for preserving data beyond the lifecycle of individual containers, ensuring data persistence and availability during pod rescheduling or failures. Provisioning flows encompass the dynamic allocation of storage resources, optimizing scalability and resource utilization.

Snapshots, another critical aspect, allow for point-in-time copies of data, facilitating data protection and recovery. The availability of tools tailored for stateful workloads enhances operational efficiency, while adhering to best practices ensures the reliability and resilience of stateful applications on EKS.

This chapter delves into the intricacies of these capabilities, exploring how persistent volumes, provisioning flows, snapshots, and tools can be effectively harnessed to operate stateful applications on Amazon EKS. By leveraging these features, users can confidently navigate the challenges associated with data management, availability, and storage in the context of stateful workloads, ultimately fostering a robust and efficient operational environment within the Kubernetes ecosystem.

[Structure](#contents.xhtml#sc2_200a)

This comprehensive chapter is organized into the following sections:

*   StatefulSets
*   PersistentVolumes
*   Snapshots
*   StorageClasses
*   Volume scaling
*   Higher application availability
*   Data lifecycle management
*   Storage topologies
*   Choosing storage services
*   CSI drivers
*   Mobility
*   Security
*   Monitoring

[Objectives](#contents.xhtml#sc2_201a)

Upon completion of this material, you will acquire a thorough understanding of key concepts in Kubernetes storage management. You will grasp the intricacies of StatefulSet and PersistentVolume (PV) primitives, empowering you to efficiently manage pods and attach storage. Additionally, the knowledge gained will enable you to create Volume Snapshots, offering valuable point-in-time copies.

The chapter provides insights into leveraging StorageClasses for dynamic provisioning, facilitating the scalability of PV capacity. The material also covers the deployment of highly available configurations, addressing the crucial aspect of application availability.

Furthermore, you will learn strategies for archiving old data while retaining access and understand the benefits of structured multi-layered storage pools. The chapter also offers a comparative analysis of Elastic Block Store (EBS), Elastic File System (EFS), and Simple Storage Service (S3) for stateful applications, allowing you to make informed decisions based on your specific requirements.

Moreover, it introduces the capabilities of open-source tools like Stash and Ark, providing valuable insights into managing storage efficiently. Then, it expands your knowledge to include the movement of storage between regions, ensuring flexibility in your deployment strategies.

Security considerations are woven into the fabric of this section, encompassing encryption and Role-Based Access Control (RBAC) to safeguard the state of your applications. Lastly, you will be equipped to monitor data stores in Kubernetes effectively, enhancing your observability and proactive management of storage resources.

[StatefulSets](#contents.xhtml#sc2_202a)

StatefulSets in Kubernetes represent a specialized set of workload API objects tailored to meet the unique requirements of stateful applications, including databases, queues, and caches. These applications demand specific characteristics such as stable hostnames, persistent storage volumes, graceful deployment and scaling procedures, and orderly shutdowns. Unlike deployments, which manage largely ephemeral and interchangeable replica POD instances, StatefulSets go a step further by preserving the identity of each component throughout restarts and lifetimes. This continuity ensures that critical state information, like stored data, persists reliably across the lifecycle of the application.

The significance of StatefulSets lies in their ability to provide a level of determinism and predictability essential for stateful applications. The stable hostnames assigned by StatefulSets facilitate consistent and recognizable communication patterns, crucial for applications requiring identity awareness. The incorporation of persistent storage volumes ensures that data persists beyond the transient nature of individual pods, addressing the specific needs of databases and other stateful workloads.

Moreover, StatefulSets support graceful deployment and scaling operations, allowing for controlled adjustments without sacrificing the integrity of the application. Additionally, orderly shutdowns ensure that stateful applications can gracefully conclude their operations, minimizing the risk of data loss or corruption. In essence, StatefulSets stand as a foundational component within Kubernetes, providing a reliable framework for managing the intricacies of stateful applications in a containerized environment. For example, a 3 replicated Redis cluster is modeled under a StatefulSet:

apiVersion: apps/v1

kind: StatefulSet

metadata:

name: redis-ss

spec:

serviceName: "redis"

replicas: 3

selector:

matchLabels:

 app: redis

template:

metadata:

labels:

app: redis

spec:

containers:

\- name: redis

image: redis

ports:

\- containerPort: 6379

name: client

volumeMounts:

\- name: redis-data

mountPath: /data

volumeClaimTemplates:

\- metadata:

name: redis-data

spec:

accessModes: \[ "ReadWriteOnce" \]

storageClassName: "gp2"

resources:

requests:

storage: 5Gi

The provided YAML details the configuration of a StatefulSet in Kubernetes, specifically for a Redis cluster with three replicas. The apiVersion and kind denote the Kubernetes API version and resource type (StatefulSet in apps/v1). In the metadata section, the StatefulSet is named "redis-ss." The spec outlines the StatefulSet specifications, including the declaration of the associated service named "redis" and the desired number of replicas set to 3. The selector is defined to match pods using the label app: redis. The template describes the pod template with labels set to app: redis and specifications for the Redis container, exposing port 6379 and mounting a volume at /data for persistent storage.

The volumeClaimTemplates section specifies templates for PersistentVolumeClaims (PVCs) associated with each pod, including naming the PVC as "redis-data" and specifying access modes, storage class ("gp2"), and storage requests (5Gi). In summary, this YAML configures a StatefulSet for a Redis cluster, ensuring three replicas, each with persistent storage through PVCs, and exposes the service named "redis" for client connections.

In essence, this YAML sets up a StatefulSet for a Redis cluster with predictable naming, ordered scaling, and persistent volumes, providing the necessary capabilities for running stateful systems reliably within a Kubernetes environment. Each replica is associated with its own persistent storage, and the entire configuration is designed to ensure predictability and stability in managing stateful applications like Redis. We next look specifically at integrating storage.

[PersistentVolumes](#contents.xhtml#sc2_203a)

In the realm of containerized applications, the necessity for external attachable storage becomes apparent, especially for data that must persist beyond container restarts or deletions. This is particularly crucial for applications such as databases, message queues, filesystems containing user content, or caches buffering expensive computations. Kubernetes addresses this need through PVs, a mechanism that seamlessly integrates external disk resources into the lifecycles of containers. This integration extends across major public clouds and on-premises storage systems, providing a unified and abstracted approach.

PVs act as a bridge between containerized applications and external storage resources, offering a standardized way to provision storage capacity. PVCs then come into play, serving as declarations made by applications or users to request a specific amount of storage. These PVCs act as the link between the application pods and the underlying PVs, ensuring a dynamic and scalable allocation of storage resources in a Kubernetes environment.

The integration of Kubernetes PVs into containerized workflows facilitates the seamless management of external storage resources, enhancing the reliability and resilience of applications that rely on persistent data. This approach not only streamlines storage provisioning but also contributes to the flexibility and portability of containerized applications across diverse cloud and on-premises environments. For example, a MySQL StatefulSet can request a 10 GB PV, as shown:

apiVersion: v1

kind: PersistentVolumeClaim

metadata:

name: mysql-pv-claim

spec:

accessModes:

\- ReadWriteOnce

resources:

requests:

storage: 10Gi

A POD then mounts this PVC, exposing the PV backing store, as shown in the following YAML snippet:

volumes:

\- name: mysql-data

persistentVolumeClaim:

claimName: mysql-pv-claim

To summarize, in this Kubernetes configuration snippet, a MySQL StatefulSet is illustrated requesting a PV of 10 gigabytes. The first block, a PVC, defines the desired characteristics of the storage, specifying access modes and requesting a storage capacity of 10Gi. This PVC serves as a declarative request for storage by the MySQL StatefulSet.

Subsequently, within the pod definition, a volume named mysql-data is created, explicitly tied to the previously defined PVC ("mysql-pv-claim"). This establishes a direct link between the application (MySQL) and the underlying persistent storage, providing a reliable mechanism for data persistence.

By abstracting the storage management through Kubernetes APIs, this configuration ensures that MySQL has durable capacity without being burdened by infrastructure intricacies. The Kubernetes abstraction enables seamless portability across various environments, as the underlying details of the storage are encapsulated within the defined storage class and the PVC.

Furthermore, Kubernetes supports multiple PV types, allowing for the implementation of storage tiering through different storage classes. This flexibility in storage provisioning empowers users to align storage resources with specific application requirements, optimizing performance and resource utilization. Overall, this configuration showcases how Kubernetes efficiently manages storage for stateful applications, promoting durability, abstraction, and adaptability across diverse infrastructure environments. Next, we explore creating PVC snapshots for data protection needs.

[Snapshots](#contents.xhtml#sc2_204a)

In the Kubernetes ecosystem, PVs play a crucial role by providing block storage volumes to pods, ensuring persistent and durable storage for applications. Complementing this functionality, VolumeSnapshots introduce the capability to create point-in-time copies of PVC data. These snapshots serve as valuable tools for backup systems, facilitating the secure storage of data into object stores such as S3. The VolumeSnapshot object represents a point-in-time copy of a PVC. It specifies the source PVC and the desired snapshot class. The VolumeSnapshotClass defines the attributes and policies for snapshot creation, such as the CSI driver to use and the parameters for the snapshot. The VolumeSnapshotContent object stores the actual snapshot data, acting as a binding between the VolumeSnapshot and the underlying storage system.

The integration of VolumeSnapshots allows for the creation of application-consistent images without requiring freezes or interruptions in the normal operation of the application. This is particularly significant for ensuring the integrity and recoverability of critical data, offering a mechanism to capture the state of a PVC at a specific moment in time.

By leveraging VolumeSnapshots, Kubernetes users gain a powerful tool for implementing robust data protection strategies. Backup systems can utilize these snapshots to create consistent backups of PVC data, storing them in object stores for added resilience and accessibility. This approach enhances the overall reliability and recoverability of applications, addressing the imperative need for comprehensive data management within dynamic containerized environments. For example, a database PVC tagged app=mysql can snapshot on a schedule, as shown:

apiVersion: snapshot.storage.k8s.io/v1

kind: VolumeSnapshot

metadata:

name: mysql-volume-snap

spec:

volumeSnapshotClassName: aws-ebs

source:

persistentVolumeClaimName: mysql-pv-claim

In this Kubernetes configuration snippet, a scheduled snapshot of a database's PVC is demonstrated, exemplifying a MySQL application with the PVC tagged as app=mysql. The VolumeSnapshot API is employed to define the characteristics of the snapshot, specifying metadata such as its name (mysql-volume-snap) and the VolumeSnapshotClass to be utilized (in this case, aws-ebs). The source of the snapshot is explicitly linked to the PVC named mysql-pv-claim, ensuring that the snapshot captures the specific data associated with the MySQL application.

By leveraging the specified VolumeSnapshotClass, which is configured to utilize underlying cloud capabilities (here, AWS EBS), the Kubernetes environment orchestrates the creation of fast and application-consistent snapshots. These snapshots are noteworthy for being stored externally in object form, departing from the conventional approach of block devices directly attached to nodes. This shift ensures that the snapshots are not only efficiently created but also become portable, storable, and restorable artifacts.

The integration of VolumeSnapshots into Kubernetes aligns with the platform's abstraction capabilities, allowing users to manage snapshots as part of the broader Kubernetes ecosystem. This approach not only enhances the resilience and accessibility of application data but also underscores Kubernetes' versatility in incorporating cloud-native features for efficient and effective data management within containerized environments. We next look at simplifying dynamic provisioning using StorageClasses.

[StorageClasses](#contents.xhtml#sc2_205a)

The manual creation of PVs and their alignment with PVCs can introduce management complexities, necessitating careful configuration of capacity and management of the attach/detach lifecycles. To streamline and simplify this process, Kubernetes introduces the concept of StorageClasses. StorageClasses act as abstractions that automatically handle the provisioning of compatible storage pools, dynamically allocating capacity based on requests placed by PVCs.

By leveraging StorageClasses, users can eliminate the need for manual intervention in configuring individual PVs, mitigating potential errors and reducing management overhead. The dynamic provisioning facilitated by StorageClasses utilizes volume plugins compatible with the underlying storage infrastructure. This automation ensures that when PVCs specify their storage requirements, the appropriate StorageClass automatically provisions the required capacity without the need for pre-allocation.

This abstraction layer not only simplifies the process of consuming storage resources but also enhances the agility and efficiency of storage management within Kubernetes. The automation introduced by StorageClasses aligns with the platform's goal of abstracting complex infrastructure details, allowing users to focus on the high-level specifications of their storage needs while Kubernetes handles the underlying provisioning intricacies. For example, a StorageClass targeting EBS gp3 volumes:

apiVersion: storage.k8s.io/v1

kind: StorageClass

metadata:

name: ebs-sc

provisioner: ebs.csi.aws.com

parameters:

type: gp3

encrypted: 'true'

Workloads request from this class, as shown in the following YAML snippet:

kind: PersistentVolumeClaim

spec:

storageClassName: ebs-sc

resources:

requests:

storage: 5Gi

In this Kubernetes configuration snippet, a StorageClass tailored for Amazon EBS gp3 volumes is defined, named ebs-sc. The StorageClass is configured to utilize the EBS Container Storage Interface (CSI) provisioner with specific parameters, specifying the volume type as gp3 and enabling encryption.

Subsequently, a workload can request storage resources from this StorageClass by creating a PVC. The PVC specifies the desired storage class as ebs-sc and requests a storage capacity of 5 gigabytes.

The EBS plugin, integrated with the specified StorageClass, handles the dynamic provisioning of PVs that match the requested size in the PVC. This process is seamlessly managed through native Kubernetes resource flows, automating the deployment of storage resources and alleviating the need for extensive upfront capacity planning. This configuration exemplifies how Kubernetes abstracts the complexities of storage provisioning, allowing users to define their storage requirements at a high level while the underlying infrastructure details are efficiently managed by the platform. We next explore expanding allocated capacity when limits constrain workload growth.

[Volume scaling](#contents.xhtml#sc2_206a)

Kubernetes addresses the dynamic nature of storage requirements throughout the lifecycle of applications by providing the capability to inspect PVC consumption. This feature allows administrators to monitor the utilization of storage resources by PVCs, gaining insights into evolving storage needs.

Importantly, Kubernetes offers a seamless mechanism for expanding the capacity of the backing volumes associated with PVCs without requiring any downtime or changes to the running workloads. This flexibility enables organizations to adapt to changing storage demands without disrupting ongoing operations. Administrators can proactively adjust storage capacities, ensuring that applications have the necessary resources to accommodate growing data or evolving requirements.

The ability to dynamically expand storage capacity aligns with Kubernetes' commitment to facilitating scalable and resilient containerized environments. It empowers organizations to efficiently manage storage resources, responding in real-time to the changing needs of applications and ensuring a smooth and uninterrupted operation throughout their lifetimes. For example, in this Kubernetes configuration example, when faced with approaching limits on a 10 GB MySQL PVC, administrators can effortlessly scale its capacity by modifying only the PVC object. The adjustment is made by altering the storage request within the PVC configuration, as illustrated by the snippet:

apiVersion: v1

kind: PersistentVolumeClaim

metadata:

name: mysql-pv-claim

spec:

accessModes:

\- ReadWriteOnce

resources:

requests:

storage: 20Gi \# Increased capacity

This singular modification triggers a seamless expansion of the underlying PV filesystem, facilitated through provider integration. Crucially, this operation occurs without the need to restart the MySQL container or make any additional modifications beyond this incremental expansion instruction. The MySQL container automatically gains double the original capacity, demonstrating Kubernetes' capability to dynamically and efficiently adjust storage resources in response to changing application requirements, ensuring continuous availability and scalability.

[Higher application availability](#contents.xhtml#sc2_207a)

In pursuit of heightened application availability, distributed topologies in Kubernetes strategically deploy across fault domains. Leveraging Kubernetes namespaces with cloud provider awareness, these deployments intelligently spread StatefulSet instances across Availability Zones (AZs). This intelligent distribution minimizes correlated failure risks arising from localized outages within a specific zone.

By incorporating cloud provider awareness, Kubernetes enhances the resiliency of StatefulSet deployments by actively considering the underlying infrastructure's fault domain structure. This approach ensures that instances of stateful applications are strategically placed across distinct AZs, thereby mitigating the impact of potential failures within a single zone.

The inherent ability of Kubernetes to understand the cloud provider's infrastructure topology enables organizations to design and implement highly available architectures. This ensures that even in the face of localized outages, applications continue to operate seamlessly, providing a robust foundation for critical workloads with minimized downtime and improved fault tolerance. StatefulSet pods specify zoning. In this Kubernetes configuration snippet, StatefulSet pods are explicitly configured to adhere to zoning preferences for enhanced resiliency. The specification includes a pod AntiAffinity rule under affinity settings, which prioritizes the scheduling of pods to distinct zones, as shown:

spec:

selector:

matchLabels:

app: mysql

replicas: 3

template:

metadata:

labels:

app: mysql

spec:

affinity:

podAntiAffinity:

preferredDuringSchedulingIgnoredDuringExecution:

\- weight: 100

podAffinityTerm:

labelSelector:

matchExpressions:

\- key: app

operator: In

values:

\- mysql

topologyKey: failure-domain.beta.kubernetes.io/zone

This configuration ensures that each instance of MySQL is scheduled to run on worker nodes situated in separate zones within the cluster. The utilization of pod AntiAffinity in conjunction with multi-Availability Zone (AZ) storage redundancy strengthens the overall resilience of the deployment. By distributing instances across different failure domains, such as zones, organizations can significantly reduce the risk of correlated failures and enhance the robustness of their applications, aligning with best practices for achieving high availability in Kubernetes environments. Kubernetes' capability to monitor PVC consumption in real-time allows administrators to anticipate storage needs and make proactive adjustments before they impact application performance. For rarely accessed data, archival storage presents cost savings next.

[Data lifecycle management](#contents.xhtml#sc2_208a)

In the dynamic landscape of application data, its access patterns naturally transition through stages of hot, warm, and cold over time. Kubernetes storage integrations provide a powerful solution to accommodate these evolving patterns by facilitating the transparent movement of contents across different storage tiers. This intelligent approach aligns data storage with usage patterns and optimizes costs by leveraging storage classes tailored to specific needs.

A prime example of this strategy involves the implementation of a three-tier hierarchy:

*   Hot tier: This tier is designed for high-performance primary storage, utilizing SSD disks to cater to frequent and critical data access scenarios.
*   Warm tier: To address less frequent bulk access patterns, the warm tier utilizes HDD disks, striking a balance between performance and cost-efficiency.
*   Cold tier: Serving archival and backup needs, the cold tier employs storage solutions such as S3 or Glacier, providing a cost-effective option for data with minimal access requirements.

Enhancing this tiered storage model, Kubernetes tools like Kasten K10 seamlessly integrate Intelligent Lifecycle Management (ILM) policies. These policies empower organizations to set specific data lifespan thresholds, triggering auto-migration of data to lower-cost storage tiers based on predetermined criteria. For instance, data that has not been accessed for 30 days may automatically transition to the warm tier, while data inactive for 90 days may be moved to the cold tier. This adaptive approach allows organizations to retain extensive data accumulated over the years while optimizing costs by dynamically adjusting the data access temperature.

Crucially, this automated tiering process occurs without disruption to ongoing applications, as they continue to run without realizing the transparent moves in the background. Moving forward, the discussion will delve into structuring storage into higher-level abstractions, further refining the management and optimization of data within Kubernetes environments. This abstraction layer provides a more streamlined and efficient way to manage storage resources at scale, offering increased flexibility and adaptability to the evolving needs of applications. CSI drivers facilitate the implementation of tiered storage by enabling Kubernetes to interact with various storage systems and automate data migration. For instance, a media company might use the hot tier for current video editing projects, the warm tier for completed projects awaiting review, and the cold tier for archived footage.

[Storage topologies](#contents.xhtml#sc2_209a)

In Kubernetes, the traditional approach focuses on individual resource attachments between PVs PVCs. However, to address the diverse needs of different application categories, Kubernetes allows for the creation of higher-order relationships between these primitives. This involves assembling structured pools of storage capacity segmented by various factors, including performance, cost, data protection, and access control.

For instance, in the context of a multi-tier web application, the storage structure may be organized into distinct categories as follows:

*   Application storage: Utilizing SSD volumes to meet low-latency requirements for critical application components.
*   User storage: Employing HDD network-attached capacity to serve as storage for user-related data.
*   Archive storage: Leveraging S3 for storing logs and audit data, providing a cost-effective solution for archival purposes.

Rather than focusing on individual PV/PVC attachments, this approach encourages reasoning about topology categorization when modeling stateful applications. The management paradigm shifts from an instance-focused approach to a higher-level policy-based framework aligned with specific business needs.

This strategy allows for a more holistic and efficient management of storage resources, catering to the nuanced requirements of different application categories. In the subsequent exploration, we delve into the major storage services available for stateful applications on AWS, providing insights into how these services can be leveraged to enhance the storage capabilities of Kubernetes environments.

[Choosing storage services](#contents.xhtml#sc2_210a)

AWS offers a comprehensive suite of storage services, encompassing robust block, file, and object storage, seamlessly integrating with Kubernetes and empowering stateful applications on Amazon EKS to leverage the most suitable storage form factors.

[EBS volumes](#contents.xhtml#sc3_211a)

Amazon EBS provides SSD performant block storage directly attached to EC2 instances. Offering persistence, snapshots, encryption, tiering, scalable capacity, and IOPS, EBS is a versatile solution for various storage needs.

EBS volumes are highly available and reliable, with built-in replication across multiple servers in the same Availability Zone. They support advanced storage features like provisioned IOPS, multi-attach for shared access, and elastic volumes for on-demand capacity modifications. EBS volumes can be used as the primary storage for databases, enterprise applications, containerized workloads, and more.

[EFS filesystems](#contents.xhtml#sc3_212a)

EFS is a fully managed NFS share facilitating parallel multi-pod access with high throughput and IOPS. It dynamically scales on-demand and operates across AZs, making it ideal for scenarios requiring shared file access.

EFS filesystems are designed to provide massively parallel shared access to thousands of Amazon EC2 instances, enabling a wide range of use cases such as content management, web serving, data analytics, and media processing. They support strong data consistency and file locking, making them suitable for applications that require a shared file system. EFS filesystems can automatically grow and shrink as files are added or removed, eliminating the need for manual provisioning and reducing operational overhead.

[S3 object storage](#contents.xhtml#sc3_213a)

S3 is a durable and cost-effective solution for storing large blobs, backups, archives, and more. Equipped with cryptographic, versioning, and replication features, S3 is well-suited for managing object-based data.

S3 provides virtually unlimited scalability, allowing you to store and retrieve any amount of data from anywhere on the web. It offers robust security features like server-side encryption, access control lists, and bucket policies. With its high durability and availability, S3 is a reliable choice for storing and distributing static content, backups, logs, and other data types across various applications and services.

Aligning the topology structure with the appropriate AWS storage services is crucial to strike a balance between performance, resilience, and cost. For instance:

*   Hosting a hot database on the EBS GP3 SSD tier for optimized performance.
*   Utilizing EFS systems for shared user file access, ensuring parallel multi-pod availability.
*   Leveraging S3 for blob object archives and backups, capitalizing on its durability and cost-effectiveness.

This strategic segmentation of usage patterns into ideal services enhances the overall efficiency of storage solutions. In the upcoming exploration, we delve into open-source tools that play a pivotal role in augmenting data protection measures, further fortifying the storage capabilities of Kubernetes environments on AWS.

[CSI drivers](#contents.xhtml#sc2_214a)

CSI is a standardized interface for container orchestration systems like Kubernetes to interact with different storage providers seamlessly. CSI decouples storage orchestration from container orchestration, allowing storage vendors to develop and maintain their own CSI drivers. These drivers enable Kubernetes to dynamically provision, attach, and mount storage volumes onto pods.

Amazon Web Services (AWS) offers three popular CSI drivers for different storage services: Amazon EBS, Amazon EFS, and Amazon S3.

The EBS CSI driver facilitates the dynamic provisioning of EBS volumes, allowing Kubernetes workloads to request and utilize block storage as per their requirements. This ensures efficient resource utilization and enables scalable storage solutions for applications running in Kubernetes clusters.

The EFS CSI driver extends similar capabilities to Amazon EFS, a fully managed file storage service. It enables dynamic provisioning of file systems and facilitates seamless integration with Kubernetes, enabling stateful applications to utilize shared file storage in a scalable and efficient manner.

For object storage, the S3 CSI driver connects Kubernetes clusters with Amazon S3, a highly durable and scalable storage service. This driver enables pods to interact with S3 buckets directly, providing a flexible and cost-effective solution for storing and retrieving data in a cloud-native environment.

Each of these CSI drivers follows the CSI specification, ensuring a consistent interface for storage provisioning across various cloud providers and storage solutions. This standardization simplifies the deployment and management of storage resources in Kubernetes, promoting interoperability and reducing vendor lock-in. CSI drivers play a crucial role in enhancing the flexibility, scalability, and efficiency of storage management within containerized environments, making them an integral part of modern cloud-native architectures.

[Mobility](#contents.xhtml#sc2_215a)

Storage classes in Kubernetes play a pivotal role by abstracting underlying storage providers, ensuring portability across different environments, including various cloud vendors and on-premises solutions. This abstraction allows applications to seamlessly move across clusters, leveraging equivalent capacity and features.

Replication tools, such as Stash, offer the ability to mirror application data, particularly from Container Storage Interface (DBMS) stores, into object buckets. This mirrored data can then be restored onto various destinations, facilitating global mobility without succumbing to vendor lock-in. This portability ensures that applications remain resilient and adaptable, mitigating the risks of fragility associated with capacity discontinuities during migrations across regions or between different providers.

The integration of common Kubernetes primitives further contributes to the consistency of infrastructure layering. This consistency spans the development and production phases, supporting the fluidity of Continuous Integration/Continuous Deployment (CI/CD) processes. Importantly, this is achieved without compromising the availability requirements inherent in stateful systems, thereby fostering a seamless and reliable transition from development to production environments.

[Security](#contents.xhtml#sc2_216a)

Efficiently isolating storage resources within a Kubernetes environment is paramount for safeguarding access. Kubernetes Role-Based Access Control (RBAC) is instrumental in this endeavor, as it restricts components to the least privilege permissions necessary for their functionalities. By implementing RBAC, organizations can ensure that storage-related operations are limited to authorized entities, reducing the risk of unauthorized access and potential security breaches.

Encryption emerges as another crucial layer of defense, particularly for safeguarding sensitive static datasets and transport payloads. This not only enhances the security posture of the storage infrastructure but also ensures compliance with regulatory standards and corporate policies throughout the entire data lifecycle.

The integration of Secure Key Management Systems (KMS), such as AWS KMS, adds an extra layer of security. These systems enable volume and snapshot encryption while leveraging hardware-backed protection for keys. This ensures that even in the event of compromised worker nodes, the encrypted storage contents remain secure and inaccessible.

In addition to RBAC, encryption, and KMS, a robust security strategy involves audited access policies. These policies combine Identity and Access Management (IAM) session controls with embedded operating system protections, providing a defense-in-depth approach. This holistic security framework ensures that storage resources are consistently protected with the principles of least privilege, encryption, and comprehensive access audits. By integrating these security measures, organizations can bolster the resilience of their storage infrastructure and maintain the integrity of their data assets.

[Monitoring](#contents.xhtml#sc2_217a)

Gaining insightful metrics into storage utilization is critical for effective management of scaled deployments. Monitoring I/O pressure, latency, and capacity scheduling provides valuable data for making informed decisions. By setting threshold alerts and analyzing usage trends, organizations can strike a balance between optimizing performance and accommodating anticipated growth.

Time series metrics play a pivotal role in identifying potential bottlenecks across various layers of the storage infrastructure. Metrics such as disk fill rates, queue depths, and read/write latency offer a comprehensive view from the application layer down through virtualization to the physical media. This holistic approach allows for the early detection of developing issues, enabling preemptive resource scaling or restructuring of the topology to eliminate surprises related to capacity exhaustion. Diligent monitoring of these metrics is essential for maintaining the overall health of the storage environment.

Integrating storage metrics with popular monitoring tools such as Prometheus and Grafana enhances visibility and analytics. These tools enable the creation of visualizations that track key performance indicators (KPIs) related to storage. By leveraging these visualizations, organizations can ensure that the availability of storage resources never compromises the delivery of application value. Furthermore, optimal resource usage efficiency can be achieved through continuous monitoring and adjustment of storage configurations based on real-time insights. This approach not only enhances the performance of storage systems but also contributes to the overall reliability and effectiveness of the deployed applications.

[Conclusion](#contents.xhtml#sc2_218a)

Kubernetes offers robust abstractions that empower stateful applications to securely utilize external storage resources. The integrated lifecycle connections between runtime objects, such as StatefulSets and PersistentVolumes, dynamically link with automatic provisioning workflows facilitated by StorageClasses. This intricate process seamlessly taps into performant and resilient services like EBS, EFS, and S3, allowing for efficient storage management within the Kubernetes ecosystem.

The platform's mature integrations extend to essential features like encryption, access controls, incremental scaling, and snapshot capabilities. These integrations are orchestrated through Kubernetes APIs and Custom Resource Definitions (CRDs), streamlining infrastructure management. This approach liberates development teams from the complexities of storage administration, enabling them to concentrate on the applications and data, while Kubernetes handles the intricate details of storage provisioning, security, and maintenance. The result is a cohesive and efficient storage solution that aligns seamlessly with the needs of stateful applications within the Kubernetes environment.

[Questions](#contents.xhtml#sc2_219a)

1.  What primitive helps run stateful apps on Kubernetes?
2.  What creates point-in-time storage volume copies?
3.  What enables creating on-demand storage capacity automatically?
4.  Can we archive infrequently accessed data to S3 cheaply?

[Exercises](#contents.xhtml#sc2_220a)

1.  Deploy a replicated MySQL StatefulSet with EBS volumes.
2.  Scale up the MySQL PVCs to simulate storage expansion needs.
3.  Simulate MySQL pod failure and restart to validate data persists.

# [CHAPTER 11Scaling AWS Elastic Kubernetes Services Workloads](#contents.xhtml#ch11a)

[Introduction](#contents.xhtml#sc2_221a)

Scaling workloads is critical for EKS clusters to ensure applications have adequate resources to meet demand while optimizing cost and efficiency. This chapter provides an in-depth overview of key methods for scaling Kubernetes workloads on Amazon Elastic Kubernetes Service (EKS). We will explore horizontal scaling with the Horizontal Pod Autoscaler (HPA), vertical scaling with the Vertical Pod Autoscaler (VPA), and cluster scaling options like Cluster Autoscaler (CA), Karpenter, and KEDA. Each method is explained clearly with examples and configuration steps.

We begin with a history of scaling in Kubernetes and why it has become essential for container orchestration. We then outline the structure of the section covering each autoscaling method. The key objectives are to learn techniques to scale EKS, understand how each autoscaler functions and integrates, and gain practical experience configuring and tuning autoscaling.

[Structure](#contents.xhtml#sc2_222a)

In this chapter, we will cover the following topics:

*   History of Kubernetes scaling
*   Horizontal Pod Autoscaler
*   Vertical Pod Autoscaler
*   Cluster Autoscaler
*   Karpenter
*   Kubernetes Event-Driven Autoscaling

[Objectives](#contents.xhtml#sc2_223a)

There are three key objectives covered in this chapter. The first is to learn techniques to automatically scale EKS workloads to meet fluctuating demand by leveraging HPA, VPA, CA, Karpenter and KEDA. Each provides automated scaling capabilities that are critical for cloud-native applications.

The second objective is to understand the purpose and functionality of each autoscaling tool. We cover how HPA scales pods, VPA resources, CA nodes, and more. Grasping the fundamentals of each method and when to apply them is essential.

Finally, the third objective is to gain hands-on experience practically implementing autoscaling for EKS deployments. The chapter provides end-to-end configuration guidance, real-world examples, and exercises to apply these techniques firsthand.

[History of Kubernetes scaling](#contents.xhtml#sc2_224a)

Since its inception, Kubernetes has supported automated scaling capabilities as a core tenet of its architecture. The ability to dynamically scale workloads based on demand is what enables Kubernetes to provide workload portability and resource efficiency at scale. The HPA was one of the first native mechanisms for scaling in Kubernetes, introduced in 2016. HPA allows automatically increasing or decreasing pod replicas based on observed CPU and memory utilization, to meet real-time application demands. Over time, the HPA functionality has continued to expand, allowing scaling based on custom metrics from external monitoring pipelines like Prometheus. This brings more application-awareness to the scaling process. Additionally, the VPA emerged for scaling resource requests and limits vertically in tandem with application needs. VPA helps right-size pod resource allocations based on historical usage analysis.

On the infrastructure layer, node autoscaling tools like the CA enable automatically scaling node pools up or down to efficiently support dynamic pod allocation and maintain SLAs. CA integrates with HPA allowing pod demand to drive quick scale out events. Beyond native tools, the Kubernetes community has built an ecosystem of scalers like KEDA that link scale events to business metrics from diverse sources like queues, databases, APIs etc. KEDA introduces cross-platform event-driven scale capabilities based on custom metrics not found in HPA.

The ability to nimbly scale up and down at both the workload and infrastructure levels makes Kubernetes uniquely suited for running containerized, cloud native applications that see variable demand patterns. Legacy monolithic applications had to run on static hardware capacities that were over provisioned to the peak, wasting resources. But micro-services on Kubernetes can leverage runtime autoscaling to ensure resources match real-time needs, without sacrificing performance or availability, optimizing efficiency and costs tremendously while maintaining SLAs. This elasticity unlocks the potential of Kubernetes to run stateful and stateless variable workloads across ephemeral infrastructure, while maintaining quality of service through automated scaling.

[Horizontal Pod Autoscaler](#contents.xhtml#sc2_225a)

The HPA automatically scales the number of pod replicas based on observed CPU/memory metrics. HPA allows scaling pod counts out and in to meet fluctuating workload demands. We first cover HPA architecture and how the components interact to calculate scale decisions.

The HPA is an essential native resource in Kubernetes designed to dynamically adjust the number of pods within a deployment. It achieves this by continuously monitoring and responding to variations in CPU/memory utilization or other specified custom metrics. This intelligent scaling capability ensures that the deployment aligns seamlessly with the resource demands, optimizing overall operational efficiency.

To employ HPA effectively, the initial steps involve creating an Amazon EKS cluster and configuring node groups through the eksctl tool. Subsequently, deploying a representative application, such as a memcached-loader, is crucial to simulate varying loads. The HPA controller, equipped with insightful metrics, then takes charge of making informed scaling decisions, dynamically adjusting the pod replicas as needed.

This automated scaling process not only enhances system resilience but also promotes resource utilization efficiency. By leveraging the HPA in conjunction with EKS, organizations can confidently manage variable workloads, ensuring optimal performance and responsiveness in their Kubernetes environments. For example, let us deploy a busybox image:

kubectl run memcached-loader --image=busybox

kubectl expose deployment memcached-loader --port=11211

kubectl top pods # view metrics

Next, we create an HPA definition as a Kubernetes resource, as shown in the following code snippet. This scales the target deployment between 1-10 replicas when CPU exceeds 50% per pod.

apiVersion: autoscaling/v1

kind: HorizontalPodAutoscaler

metadata:

name: memcached-loader-hpa

spec:

 scaleTargetRef:

apiVersion: apps/v1

kind: Deployment

name: memcached-loader

minReplicas: 1

maxReplicas: 10

targetCPUUtilizationPercentage: 50

Apply this with the following lines:

kubectl apply -f memcached-hpa.yaml

kubectl get hpa # view current status

kubectl autoscale deployment memcached-loader --cpu-percent=50 --min=1 —max=10

Now, with the HPA in action, it dynamically scales the deployment by evaluating the CPU threshold, automatically adjusting the number of pods in response. This capability becomes especially valuable as we generate load intentionally to trigger scaling and validate the system's responsiveness. The HPA's ability to swiftly scale in and out ensures that applications maintain performance Service Level Agreements (SLAs) seamlessly, even when confronted with fluctuating workloads.

By employing HPA, organizations can confidently uphold performance standards without manual intervention, allowing for an agile and adaptive infrastructure. The automated scaling process not only streamlines operations but also guarantees that the system can handle varying demands efficiently. In essence, HPA empowers applications to meet and sustain performance SLAs, offering a resilient and self-regulating solution in the face of dynamic workloads.

[Vertical Pod Autoscaler](#contents.xhtml#sc2_226a)

The VPA emerges as a sophisticated Kubernetes resource, taking resource optimization to a granular level by automatically determining optimal CPU and memory requests and limits for pods. This is achieved through a meticulous analysis of historical usage patterns, enabling the system to right-size resource allocations dynamically rather than relying on static overprovisioning. Consequently, this not only optimizes workload density on nodes but also contributes to more efficient resource utilization. VPA adjustments can trigger pod restarts as resource limits and requests are modified, which might disrupt running applications. It's important to weigh this trade-off to ensure that the benefits of optimized resource usage outweigh the potential downtime or disruptions.

To showcase the prowess of VPA, we will initiate its deployment on an Amazon EKS cluster. This demonstration aims to underscore the vertical scaling capabilities of VPA in action. As VPA continuously evaluates and adjusts resource requirements based on historical data, it ensures that each pod receives precisely the resources it needs, promoting a balanced and efficient allocation strategy.

The significance of VPA becomes apparent as it mitigates the common pitfalls of overprovisioning by tailoring resource allocations to actual pod usage patterns. This not only enhances the overall performance of the system but also facilitates cost-effectiveness by eliminating unnecessary resource surplus. In essence, VPA is a crucial tool for achieving optimal resource utilization and maintaining an adaptive infrastructure that can dynamically respond to evolving workload demands.

First, ensure metrics-server is running in cluster to provide metrics for VPA, as shown:

helm install metrics-server stable/metrics-server

kubectl top pods # view metrics

Next, create a VPA definition indicating the target deployment and mode, as shown in the following code snippet. This controls container resources based on real-time utilization scanned every 60 seconds:

apiVersion: autoscaling.k8s.io/v1

kind: VerticalPodAutoscaler

metadata:

name: my-app-vpa

spec:

targetRef:

apiVersion: "apps/v1"

kind: Deployment

name: my-app

updatePolicy:

updateMode: "Auto"

resourcePolicy:

containerPolicies:

\- containerName: "\*"(20 lines)

minAllowed:

cpu: 5m

memory: 50Mi

maxAllowed:

cpu: 1

memory: 500Mi

Apply this VPA config to enable vertical scaling:

kubectl apply -f my-vpa.yaml

kubectl describe vpa my-app-vpa # view recommendations

With the VPA now in operation, it autonomously fine-tunes the CPU and memory resource limits and requests for the designated deployment. This dynamic adjustment is made in response to changing resource utilization, presenting a stark departure from the traditional approach of static overprovisioning based on peak needs. VPA's adaptive nature ensures that the target deployment receives precisely the resources it requires, avoiding unnecessary resource surplus.

As utilization patterns fluctuate, VPA continuously analyzes historical data to optimize resource allocations, aligning them with the actual demands of the application. This not only enhances the efficiency of resource utilization but also prevents potential performance bottlenecks caused by overprovisioning. The result is a more responsive and resource-efficient system that gracefully adapts to varying workloads, all while maintaining cost-effectiveness through judicious resource allocation. VPA stands as a testament to Kubernetes' ability to intelligently manage resources, providing a dynamic and efficient solution for modern deployment scenarios.

[Cluster Autoscaler](#contents.xhtml#sc2_227a)

The CA plays a pivotal role in maintaining optimal resource balance within an Amazon EKS environment. This intelligent Kubernetes resource automatically adjusts the size of EKS node groups to align with the resource demands of pods. The primary objective is to scale node capacity out when there are pending pods unable to schedule due to insufficient resources and scale in when nodes exhibit underutilization. The dynamic nature of CA ensures that the EKS cluster adapts seamlessly to varying workloads, optimizing resource allocation in real-time.

For the effective utilization of CA, it is imperative to configure EKS node groups as Auto Scaling Groups (ASGs). ASGs provide the underlying framework that allows CA to dynamically adjust the number of nodes in response to changing demands. By doing so, CA enables organizations to strike a balance between meeting application performance requirements and optimizing cost efficiency.

This approach not only ensures high availability by addressing resource shortages but also promotes cost-effectiveness by scaling in during periods of reduced demand. The synergy between CA and ASGs exemplifies Kubernetes' ability to automate and intelligently manage infrastructure, making it well-suited for dynamic and scalable containerized applications in the cloud. Overall, CA stands as a cornerstone in achieving an adaptive and efficient Kubernetes cluster within the EKS environment. First, annotate ASGs to enable discovery by CA, as shown:

kubectl annotate nodegroup my-nodegroup \\

cluster-autoscaler.kubernetes.io/scale-down-utilization-threshold=0.5

Next, deploy CA to EKS, as shown:

kubectl apply -f https://raw.githubusercontent.com/kubernetes/autoscaler/master/cluster-autoscaler/cloudprovider/aws/examples/cluster-autoscaler-autodiscover.yaml

Edit the configmap with node groups and AWS region, as shown:

kubectl edit configmap cluster-autoscaler-status -n kube-system

awsRegion: us-west-1

autoDiscovery:

clusterName: demo

Add auto-discovery tags to node group ASGs for CA to manage scaling, as shown:

Tags:

\- Key: k8s.io/cluster-autoscaler/enabled

Value: true

\- Key: k8s.io/cluster-autoscaler/demo

Value: owned

Now, CA will automatically scale EKS nodes based on pending pods and utilization metrics. When using CA alongside HPA and VPA, they work in tandem to optimize both pod-level resource allocation and node-level capacity. HPA and VPA manage pod scaling and resource requests, while CA adjusts the number of nodes to ensure there is enough capacity to meet the demands set by HPA and VPA, enabling a fully automated and responsive scaling strategy in Kubernetes.

[Karpenter](#contents.xhtml#sc2_228a)

Karpenter stands out as a powerful open-source node provisioner tailored for Amazon EKS clusters, offering a specialized solution for just-in-time scaling. This innovative tool addresses the challenge of rapid node provisioning by automatically launching nodes precisely when pods face scheduling difficulties due to resource constraints. Unlike traditional approaches, Karpenter alleviates the burden of directly managing and scaling EKS node groups, providing a seamless and efficient solution for dynamic workloads.

The core strength of Karpenter lies in its ability to intelligently analyze pod requirements and initiate node provisioning in real-time. By dynamically scaling the cluster to meet demand, Karpenter ensures that applications can seamlessly deploy and scale without manual intervention. The elimination of the need to manage node groups directly streamlines operations, making it easier for organizations to focus on building and deploying applications rather than managing infrastructure minutiae.

Karpenter's just-in-time scaling capabilities align resource availability with application demands, enhancing both efficiency and cost-effectiveness. This ensures that organizations can maintain optimal performance levels without unnecessary resource overhead. Moreover, Karpenter's open-source nature fosters collaboration and innovation within the Kubernetes community, contributing to the continual evolution of tools that simplify the orchestration and scaling of containerized applications in EKS clusters. In essence, Karpenter represents a forward-looking approach to node provisioning, bringing agility and automation to EKS deployments. To install Karpenter, refer to the following code snippet:

\# Set cluster requirements

eksctl utils update-cluster-endpoints --region=us-east-1 --name=my-cluster --append-subdomains=karpenter

\# Install the Helm chart

helm repo add karpenter https://charts.karpenter.sh

helm install karpenter karpenter/karpenter --create-namespace -n karpenter --set serviceAccount.annotations."eks\\.amazonaws\\.com/role-arn"=arn:aws:iam::123456789:role/KarpenterNodeRole

\# Label the nodegroup to opt-in

kubectl label nodegroup ng-1 karpenter.sh/discovery=true

This enables Karpenter node provisioning for the labeled node group. You can also configure provisioner rules and constraints, as shown:

cat <<EOF | kubectl apply -f -

apiVersion: karpenter.sh/v1alpha5

kind: Provisioner

metadata:

name: default

spec:

requirements:

\- key: "node.kubernetes.io/instance-type"

operator: In

values:

\- "t3.medium"

EOF

Now, Karpenter will automatically scale up and down nodes matching the provisioner rules as pod scheduling demands change in real-time.

[Kubernetes Event-Driven Autoscaling](#contents.xhtml#sc2_229a)

Kubernetes Event-Driven Autoscaling (KEDA) stands as a transformative tool, offering the ability to scale pods based on custom metrics derived from external sources such as Kafka, Redis, MySQL, SQS, and other diverse systems. This unique feature sets KEDA apart by providing event-driven scaling capabilities rooted in business metrics that may not be readily available in HPA. The significance of KEDA becomes evident as it enables Kubernetes clusters to dynamically adjust the number of pods based on real-time events from external sources. By extending beyond the traditional CPU and memory metrics, KEDA empowers organizations to scale their applications in response to specific business-oriented indicators. This allows for a more nuanced and finely tuned approach to scaling that aligns directly with the operational requirements of the applications.

KEDA's compatibility with a wide array of external sources broadens its applicability, making it versatile for diverse use cases. Whether it is reacting to changes in data flow, monitoring message queues, or responding to database activity, KEDA provides a holistic solution for event-driven scaling. The extensibility of KEDA enables organizations to tailor their scaling strategies based on the unique demands of their applications, fostering a more responsive and adaptable Kubernetes environment. The tool's capacity to interface with various external systems underscores its adaptability, allowing Kubernetes clusters to seamlessly integrate with different data sources and respond dynamically to changing conditions. This not only enhances the scalability of applications but also promotes a more efficient allocation of resources based on real-world business considerations.

In essence, KEDA emerges as a valuable addition to the Kubernetes ecosystem, bridging the gap between application scaling and diverse external metrics. Its ability to harness business-specific indicators for scaling decisions reflects a forward-thinking approach to Kubernetes orchestration, demonstrating the flexibility and responsiveness required to meet the evolving needs of modern containerized applications. To use KEDA, install the operator first with the following code snippet:

helm repo add kedacore https://kedacore.github.io/charts

helm repo update

helm install keda kedacore/keda --namespace keda --create-namespace

This installs the KEDA operator that will monitor scalers and scale deployments. Next, create a scaler with the trigger metric, as shown:

apiVersion: keda.sh/v1alpha1

kind: ScaledObject

metadata:

name: consumer-scalable

spec:

scaleTargetRef:

deploymentName: consumer

pollingInterval: 30

cooldownPeriod: 300

maxReplicaCount: 30

triggers:

\- type: redis

metadata:

host: redishost

port: 6379

listName: jobs-to-process

queueLength: “20"

This scales the 'consumer' deployment based on the Redis jobs-to-process list length as a custom metric for autoscaling. Finally, ensure the KEDA adapter is deployed, as shown:

kubectl apply -f https://github.com/kedacore/keda/releases/download/v2.0.0/keda-2.0.0-redis-queue-adapter.yaml

KEDA introduces a revolutionary approach by enabling the scaling of applications based on custom metrics derived from any source. This flexibility allows for the incorporation of application-specific metrics, extending beyond the traditional CPU and memory considerations. KEDA provides a seamless and tightly integrated solution for event-driven autoscaling, responding dynamically to changes in real-time metrics. The versatility of KEDA is evident in its ability to adapt to a wide range of data sources, ensuring that applications can scale based on precisely defined criteria. By accommodating app-specific metrics, KEDA aligns the scaling process with the unique requirements and performance characteristics of individual applications. This tailored approach enhances the precision and efficiency of autoscaling operations.

The tight integration offered by KEDA simplifies the implementation of event-driven autoscaling strategies, facilitating a more responsive and adaptive Kubernetes environment. This capability is particularly valuable for applications relying on diverse sources such as Kafka, Redis, MySQL, SQS, and others. KEDA's commitment to supporting various external systems underscores its commitment to versatility and interoperability in the ever-evolving landscape of Kubernetes orchestration.

[Conclusion](#contents.xhtml#sc2_230a)

The chapter covered core methods for scaling EKS workloads to meet demand automatically, including Horizontal Pod Autoscaler, Vertical Pod Autoscaler, Cluster Autoscaler, Karpenter, and KEDA. Each enables configuring autoscaling definitions and rules tailored to workload needs. The exploration began with HPA, focusing on its role in scaling pod replicas, followed by VPA, which addressed resource requests and limits for optimal efficiency. The discussion extended to CA, emphasizing its ability to scale nodes dynamically and Karpenter's innovative just-in-time scaling approach. KEDA took the spotlight for event-driven autoscaling, showcasing its versatility in accommodating custom metrics from diverse external sources.

Understanding the purpose of each autoscaler, individually and in synergy, became evident through examples like the configuration YAMLs provided. This knowledge empowers users to implement these autoscaling techniques effectively, adapting them to their specific application needs. With these EKS scaling techniques, users can construct truly elastic, cloud-scale applications capable of dynamically provisioning and descaling infrastructure based on real-time application metrics and signals. The provided exercises serve as practical tools for applying these scaling mechanisms directly, allowing users to witness autoscaling behaviors firsthand and gain confidence in managing dynamic workloads effectively within the EKS environment. Overall, this chapter provided a robust foundation for orchestrating scalable and responsive Kubernetes deployments in the cloud.

[Questions](#contents.xhtml#sc2_231a)

1.  What are the three major reasons to configure autoscaling for EKS applications?
2.  Differentiate between HPA versus VPA.
3.  Can Cluster Autoscaler scale node groups based on custom metrics like Kafka lag?
4.  What Kubernetes resource do you configure KEDA autoscaling rules within?
5.  True or False: Karpenter requires managing node groups to scale worker capacity.

[Exercises](#contents.xhtml#sc2_232a)

1.  Install HPA and configure autoscaling for a sample deployment using custom metrics. Observe scaling out/in over load.
2.  Set up Vertical Pod Autoscaler for a namespace and monitor the resource allocations over a period of days.
3.  Deploy Cluster Autoscaler and Karpenter and stress test node capacity to watch provisioning. Compare launch times.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 12Networking with AWS Elastic Kubernetes Services](#contents.xhtml#ch12a)

[Introduction](#contents.xhtml#sc2_233a)

Kubernetes defines a network model that ensures pods and services can communicate within and across cluster nodes. Realizing this connectivity is critical when operating production EKS clusters at scale across availability zones and regions. This chapter provides an in-depth overview of Kubernetes and EKS native networking abstractions, architecture, and options for configuring networking.

We cover fundamental pod and service networking constructs for enabling container-to-container and pod-to-pod connectivity. Building on core concepts, we explore Ingress controllers, load balancing options, and advanced networking patterns for production EKS across zones and regions.

Network security groups, access controls, multi-zone clustering and service mesh integration examples demonstrate production-grade networking topology and controls. You will gain hands-on experience configuring and testing key networking structures through provided sample manifests and connectivity validation steps.

[Structure](#contents.xhtml#sc2_234a)

This chapter covers the following topics:

*   Pod networking
*   Service networking 
*   Ingress controllers 
*   Load balancing 
*   Security group for pods 
*   Network policies 
*   Custom networking 
*   Prefix delegation 
*   Amazon VPC Lattice 

[Objectives](#contents.xhtml#sc2_235a)

By the end of this chapter, you will have acquired a comprehensive understanding of Kubernetes and the native networking abstractions specific to Amazon EKS, including insights into the underlying architecture. Throughout the learning process, you will explore the various configuration options available for establishing connectivity within EKS clusters, focusing on enabling seamless communication from pods to services. A significant emphasis is placed on providing hands-on experience as you navigate through practical exercises, configuring key networking structures such as Ingresses, load balancers, and network security groups. This practical approach ensures that you not only grasp theoretical concepts but also gain practical proficiency in implementing crucial networking components within the EKS environment.

Furthermore, the chapter facilitates a deep dive into Amazon VPC Lattice, prefix delegation, custom networking, security group for pods, and network policies, offering hands-on experience to reinforce your understanding of these essential networking features. By the end of this chapter, you will emerge with a robust skill set, equipped to navigate and configure critical networking elements within Amazon EKS, enhancing your overall proficiency in Kubernetes networking.

[Pod networking](#contents.xhtml#sc2_236a)

Pod networking in EKS allows pods running on EKS worker nodes to communicate with each other, the EKS control plane, and external networks. By default, the Amazon VPC CNI plugin is used for pod networking. The CNI handles assigning IP addresses from VPC subnets to pods and attaches elastic network interfaces (ENIs) to EKS nodes for this purpose. When a pod gets scheduled onto an EKS worker node, the CNI requests an IP address for the pod from the IP address management daemon (ipamd). The ipamd allocates a secondary IP address from the ENI attached to the node. This IP gets assigned to the pod, and routing is configured on the node to reach this address.

The pod will now have IP connectivity to other pods on the same node as well as pods on other nodes using VPC routing. The CNI integrates with VPC security groups and network ACLs to control pod traffic flows. For pod-to-pod communications, an ENI allows multiple secondary IP addresses to be assigned up to the elastic network interface limit. The Amazon VPC CNI plugin monitors pod events and manages IP address assignment and routing configuration lifecycle based on whether pods are created, terminated, or moved across nodes. The CNI runs as a DaemonSet across worker nodes. Prefix delegation can also be enabled so that ENIs get assigned an IP prefix from which pod IP addresses get allocated to maximize IP density.

EKS pod networking provides simple flat networking between Kubernetes pods without complex overlay or encapsulation requirements. This enables high performance pod-to-pod communications critical for microservices alongside efficient IP address allocation. Built-in integration into other AWS services makes it easy to apply security best practices. Advanced networking capabilities like service meshes and Ingress can be enabled via additive controllers and components on top of the native Amazon VPC CNI pod networking foundation. However, most EKS users need simple, reliable, and secure pod connectivity, which is achieved through the tightly integrated CNI plugin.

[Service networking](#contents.xhtml#sc2_237a)

Service networking in EKS enables network connectivity to Kubernetes services from within the cluster or externally from the internet. Services allow logical grouping of pods under a common endpoint, which clients can access without knowing the underlying pod IP assignments. The most basic Kubernetes service type is the ClusterIP which exposes the service via an internal virtual IP only reachable within the cluster from other pods and components. This gets translated by kube-proxy on worker nodes to underlying pod IPs using iptables rules. The AWS VPC CNI handles allocating secondary ENI IPs per pod.

Another service type is NodePort which opens a port on each worker node mapped to the service. External clients can connect to Node IP + NodePort to access the pods comprising the service. Load balancing happens locally via kube-proxy. Finally, LoadBalancer type services provision an external load balancer to route to nodes backing the service. This could be a classic ELB load balancer or NLB mapped to Node ports. Annotations can trigger integration with other AWS services like gateway load balancers.

On top of base service networking, Ingress controllers are commonly used to route external traffic to Kubernetes services by hostname, path or other rules. ALB Ingress controller is the default offering integrating AWS ALBs. Other add-ons build on services via sidecar pattern rather than proxying such as external DNS for auto DNS record management, service mesh for microservices security and reliability, and various log, metric, tracing integrations.

EKS users can start very simply with ClusterIP services for internal discovery and growth into NodePorts or LoadBalancer patterns for exposing to external users. Additional networking capabilities get incrementally added through managed add-ons and integrations without disrupting core Kubernetes service mechanics powered by the CNI. Security considerations are crucial when exposing services. Implementing network policies can help control the Ingress and egress traffic to services, ensuring only authorized access.

[Ingress controllers](#contents.xhtml#sc2_238a)

Ingress controllers are an important mechanism for routing external traffic to Kubernetes services in EKS. Since EKS runs in a VPC, Ingress management requires integration with AWS network components like load balancers or API gateway. The AWS Load Balancer Controller is the default Ingress for EKS. It deploys Elastic Load Balancers and target groups mapped to Kubernetes Ingress and service resources. The ALB Ingress translates Kubernetes Ingress APIs to AWS API calls to provision L7 capable application load balancers automatically. For instance, setting up an Ingress controller for a multi-tenant environment involves defining distinct Ingress rules for each tenant. This ensures isolated and secure traffic routing, allowing each tenant's application to be accessed independently while maintaining security and privacy.

This simplifies exposing HTTPS applications deployed on EKS to the outside world. Ingress rules define routing to backend services based on path or hostname allowing a common load balancer front-end to handle traffic for multiple distinct apps. ALB Ingress integrates with other AWS services like WAF, access logs, and advanced request routing. Authentication can be enabled via OIDC and logout redirection. Per route timeouts and retries optimize edge delivery.

The AWS App Mesh Ingress controller brings service mesh capabilities alongside application traffic routing via Envoy proxy integrations. Third party solutions exist for more advanced traffic management capabilities on top of Kubernetes Ingresses. Solutions like HashiCorp Consul or Traefik integrate Ingress Routes with service mesh and observability pipelines.

Having robust Ingress management is critical for EKS clusters to provide applications access over HTTPS, manage security, and secure communication via mTLS or OAuth for microservices use cases spanning multiple teams. The AWS ALB Ingress controller provides EKS users with a simple way to start defining application traffic Ingress management while allowing customizable upgrades to open source, AWS native, or third-party integrations at the edge router tier.

[Load balancing](#contents.xhtml#sc2_239a)

Load balancing is critical in EKS to route and distribute traffic across applications deployed on the cluster. At the most basic level, EKS leverages kube-proxy running on each node, which programs iptables rules to load balance across pods backing a Kubernetes Service. This handles internal cluster communication. For external traffic, LoadBalancer type Kubernetes Services integrate with Elastic Load Balancing to create classic, network, or application tier load balancers. These ELBs enable secure, highly scalable Ingress routing to EKS pods and nodes for public, internet facing applications. Integration is handled via Kubernetes service annotations, which trigger calls to AWS APIs to create and configure the ELBs.

Network Load Balancers function up to the transport layer, allowing ultra-high-performance layer 4 proxying to nodes. TCP or UDP traffic can be routed this way to any container or VM based application, avoiding the need to run proxies. NLBs also handle SSL offloading at scale. application load balancers provide advanced Layer 7 capabilities like HTTP routing, host and path-based delivery, health checks, and sticky sessions translating Kubernetes service intentions into configurable load balancing behavior.

Multiple load balancer types and integrations are available to unlock AWS native delivery, security, and availability capabilities at the edge layer, fulfilling core traffic routing and delivery needs for both North South and East West traffic in EKS clusters running across multiple AZs. Advanced service mesh solutions build on base load balancing resources in EKS but for most applications, leveraging ELBs via Kubernetes services provides an integrated solution to application traffic routing challenges.

[Security group for pods](#contents.xhtml#sc2_240a)

EKS offers integrated support for assigning VPC security groups to pods, similar to how you attach security groups to EC2 instances as virtual network firewalls. Enabling security groups at the pod level allows defining fine-grained networking rules focused on allowing only the necessary Ingress and egress connectivity based on the principle of least privilege.

Pod security groups enhance security by establishing network guardrails that lock down connectivity on a per-pod basis. This compartments pods into isolated networking segments, preventing lateral traversal in case an attacker compromises one element within the cluster. Without pod security groups, all pods across worker nodes exist on an open and flat network by default in EKS. By delineating pods into security groups aligned to specific functions or risk profiles, the blast radius from within is drastically reduced. Necessary communication between legitimate services can still occur through allowing explicit access between security groups rather than wide open pod-to-pod communication meshes.

These pod network security policies integrate directly with existing EC2 security groups constructs, enabling reuse of established controls. Pod security groups can declare egress rules to govern what remote connections are permissible as well as Ingress rules dictating allowed entry points. Fine-tuned pod security groups tuned to follow least privilege allow EKS administrators to find an appropriate balance between defense in-depth and operational overhead. Locking down connectivity across all pods to fully isolated groups may not make sense depending on use cases and risk tolerance. But combining pod security groups for sensitive workloads with cluster level Network Policies tailored based on environment is an EKS security best practice. The dual layers help restrict damage and blast radius in case of any pod or node exploitation at runtime. To configure pod security groups, you could try the following:

1.  Enable support in the EKS cluster if not already done, as shown:
    
    eksctl utils update-cluster-endpoints --name mycluster --region us-west-2 --vpc-private-access —wait
    
2.  Create a security group with required ingress/egress rules, as shown:
    
    aws ec2 create-security-group --group-name my-pod-sg --description "Security group for pods"
    
    aws ec2 authorize-security-group-ingress --group-name my-pod-sg --protocol tcp --port 8080 --cidr 0.0.0.0/0
    
3.  Annotate the pod spec to reference the security group, as shown:
    
    spec:
    
    securityGroups:
    
    \- name: my-pod-sg
    

This will attach the defined security group to the Kubernetes pod, enforcing network controls. Combine with network policies for defense-in-depth security.

[Network policies](#contents.xhtml#sc2_241a)

Network policies represent an important network security construct within Kubernetes clusters, enabling isolating and compartmentalizing communication between pods based on rules. Much like security groups function for infrastructure, network policies provide guardrails and control over traffic flow between pods. By default, within a Kubernetes cluster, all pods can contact one another across nodes, creating an open and flat networking mesh. This lack of boundaries makes lateral movement trivial in case an attacker gains access to a single pod for moving laterally. Hardening networking security is critical. One common issue user might face when implementing network policies is inadvertently blocking necessary traffic, which can cause application failures. To troubleshoot, start by checking the policy rules and ensure that the labels and selectors are correctly applied. Use kubectl describe and kubectl logs commands to get more information on policy enforcement and pod connectivity.

A network policy defines rules governing Ingress and egress connectivity between pod label selectors within a namespace. Pods not explicitly covered by a policy default to deny behavior for locked down environments. Policies allow whitelisting traffic between pods matching certain labels, enabling free communication to those meeting the criteria. Built-in Kubernetes network policy resources integrate with CNI providers like Calico and Cilium to implement the policies. Cluster admins write declarations indicating pods permitted to initiate connections to target pods, covering protocols, ports and directionality. Matching occurs based on pod labels rather than instance names.

Network policy rules combine to establish compartmentalized network segments across clusters, mitigating risks from unfettered lateral access. Restricting traffic to only required connectivity based on the principle of least privilege improves security posture. Network policies represent the first layer, with encryption, authentication and authorization complementary controls. Carefully crafted network policies which validate both Ingress and egress connectivity drastically reduce blast radius from within clusters in case of malicious attacks or accidental exposures. Segmentation limits impact to directly communicating pods rather than cluster wide. Hardening Kubernetes networking is paramount for security-focused environments through policies. To achieve this, you could try the following steps:

1.  Check that network policy support exists in the EKS cluster, as shown:
    
    eksctl utils describe-cluster --name demo --region us-east-1 | grep -i cni
    
2.  Label namespaces and pods that will be governed by the network policy. Labels are used for rule selection. For example, let us use the following labels:
    
    kubectl label ns myapp app=foo
    
    kubectl label pod myapp-pod app=foo
    
3.  Create a YAML file defining allow rules for ingress/egress connectivity between pod labels that should be permitted based on least privilege (refer to the following code):
    
    kind: NetworkPolicy
    
    apiVersion: networking.k8s.io/v1
    
    metadata:
    
    name: allow-foo
    
    spec:
    
    podSelector:
    
    matchLabels:
    
    app: foo
    
    policyTypes:
    
    \- Ingress
    
    \- Egress
    
    ingress:
    
    \- from:
    
    \- podSelector:
    
    matchLabels:
    
    app: foo
    
4.  Apply the network policy, as shown:
    
    kubectl apply -f network-policy.yaml
    

Now, only pods carrying the app=foo label can communicate to other pods matching that tag within the policy namespace. All other connectivity will be blocked.

[Custom networking](#contents.xhtml#sc2_242a)

The Amazon VPC CNI plugin handles pod networking and IP address management in EKS clusters. By default, pods get assigned IP addresses from the primary node subnet's CIDR range. However, if that subnet range is too narrow to support scaling pod counts within your workloads, IP exhaustion can quickly occur, preventing pod scheduling. Custom networking addresses this limitation by enabling secondary IP address ranges to be defined and used specifically for pod allocation. Rather than restrict pods to the primary node subnet CIDR, custom ranges carved from larger secondary VPC subnets can be configured instead.

The EKS custom networking feature allows the creation of ENIConfig custom resources that define a secondary VPC subnet CIDR to use for pods as well as an associated security group for those pods. The Amazon VPC CNI will then create ENIs connected to that secondary subnet to assign pod IPs from the allocated range. This prevents pod address exhaustion by moving allocation into a wider secondary subnet instead of the limited node primary subnet. Custom networking also allows controlling networking and security policies for the pods separately from worker nodes through a dedicated security group.

The VPC CNI will seamlessly handle attaching pods deployed to EKS worker nodes to the custom networking configuration rather than default primary networking. This enables cluster scale supporting significantly higher pod density without changing node subnets or lower-level networking. Custom networking paired with appropriate secondary VPC CIDR ranges simplifies resolving pod IP exhaustion as EKS clusters grow. The CNI handles the complexities of managing secondary ENIs and addressing them behind the scenes while benefiting from expanded allocation pools. To achieve this, let us do the following in an existing EKS cluster:

1.  Create a custom security group for pods, as shown:
    
    aws ec2 create-security-group \\
    
    \--group-name sg-eks-pods \\
    
    \--description "Security group for EKS pods”
    
2.  Define a custom subnet in your VPC for secondary IP allocation, as shown:
    
    ws ec2 create-subnet \\
    
    \--vpc-id vpc-abcd12345 \\
    
    \--cidr-block 10.7.0.0/20 \\
    
    \--availability-zone us-east-1a
    
3.  Create an ENIConfig resource config file, as shown:
    
    apiVersion: crd.k8s.amazon.com/v1alpha1
    
    kind: ENIConfig
    
    metadata:
    
    name: eniconfig
    
    spec:
    
     securityGroups:
    
    \- sg-eks-pods
    
    subnet: subnet-0ecac748
    
    vpcId: vpc-abcd12345
    
4.  Apply the ENIConfig resource with the following:
    
    kubectl apply -f eniconfig.yaml
    

This will configure the VPC CNI to assign pod IP addresses from the secondary subnet CIDR instead of the primary node subnet. Custom networking now enables scaling pods without exhaustion risks.

[Prefix delegation](#contents.xhtml#sc2_243a)

Amazon VPC CNI can assign network prefixes to Amazon EC2 network interfaces to increase the number of IP addresses available to nodes and increase pod density per node. You can configure version 1.9.0 or later of the Amazon VPC CNI add-on to assign a prefix instead of assigning individual secondary IP addresses to network interfaces. With prefix assignment mode enabled, the maximum number of ENIs per instance type remains the same, but Amazon VPC CNI can now assign /28 (16 IP addresses) IPv4 address prefixes instead of individual IPv4 addresses to the slots on network interfaces on nitro EC2 instance types. When prefix delegation is enabled, VPC CNI allocates an IP address to a Pod from the prefix assigned to an ENI.

During worker node initialization, the VPC CNI assigns one or more prefixes to the primary ENI. The CNI pre-allocates a prefix for faster pod startup by maintaining a warm pool. As more Pods are scheduled, additional prefixes will be requested for the existing ENI. First, the VPC CNI attempts to allocate a new prefix to an existing ENI. If the ENI is at capacity, the VPC CNI attempts to allocate a new ENI to the node. New ENIs will be attached until the maximum ENI limit (defined by the instance type) is reached.

When a new ENI is attached, ipamd will allocate one or more prefixes needed to maintain the warm pool settings defined in the CNI configuration. The size of the warm pool determines how many IPs are pre-allocated to avoid latency when pods are scheduled. To configure prefix delegation, the ENABLE\_PREFIX\_DELEGATION parameter must be set to true in the CNI configuration file on the worker nodes. There are also additional settings that can tuned, such as warm\_prefix\_target, which controls the number of prefixes maintained in the warm pool.

When enabled, the VPC CNI will assign one or more /28 prefixes to the primary ENI at node initialization time. As pods are scheduled on the worker node, IP addresses get allocated from the assigned prefixes. If additional prefixes are needed, the VPC CNI will attempt to assign more prefixes to existing ENIs first before allocating additional ENIs. This enables more efficient IP address allocation and higher pod density. There are a few key benefits of using prefix delegation in EKS clusters, as follows:

*   Increased pod density per node. Each prefix provides 16 IP addresses versus just 1 for secondary IPs.
*   Reduced IP address allocation latency when pods are scheduled since the warm pool has pre-allocated addresses ready.
*   Efficient IP address assignment since addresses are allocated from ENI prefixes without needing to assign secondary IPs individually.
*   Seamless experience without needing to make any application changes. The CNI handles all the IP address management on the worker nodes.

Some good practices when using prefix delegation include monitoring ENI and IP allocation on nodes, sizing the warm pool appropriately for your workload, and using instance types that support additional ENIs. To use this feature, try this as an example as follows:

1.  Upgrade the AWS VPC CNI plugin on the worker node, as shown:
    
    \# Install latest version > 1.9.0
    
    yum install -y amazon-vpc-cni-k8s
    
2.  Edit the CNI config file with the following command:
    
    vi /etc/cni/net.d/10-aws.conflist
    
3.  Enable prefix delegation, as shown:
    
    {
    
    "cniVersion": "1.0.0",
    
    "enable\_prefix\_delegation": true,
    
    "warm\_prefix\_target": 5
    
    }
    
4.  Set warm pool prefix target to 5. This will pre-allocate 5 /28 prefixes per ENI. Save config file and restart CNI daemon with the following command:
    
    systemctl restart aws-vpc-cni
    
5.  Confirm if the VPC CNI is configured to run in prefix mode. The ENABLE\_PREFIX\_DELEGATION value should be set to true:
    
    kubectl get ds aws-node -o yaml -n kube-system | yq '.spec.template.spec.containers\[\].env'
    
    This should provide the output as follows:
    
    \- name: ENABLE\_PREFIX\_DELEGATION
    
    value: "true"
    

After this, we should be able to see prefix assigned to the network interfaces of the worker nodes.

[Amazon VPC Lattice](#contents.xhtml#sc2_244a)

Amazon VPC Lattice is an application layer networking service that provides a consistent way to connect, secure, and monitor service-to-service communication across accounts and VPCs without needing networking expertise. Lattice handles common networking tasks like service discovery, traffic routing, and access authorization so developers do not have to build this functionality themselves. With a few clicks or API calls, developers can define communication policies between services across heterogeneous infrastructure like EC2, EKS, and Lambda. This increases developer productivity by eliminating complex networking and security challenges.

Lattice offers a range of key benefits that collectively enhance the development and operational aspects of applications. One significant advantage is the boost in developer productivity, as Lattice ensures a uniform networking, security, and observability framework. This enables developers to concentrate on business features rather than getting bogged down by intricate networking implementations. Furthermore, Lattice contributes to an improved security posture by facilitating the implementation of granular access control policies across services and enforcing encryption for in-transit traffic. Remarkably, this is achieved without imposing the burdensome overhead associated with certificate management.

In terms of scalability and resilience, Lattice excels by providing essential features such as routing and monitoring without introducing unnecessary resource overhead on workloads. This capability positions Lattice as a robust solution capable of supporting large-scale deployments and handling high requests per second, ensuring applications operate smoothly even under demanding conditions. Lastly, Lattice showcases remarkable flexibility by delivering consistent networking features that seamlessly operate across various infrastructure environments, including EC2, EKS, Lambda, and on-premises setups. This flexibility empowers organizations to choose the optimal compute environment that aligns with their specific needs and preferences. In essence, Lattice's multifaceted benefits contribute to a more streamlined and efficient development and operational experience for diverse application scenarios.

Lattice comprises several key components that collectively contribute to its functionality. Firstly, the Service Network serves as a logical grouping of services and policies, providing a shared environment for efficient collaboration. Within this network, the second component, the Service, plays a pivotal role by representing application units with DNS naming that spans across instances, containers, and serverless compute. A Service is composed of essential elements such as listeners, target groups, and targets. To maintain a comprehensive registry of services, Lattice incorporates the Service Directory, offering a global view categorized by version and DNS name within an AWS account. This directory serves as a centralized repository, facilitating streamlined management and accessibility of services.

Finally, Lattice emphasizes security through the inclusion of Security Policies. These policies are declarative in nature and play a crucial role in determining the communication allowances among services within a network or between different networks. By implementing Security Policies, Lattice ensures a secure and well-defined framework for interactions within the infrastructure, bolstering the overall integrity of the system. Collectively, these components form the core structure of Lattice, promoting efficient service management, secure communication, and streamlined application representation.

For EKS specifically, Lattice helps simplify pod-to-pod and pod-to-service communication between Kubernetes clusters and other services. Defining lattice service networks with authentication and authorization policies secures EKS communication without complex Kubernetes networking expertise. Native integration with AWS services like CloudMap and EventBridge allows service discovery and event-driven workflows across hybrid environments. Common EKS use cases like Istio service mesh are greatly simplified with Lattice handling mTLS and access control.

Overall, Lattice reduces complex application networking challenges into simple policy-based configurations that bind connectivity, security and visibility together consistently across heterogeneous infrastructure. The Gateway API is an open standard managed by the Kubernetes networking community that models declarative application networking resources in Kubernetes. It originated as a potential next-generation successor to the Ingress API and supports commonly used protocols and tight TLS integration lacking in Ingress. AWS implements the Gateway API by integrating it with Amazon VPC Lattice through the AWS Gateway API Controller add-on. When installed on an EKS cluster, the AWS Gateway API Controller handles provisioning Lattice networking infrastructure in response to users creating Kubernetes Gateway API resources like Gateways, Routes and HTTPRoutes. 

The AWS Gateway API Controller and integration with Amazon VPC Lattice enables different personas in EKS clusters to configure Lattice networking using native Kubernetes resources they are already familiar with. Specifically, infrastructure providers create GatewayClass definitions that map to the underlying Lattice service being used to implement the API. Cluster operators define Gateway resources that pull information and integrate with Lattice components like service networks, listeners and other constructs that have been defined. Finally, application developers create Routes and HTTPRoutes resources to direct client Ingress traffic to the backend Kubernetes services running on pods and nodes that make up their microservices. By leveraging declarative Kubernetes APIs, the Gateway controller abstracts the underlying Lattice infrastructure and networking so each persona can use familiar constructs and offload connectivity, security and visibility challenges onto Lattice via Infrastructure as Code principles. This simplifies usage of Lattice’s enterprise networking capabilities for EKS users across infrastructure, cluster and application tiers.

By leveraging the Kubernetes native Gateway API, Lattice capabilities like cross-account and cross-region service discovery, fine-grained access policies between services, end-to-end encryptions, and robust traffic metrics and logs are unlocked for EKS users without complex networking expertise. Common use cases like canary rollouts, traffic splitting, and observability that previously required specialized tools like Istio service mesh can now be enabled through simple Gateway API resources.

Overall, the AWS Gateway API Controller bridges the gap between the Kubernetes and infrastructure layers to activate Lattice's full features for EKS through declarative API abstractions. This reduces networking complexity for developers while providing enterprise-grade networking, security, and visibility for apps across heterogeneous infrastructure. Enable Lattice and install the Gateway API controller on your EKS cluster with the following command:

eksctl utils install-gatewayapi-controller

Create a GatewayClass resource for Lattice, as shown:

apiVersion: gateway.networking.k8s.io/v1alpha2

kind: GatewayClass

metadata:

name: lattice-gw

spec:

controller: “lattice.services.k8s.aws/lattice-loadbalancer"

Create a Gateway resource to configure a Lattice gateway (refer to the following code snippet):

apiVersion: gateway.networking.k8s.io/v1alpha2

kind: Gateway

metadata:

name: my-gateway

spec:

gatewayClassName: lattice-gw

listeners:

\- name: lattice-listener

port: 80

protocol: HTTP

routes:

backends:

\- conditions:

\- prefix: /

services:

\- name: my-service

port: 80

Link the Gateway to a Kubernetes service with the following command:

kubectl expose deployment my-app --port=80 —name=my-service

Lattice will automatically create the service network, listeners, and routes to enable Kubernetes pods to communicate securely based on the Gateway resource configuration. The Gateway API provides a Kubernetes native API to configure Lattice's networking and security policies. This simplifies defining application connectivity and infrastructure abstraction.

[Conclusion](#contents.xhtml#sc2_245a)

Robust and secure networking is essential for running production-grade EKS clusters at scale. In this chapter, we covered core networking abstractions like pod and service connectivity along with Ingress routing, load balancing integration, and advanced constructs such as prefix delegation, pod security groups, and network policies. Hands-on configuration steps and code samples demonstrated applying these networking capabilities to harden clusters through segmentation while still enabling reliable communication between applications and microservices.

From foundational pod and service networking enabled by the integrated AWS VPC CNI plugin to progressively adding complex network security, traffic management, and infrastructure integration through additive controllers, EKS provides integrated yet customizable networking for containers. Additional integration with Amazon VPC Lattice via the Kubernetes Gateway API further simplifies cross-account and hybrid networking complexity. EKS delivers enterprise-ready networking for pods backed by the proven scalability, availability, and security of AWS networking.

[Questions](#contents.xhtml#sc2_246a)

1.  How does the AWS VPC CNI plugin assign IP addresses and enable connectivity for pods in EKS clusters?
    
2.  What are some use cases for leveraging Ingress controllers in managing external traffic routing for EKS based applications?
    
3.  How can prefix delegation help maximize pod IP address allocation and density within EKS nodes?
    
4.  What security benefits do network policies provide in EKS?
    
5.  How does integration with Amazon VPC Lattice simplify hybrid and multi-cluster networking for EKS?
    

[Exercises](#contents.xhtml#sc2_247a)

1.  Install an Ingress controller like the AWS ALB Ingress controller on an EKS cluster and configure Ingress routing to a sample application.
    
2.  Enable prefix delegation on EKS worker node ENIs and analyze IP address allocation metrics before and after.
    
3.  Define security groups for pods and test applying them to sample workloads to validate policy enforcement.
    

# [CHAPTER 13Securing AWS Elastic Kubernetes Service Clusters](#contents.xhtml#ch13a)

[Introduction](#contents.xhtml#sc2_248a)

Amazon Elastic Kubernetes Service (Amazon EKS) emerges as an all-encompassing, fully managed solution that seamlessly facilitates the deployment, management, and scalability of containerized applications through the efficiency of Kubernetes. Despite the platform's user-friendly interface and robust capabilities, the imperative to fortify the security of EKS clusters is undeniable, acting as a critical line of defense to safeguard sensitive workloads and data within the dynamic ecosystem of container orchestration. Recognizing the intricate nature of security challenges, a multifaceted approach becomes essential, delving into various facets, namely pod security, network security, authentication, authorization, monitoring, encryption, and infrastructure security.

Within this expansive framework, this chapter becomes a compass, navigating through best practices and tailored options meticulously designed to meet the nuanced needs of EKS clusters. A comprehensive spectrum of considerations comes into play, encompassing access controls to regulate permissions, adherence to compliance standards, heightened visibility for effective monitoring, and the implementation of data protection mechanisms. The aim is to equip EKS users with a robust security posture that not only mitigates potential risks but also aligns seamlessly with the stringent security objectives governing their cluster workloads. This proactive stance becomes a cornerstone, ensuring that the potent combination of power and flexibility inherent in Amazon EKS is harnessed to its full potential without sacrificing the integrity and confidentiality of the containerized applications and their associated data.

By immersing in the detailed security guidelines provided, EKS users embark on a journey towards a fortified environment where the inherent strengths of Amazon EKS are maximized, bolstered by a proactive commitment to security. This comprehensive approach not only safeguards against potential threats but also instills confidence in users, assuring them that their containerized applications are shielded within a secure and well-governed EKS cluster. As technology advances and security challenges evolve, the guidance within this section stands as a beacon, adapting to the dynamic landscape and ensuring that EKS users remain at the forefront of secure container orchestration practices.

[Structure](#contents.xhtml#sc2_249a)

In this chapter, we will look at the following topics in detail:

*   Pod security
*   Node security
*   IAM role for service accounts
*   Secrets management
*   Amazon GuarDuty for EKS
*   Pod Security Standards
*   Policy management
*   EKS Pod Identity

[Objectives](#contents.xhtml#sc2_250a)

In the dynamic landscape of modern application development, the pursuit of rapid feature delivery and agile iteration speeds takes center stage for application teams. Leveraging the efficiency of containerized microservices and serverless functions deployed into Amazon EKS, these teams strive for optimal performance and scalability. However, amidst this relentless pace, the onus of governing security, compliance, and risk management falls squarely on the shoulders of platform operators and cluster administrators. These individuals are tasked with enforcing essential guardrails across the spectrum of development, staging, and production environments, ensuring the integrity and security of the entire system.

The focal point of this chapter is to empower both application teams and operational personnel by providing practical and actionable controls guidance applicable throughout the entire lifecycle of Amazon EKS management. Offering valuable insights and takeaways, readers can expect to gain access to reference architectures, security workflow patterns, and operational runbooks. These resources are designed to be directly applicable to their day-to-day responsibilities, particularly as workloads transition from code repositories holding infrastructure as code templates into downstream provisioning.

Each discussion within the chapter surrounding control areas is meticulously crafted to equip practitioners with in-depth knowledge concerning risk considerations, available capabilities, and step-by-step configuration procedures. The goal is to tailor these insights specifically to harden Amazon EKS use cases, drawing from industry best practices and real-world experiences. By incorporating cross-references between various controls, the chapter seamlessly integrates solutions, providing a holistic understanding of how different elements work together to create a secure and compliant EKS environment.

[Pod security](#contents.xhtml#sc2_251a)

Securing pods represents a critical element of protecting overall security posture in Amazon EKS environments. As the basic units of workload abstraction within EKS clusters, pods interact extensively with other internal and external services and resources. Hardening pod configurations can limit damage in the event of an individual pod compromise.

Pods authorize against the EKS API server to read from or write to resources and endpoints. By default, pods utilize service accounts which grant access via default ClusterRoleBindings. These service accounts may provide excessive permissions beyond what is needed for a pod's function. One best practice involves configuring more restrictive pod service accounts and RoleBindings. For example, linking pods to a custom service account that only binds to a specific role covering that pod's explicit read/write resource needs. Tightening service account scopes limits the blast radius of what could be accessed if a malicious pod or container obtained service account credentials from another pod.

In addition to access controls, pod security contexts represent areas in need of hardening from defaults. Security contexts define privilege and access levels, such as whether a pod runs as root user ID (uid=0) and what Linux capabilities are available to containers in the pod. Restricting privileged mode and capabilities tightens the security context of what malicious code could achieve if able to execute inside the pod. Removing Linux capabilities like SYS\_ADMIN, NET\_ADMIN, and permissions to mount host volumes would tamp down potential lateral movement or node compromise via unintentional container breakout scenarios into host namespaces.

Going beyond individual pod definitions, EKS admins can enforce security policies on pods at time of creation or mutation. Using OPA Gatekeeper and ConstraintTemplates allows creating consumable policy restrictions on pod specs that are controlled via admission control when pods are launched. Constraints can check for field values in the pod manifest like service account names, security contexts, namespace selectors and volume sources to block non-compliant pod launches violating organizational policies. ConstraintTemplates becomes a powerful way to apply baseline security standards on all EKS pods consistently from deployment.

While pod specifications govern access controls and settings, network controls provide another vector for limiting pod communication risks. Tools like network policies, security groups, VPC flow logs, and network firewalls give pod-level visibility and governance over ingress and egress connectivity. Segregating workload communications and filtering flows via these controls adds further compartmentalization based on pod labeling for deployments that align to trust boundaries in the environment. Beyond foot traffic filtering, network-layer controls also accelerate forensic evaluations by capturing essential metadata about all pod interactions for rapid historical lookups.

Threat detection within running pods represents an additional consideration alongside preventative measures. Falco and Sysdig Open Source can be deployed as daemon sets across EKS nodes to provide kernel-level runtime security event capture, compliance checks, and behavioral anomaly alerts related to pod access or networking. As an open-source alternative to commercial tools like Sysdig Secure, Falco taps into Linux audit frameworks for deep packet inspection and system calls analysis to flag when pod activities deviate from expected authorized behaviors. Extending detection capabilities to host processes surrounding pods closes visibility gaps as malicious activities often target host-level resources that can impact pods like container engines, kernels and cloud provider metadata services.

Scanning pods for misconfigurations or exposing sensitive files also assist in hardening efforts by proactively identifying issues before adversaries exploit easy targets. Tools like kube-hunter actively test pods against common attack patterns to identify areas of improving security hygiene. Additionally, continuously scanning deployed pod infrastructure as code definitions assists in preventing pod drift from secure baselines into increased risks from new CVEs across image registries, OS packages, and software dependencies as code moves through CI/CD pipelines. Static and dynamic scanning combined fortify pods from known issues while monitoring and enforcement guardrails prevent easy mechanism for reintroduction of problems.

While pods should be locked down, some workloads require segregation rather than restriction. For multi-tenant EKS use cases with untrusted users running privileged pods, additional isolation should be mandated between pods belonging to different teams or customers. Containers add segmentation however nodes allow potential breakouts. Advanced network controls, admission rules, and using tools like Calico together enforce strict micro segmentation between pods running on shared infrastructure. Applying namespace quotas based on node allocations ensures fair use while preventing noisy neighbor issues resulting from resource starve outs.

Protecting sensitive data that pods rely upon represents an additional consideration given pods often utilize mounted Kubernetes secrets containing API keys, self-signed certificates, application passwords and configuration data. The etcd key-value store backing EKS lacks default encryption granting visibility to secrets by default cluster admin roles. The etcd-encryption-kms plugin can securely encrypt secrets at the etcd layer protecting critical pod assets at rest. For protecting secrets in transit, enabling mTLS authentication for cluster endpoints, pod service networking and ingress controllers prevents man-in-the-middle attacks through traffic encryption. Locking down Kubernetes RBAC binding scopes limits secret visibility to only authorized pods and service accounts.

Lastly, comprehensive visibility remains imperative given vectors exist for potential breakouts, data exfiltration via network endpoints, or abuse of identities and permissions. Strong logging, monitoring, auditing and alerts create the feedback cycle to accelerate detection, response and remediation when suspicious pod events, anomalies or incidents take place. Passing logs to storage solutions like S3 buckets or analytics services such as Mizuho or Chronicle aids deeper investigation of big data correlations that identifies threats earlier through pattern recognition powered by machine learning. Tracing network flows between pod cohorts assists in forensic evaluations by rapidly identifying anomalies in communications indicative of east-west movement associated with compromises for historical pivots.

[Node security](#contents.xhtml#sc2_252a)

Amazon EKS worker nodes represent the underlying infrastructure where Kubernetes schedules and runs containerized pod workloads. As the interface between sensitive pod data and the hosting environment, nodes require additional security considerations beyond typical EC2 hardening baselines. The elevated privileges of the kubelet process which manages pod lifecycles combined with pods mounting host directories for storage and network attachments all increase risks of nodes as attack vectors.

Limiting direct access represents the priority for securing EKS nodes. While EC2 security groups provide network perimeter controls, additional authentication and authorization policies should govern human and application access alike. Strictly controlling SSH logins with ephemeral credentials prevents standing privileged shell sessions. Integrating nodes exclusively into central identity providers enables the revocation of compromised credentials. Two-factor authentication raises the bar for authentication assurance levels.

Process-level access on nodes also warrants governing based on least privileges. The node kubelet daemon requires broad read/write access to facilitate pod operations. Hardening the attack surface of the kubelet helps minimize damage if its credentials are ever compromised. Similarly, utilizing IAM roles for EC2 instances that map to specific AmazonKubernetesService\* managed policies only grants needed privileges. Avoiding blanket \* type permissions lowers risk of pre-existent credentials lying dormant ready for abuse in hands of bad actors.

Communication channels entering and exiting EKS nodes represent high value targets for intercepting sensitive Kubernetes control plane traffic or data from node workload communications. Enabling TLS not only for the front-end API server but also the kubelet API protects critical infrastructural endpoints from MiTM tampering or takeovers. Wherever possible, forcing all ingress and egress traffic to route over VPN or AWS Direct Connect facilitates transport encryption, plus packet inspection and filtering controls to detect anomalies.

Threat prevention on nodes remains crucial but insufficient as some will inevitability slip past defenses over time. Expanding capabilities for detection, alerting, and visibility into node activities provide oversight for when or not scenarios occur. Open-source options like Falco tap into Linux audit frameworks and eBPF for deep packet inspection of system calls related to sensitive files, network events, privilege escalations and susceptibility to attack patterns. Daemonized agents send security events to centralize SIEMs. Together, prevention and detection give inside out and outside in coverage.

Despite scaling best practices security controls and practices across infrastructure configurations and network architectures alike, the reality of compute persists with no environment totally impenetrable. Isolating risks of outright node compromises represents the last line of defense in securing EKS. Planning incident response scenarios which assume breach contain the ability for adversaries to move laterally or vertically throughout node groups. Compromised node draining, quarantining, replacement and gathering forensic artifacts for analysis accelerates mean time to recovery while halting expansion beyond singular footholds.

[IAM role for service accounts](#contents.xhtml#sc2_253a)

IAM roles for service accounts (IRSA) represent a robust mechanism to implement least privilege access controls and governance guardrails around Kubernetes workloads running on Amazon EKS. IRSA allows managing permissions to interact with AWS resources or services via IAM for EKS pods based on their associated service account instead of the node's role or human IAM users.

This enables granular scoping of access at the pod level based on logical mappings to service accounts. For example, backend API pods may map to a backend-app-sa service account binding to an IAM role called backend-pod-role allowing only S3/DynamoDB CRUD access. Whereas separate frontend pods leverage a frontend-sa service account connecting to a frontend-role with ELB/CloudWatch/SNS permissions. That way compromised API keys or JWTs remain confined only to scopes defined on each specific role.

Under the covers, IRSA leverages OIDC identity providers connected over the pods native Kubernetes authentication flow rather than introducing new external tokens. The EKS OIDC provider provisions tokens signed by the cluster that map service account subjects to external roles. STS federated authentication authorizes assuming the role based to grant time-bound credentials. This avoids the need to directly embed IAM keys as file-based token mounts or environment variable exports that could expose credentials into the container or image build pipelines. Instead, temporary creds attach to the pod's filesystem, transparently refreshing in the background without applications having to explicitly re-up authorizations.

From an implementation perspective, introducing IRSA to an EKS cluster involves three main components: enabling the OIDC provider on EKS, creating Kubernetes service accounts to represent workload identities, and then linking IAM roles plus policy attachments to service accounts as represented in the access manifest. Service account creation utilizes native Kubernetes APIs, while new IAM roles follow AWS best practices around least privilege. The OIDC provider activation happens once at cluster creation or with a single update.

As a conceptual analogy, think of IRSA as like User/Group separation where service account lives in the Kubernetes namespace, while IAM roles equate to Groups containing access permissions that get assigned to accounts based on namespace labeling and annotations. Admins can centrally update policies on roles while scaling decentralized service accounts across applications without embedded credentials. Revoking access requires only detaching IAM roles from service accounts rather than hunting down deployed secrets. Overall, IAM roles for service accounts unlock cloud native security approaches for granular ACLs with native identity integrations that avoid secrets sprawl. Segmenting access tiers based on Namespace attributes as part of zero trust architectures limits blast radius from compromised workload without heavy lifting updating deployment manifests.

[Secrets management](#contents.xhtml#sc2_254a)

Kubernetes secrets represent a core primitive for securely distributing credentials, keys, tokens, certificates, and other sensitive data to pods running on Amazon EKS. However, natively secrets provide base64 encoding rather than encryption for data at rest. Storing manifests directly in Git risks trivial decryption exposure in pipelines. These challenges prompt the need for external secrets management integrated with EBS deployment workflows. Sealed Secrets provides one solution for managing EKS secrets externally before syncing into the cluster. It leverages asymmetric cryptography by using a sealing key stored in the cluster to encrypt secret manifests which admins check into source control. A controller syncs encrypted secrets from the repo, decrypts with the cluster key and creates native Kubernetes secrets accessible to authorized pods. This bridges encryption gaps with Git based workflows.

Admins first initialize SealedSecret controllers into target namespaces with access to a public/private key pair. Public keys encode manifests locally before they commit to GitHub, for example, when private keys decrypt on the cluster side. Permissions allow restricting controller access and sealing key usage to admin roles only. Secret rotation happens by re-sealing with an updated public key rather than needing to redeploy pods. Destroying keys or controllers wipes all derived secrets by design to avoid leftovers outliving usage policies. Sealed Secrets represents one third party tool that uses client-side encryption to solve secrets management challenges. Other methods like HashiCorp Vault or AWS Secrets Manager offer alternative approaches deeply integrated into upstream identity providers, key storage systems and encryption APIs. Vault benefits from mature RBAC, dynamic secrets, leasing, and multiple backend/unseal options, while Secrets Manager taps into AWS KMS protections.

Natively, AWS Secrets Manager allows creating managed secrets tied 1:1 with KMS keys for envelope encryption at rest while respecting IAM permissions and resource policies for access controls. EKS pods configure IRSA to assume IAM roles that allow calling Secrets Manager APIs to retrieve secret details at runtime without hard coding tokens. Automatic rotation based on schedules incrementally provisions new secret versions that pods transparently handle via SDKs without rebuild workflows.

Revocation occurs by disabling IRSA role permissions for service accounts to access secret ARNs, while deletion removes payloads after staging waiting periods to mitigate accidental permanent loss. Charge only accrues for payloads encrypted plus API calls rather than static storage allocations to keep costs proportional to value secured. Audit trails cover both Secrets Manager console and API calls, plus the underlying Key Management Service provides detailed access telemetry against encryption keys used for Federal compliance reporting needs. Combined AWS and Kubernetes management planes unlock server-side encrypted secrets as turnkey services managed external to repos with tighter access controls and native identity integrations for EKS deployments.

[Amazon GuardDuty for EKS](#contents.xhtml#sc2_255a)

Amazon GuardDuty represents a threat detection and response service providing continuous monitoring across AWS accounts and cloud assets, including visibility into risks targeting Amazon EKS control planes. GuardDuty analyzes metadata streams from CloudTrail, VPC Flow Logs, DNS Logs, benchmark patterns, and imported threat intelligence to identify potential incidents. For EKS, GuardDuty focuses on two areas: auditing Kubernetes API requests and payloads to the EKS endpoints for policy violations or compromise attempts and runtime security inspection of node activities searching for signs of crypto mining or compromised credentials.

Auditing the EKS API surface provides visibility as Kubernetes auditing logs pipe into GuardDuty through integration with CloudWatch Events or direct ingestion. Analyzing API patterns reveals suspicious queries against pod or service metadata, which could indicate a compromised principal probing for lateral movement pivots. Repeated unauthorized access attempts against the EKS endpoint may represent brute force credential stuffing attacks attempting to establish an initial foothold.

In addition to EKS APIs, GuardDuty also monitors the security groups, ENIs, EBS volumes, Route53 queries and Lambda functions associated with EKS clusters searching for misconfigurations or unusual traffic flows to/from workloads that deviate from historical baselines. For example, a Node termination failure event could indicate adversary actively preventing auto scaling replacements to maintain persistence.

GuardDuty surfaces detected threats through Security Automation and Orchestration Playbooks fed into SIEMs, SOAR platforms or human review queues. Tagged EKS asset IDs and categories allow rapid scoping to narrow incidents just to container runtimes. Automating response actions like triggering Lambda functions to isolate compromised worker nodes demonstrates built-in remediation pathways once alerts validate true positive risks.

Expanding into runtime protection for EKS nodes and pods leverages GuardDuty Container Insights. Purchase or trial activation of the container-focused threat detection offering installs the CWAgent and ciprotect module onto nodes as a daemonset. Access to syscall, network and file behaviors feed behavior analysis and asset inventory mapped to cluster constructs like container ids and images, node ARNS, assigned security groups and more. This data powers anomaly detection against deployments for signs of cryptojacking in containers, network scanning from pods, privilege escalations on hosts, malware infections, plus sophisticated attacker behaviors representing breached environments and infrastructure hijacking. Container insights integrate with other AWS visibility planes, as CloudWatch Metrics, X-Ray Traces, Billing alarm spikes correlated against runtime node activities paint contextual threat scenarios.

GuardDuty Container Insights shines strongest with AWS Fargate serverless runtimes given challenges instrumenting underlying infrastructure. Across EKS and Fargate, Cloud Native Application Protection platforms like Sysdig Falco parse system calls, k8s audit logs, and high-fidelity network events, which GuardDuty can ingest via CloudWatch Logs subscriptions, opening more telemetry data streams. Extending threat detection coverage through GuardDuty to audit EKS management consoles and gain at runtime visibility against underlying node activities enables Kubernetes customers to identify risks from misuse of legitimate credentials, crypto mining in containers, supply chain compromises and insider threats.

[Pod Security Standards](#contents.xhtml#sc2_256a)

Kubernetes environments face innate security challenges stemming from the highly dynamic and ephemeral nature of containerized workloads and microservice architectures. Pods exhibit volatile creation, updating, scaling and teardown churn as organizations increasingly embrace CI/CD deployment patterns for cloud native development. These rapidly changing environments increase the risk of deploying misconfigured pod manifests to production. Such misconfigurations may lack proper security controls, hardening measures, or protections for the assets that pods access. This can lead to vulnerabilities in areas like asset mounting, networking, and credential access.

Controlling security hygiene across the pod life cycle with guardrails, policy enforcement and drift prevention represents a primary concern for teams operating Kubernetes clusters, especially at a scale across disparate application teams integrating third party code or open-source components full of potential vulnerabilities. Amazon EKS provides all the rapid provisioning and orchestration strengths of Kubernetes while requiring approaches to lock down pods, avoiding bad practices that leave pod escape hatches, escalated privileges, or access to sensitive backends used for lateral traversal in the wrong hands.

To address this concern set, Kubernetes introduced a concept known as Pod Security Standards (PSS), starting initially in version 1.21 before reaching general availability in Kubernetes 1.25. PSS defines a set of security best practices and control objectives covering various principles related to governing pod access controls, limiting excessive privileges, restricting mounting various host system volumes or assets, specifying Linux capability sets and similar areas impacting pod hardening postures.

Rather than leaving such security configuration entirely up to each application team in a bespoke fashion, PSS outlines cluster administrators and platform operators to centrally codify and enforce baseline policies. Having common standards ensures consistency at scale rather than hoping that developers independently uplevel their own pod hygiene. The standards approach focuses remediation effort on improving Kubernetes YAML policies rather than chasing down runtime issues vulnerably exposed in production.

The PSS project originally consisted of three different standards scoping various levels of increasing hardening categories applicable to different use cases. The privileged posture remains fully permissive, allowing pods to run as root, bind host ports and file systems, or use elevated Linux capabilities suitable for platform-level pods powering operational functions like logging, monitoring, service mesh sidecars, or storage providers integrating deeply into lower layers of the infrastructure stack. Most application pods fall under the baseline PSS designation, which strips away unnecessary privileges but allows properly configured workloads to handle their own processing needs without overprovisioning abilities to impact platform components unintentionally or maliciously. Restricted profiles take the final step in enforcing various pod security enhancing configurations like mandating read-only root file systems, blocking privilege escalation paths via capabilities, and requiring verified image signatures.

With the different PSS tier definitions scoped, putting associated controls into practice within EKS clusters involves leveraging another Kubernetes feature known as Pod Security Admission webhooks. Also reaching general availability in Kubernetes 1.25, this dynamic admission controller functionality allows intercepting API requests to create, modify or delete pod resources. Evaluating YAML manifest contents against configured PSS policies blocks submissions failing to meet security standards. Several enforcement options provide flexibility determining how strictly to gate pod submissions depending on organizational compliance needs. Enforce mode outright rejects non-conforming pods as the default posture. Audit passes deficient pod launches but flags policy violations for tracking and visibility. Warn mode also allows insecure pod launches while alerting on security gaps prompting remediation by developers. Namespaces that lack explicit PSA configuration inherit the default privileged posture with no restrictions.

This puts power into the hands of EKS administrators to sculpt security standards catering to trust levels, compliance, and risk appetite across various namespace segments. For example, production services may mandate restricted pod policies while development environments remain unconstrained for rapid experimentation unless pushing to staging or production pipelines. Cluster operators can enact blanket baseline policies with exemptions carved out for infrastructure namespaces running CNI providers for networking or logging agents monitoring from privileged vantages.

Combined, PSS definitions and PSA enforcement mechanisms provide EKS customers native capabilities for governing security hygiene as code progresses from repositories into production without requiring additional tools or consoles while still retaining Kubernetes' flexibility in adapting policies to specific applications.

[Policy management](#contents.xhtml#sc2_257a)

Kubernetes intentionally avoids prescriptive guardrails, recognizing that organizations have varying standards, controls, and security needs applicable to their cloud environments and workloads. However, such flexibility results in configuration drift sprawl without consistency in managing policy rules. As organizations scale container deployments, infrastructure teams require policy as code solutions, ensuring uniformity in governing clusters across multiple applications and platform components collectively while still adapting rules tailored for specific scenarios.

Kyverno represents one such open-source project purposely built as a policy engine for defining and enforcing admission controls as Kubernetes native resources without new languages to learn. As developers commit YAML manifests declaring deployments, services, ingress routes and more into repositories and pipelines, Kyverno policies mutate and validate API object creation requests against configured best practices, codifying governance directly into provisioning flows rather than chasing down configuration debt accrued in production. Policies declare match conditions, identifying applicable target resources via attributes like kind, name, labels and namespace. Applied rules then check, transform or generate configurations predefining desired or prohibited elements to enforce change controls as code attempts infrastructure modifications. For example, rules can require pods to limit compute resource requests and define ingress routing rules based on namespace traits. Additional logic blocks unlabeled services from getting exposed publicly or prevent scale commands that would exhaust predefined cost quotas.

Kyverno taps into the extensibility of the Kubernetes admission controller architecture, intercepting API server requests as a validating and mutating webhook and delivering policy decision verdicts, allowing, denying, or patching submissions. Running as a dynamic plugin embedded into EKS, Fargate, and EC2 cluster control planes removes external dependencies or consoles to manage, avoiding costly refactoring as policies evolve alongside configurations. Audit logging and event generation provide policy feedback loops for administrators to refine rules chasing compliance needs or address overly restrictive cases hindering developers.

Being Kubernetes native, Kyverno policies benefit from native interfaces, CLI tooling, and RBAC permissioning, building upon constructs teams already utilized daily rather than introducing proprietary semantics. Policy updates sync from source-declared versions rather than depending on agent runtime polling. Conducting expansions into managing image attestations and TUF signature validation evaporates additional organizational interfaces into unified policy planes. Combined with PSS for workload hygiene and OPA Gatekeeper constraints governing cluster component configurations, Kyverno policies ensure EKS infrastructure compliance, staying within security guidelines, protecting multi-tenant environments against misconfigurations like overly permissive network policies, IAM roles granting excessive access or encryption deficiencies on sensitive data stores.

In the world of Kubernetes, security and compliance are paramount concerns for organizations of all sizes. Kyverno shines in this arena by offering concrete ways to enforce best practices. For instance, it can ensure that all containers run as non-root users, a crucial security measure that reduces the risk of container breakouts. Kyverno can also mandate the use of read-only root filesystems, limiting the potential for malicious modifications. When it comes to regulatory compliance, Kyverno proves invaluable. It can enforce HIPAA requirements by ensuring encryption for sensitive data or implement PCI-DSS standards by isolating environments that handle cardholder data. For organizations grappling with GDPR, Kyverno can enforce data minimization practices and strict access controls.

Resource management and networking are other areas where Kyverno's policy enforcement capabilities prove their worth. It can set CPU and memory limits for all containers, preventing resource hogging that could destabilize the cluster. Kyverno can enforce resource quotas per namespace, ensuring fair resource allocation across teams or applications. It can mandate specific ingress and egress rules on the networking front, enforcing network segmentation between namespaces. This is crucial for maintaining a strong security posture and preventing lateral movement in case of a breach. Kyverno can also require TLS for all ingress traffic, enhancing data protection in transit.

Image security and access control are critical aspects of Kubernetes management that Kyverno addresses effectively. It can restrict deployments to only images from approved registries, reducing the risk of introducing vulnerable or malicious containers. Kyverno can also enforce image scanning policies, blocking deployments with critical vulnerabilities. For access control, it can mandate the use of specific service accounts for workloads and enforce RBAC policies across namespaces. This granular control over permissions helps maintain the principle of least privilege, a cornerstone of robust security. Lastly, Kyverno can assist with compliance auditing by generating reports on policy violations and enforcing retention policies for audit logs. This makes it easier for organizations to demonstrate compliance during audits and maintain a clear picture of their security posture over time.

[EKS Pod Identity](#contents.xhtml#sc2_258a)

Managing authentication and access controls for large scale Kubernetes deployments across a fleet of Amazon EKS clusters presents governance hurdles ensuring security hygiene. Hundreds of namespaces may subdivide network segments and compute isolation yet share common backend resources needs like Amazon S3 buckets, DynamoDB tables, or Secrets Manager encryption keys. Keeping identity and permissions synchronized securely while still maintaining least privilege protections represents an ongoing pain point.

EKS Pod Identity intends to streamline this user experience by removing the external AWS Identity and Access Management console dependency when configuring role-based permissions required by applications deployed into pods. Instead, cluster administrators directly integrate IAM single sign-on authentication with service accounts as native Kubernetes resources avoiding cumbersome modifications to role trust relationships, prohibiting assumed roles scaling across EKS clusters. Rather than embedding keys into container images or YAML manifests, pod identity authorization transparently handles temporary credential exchanges to fulfill pod resource requests through AWS SDKs and CLIs. Credentials get attached directly onto the pod filesystem like projected service account tokens yet contain IAM principals rather than service account subjects. Cluster workloads never directly manage the access keys or sessions.

Implementation allows cluster administrators to first create reusable IAM roles with permission policies covering expected read/write needs against S3, SQS, Dynamo and more AWS services. No special EKS conditions exist on the role trust policy thanks to tokens signed by the cluster identity provider. These standalone roles then get linked against Kubernetes service accounts via API annotations. A new controller watches for service accounts with pod identity bindings, checks RBAC authorization to validate policy create requests, requests short-lived session credentials mapped to the IAM role resource, and projects down temporary AWS access keys, tokens, and regional endpoints into the pod during scheduled placement.

Workloads utilize AWS SDK clients, which automatically discover populated credentials from pod filesystems and transparently refresh tokens by leveraging built-in retries rather than hard coding access key IDs and secret values into deployment configurations. Session tags inherited from pod identity enable administrators to craft singular policies functioning across multiple roles by checking values like cluster name, namespace, service account, and pod IDs for contextual authorization.

EKS pod identity streamlines cloud IAM configuration through Kubernetes native integration without managing external web identity providers. Troubleshooting bad permissions, leaked keys, or excessive access no longer mandates SSH tunneling into bastion hosts to pore through container logs and configs, hunting down sources of guns or butter.

[Conclusion](#contents.xhtml#sc2_259a)

Amazon Elastic Kubernetes Service provides teams with advanced clustering functionality fueling containerized microservices deployment at scale across distributed networks of container hosts. While EKS solves major orchestration complexity hurdles, realizing production readiness requires acknowledging additional security considerations from workload isolation assurances down through the integrated infrastructure stacks.

This chapter sought to accelerate organizations leveraging EKS to modernize application architectures without inadvertently introducing risks or compromising compliance obligations by thoroughly examining attack surfaces alongside hardening controls available against pod, network, access, infrastructure, and data threat vectors. Each section contained actionable configurations like admission controllers, network policies, TLS certificates, IAM roles, and security groups to apply immediately towards a layered defense-in-depth strategy reinforced by visibility and detection capabilities.

Readers should take comfort in the fact that EKS security best practices will continue evolving in parallel as AWS services enhance encryption options, identity integrations, certificate management and network segmentation controls further automating security hygiene. Concurrency of agility and oversight stands achievable by collaborating early across development, operations, security and platform teams while ensuring all voices remain empowered, enforcing policies scalably as code traverses the delivery pipeline ultimately into production.

In the next chapter, we will discuss about the storage options with EKS including AWS Elastic Block Service (EBS), AWS Simple Storage Service (S3), etc.

[Questions](#contents.xhtml#sc2_260a)

1.  Which Kubernetes admission controller can enforce pod-level security policies?
2.  How can you limit network access to EKS pod workloads?
3.  What methods allow for role-based access control to EKS resources?
4.  What tools can provide centralized visibility and alerting for EKS security events?
5.  How can you enable TLS encryption for Kubernetes secrets?

[Exercises](#contents.xhtml#sc2_261a)

1.  Install OPA Gatekeeper and use ConstraintTemplates to enforce a pod security policy.
2.  Define a Kubernetes Role and RoleBinding to implement least privilege access for an app.
3.  Enable envelope encryption via the KMS provider for etcd data encryption.

# [CHAPTER 14Storage Options for AWS EKS Workloads](#contents.xhtml#ch14a)

[Introduction](#contents.xhtml#sc2_262a)

Elastic Kubernetes Service (EKS) stands as a managed Kubernetes solution within the AWS ecosystem, facilitating the deployment and operation of containerized applications. One of the pivotal considerations when orchestrating applications on EKS is the realm of storage. For applications to function optimally, they necessitate durable, scalable storage solutions that cater to various requirements, such as data persistence, seamless data sharing between pods, resilience against crashes and restarts, and more.

This chapter serves as an in-depth exploration of the diverse storage options available for EKS workloads. To establish a solid foundation, it delves into the core Kubernetes storage abstractions, encompassing volumes, persistent volumes, storage classes, and other fundamental concepts. Subsequently, the exploration ventures into a comprehensive examination of various storage services that seamlessly integrate with EKS, including Amazon Elastic Block Store (EBS), Amazon Elastic File System (EFS), Amazon FSx for NetApp ONTAP, and Amazon FSx for Lustre.

Each of these storage options is meticulously elucidated, providing detailed insights into their respective use cases, benefits, limitations, pricing models, setup procedures, and more. The aim is to equip readers with a nuanced understanding of each storage solution, allowing them to make informed decisions based on their specific workload requirements. The chapter offers valuable guidance on when to opt for a particular storage system, aligning choices with the unique demands of different workloads running on EKS.

By the conclusion of this chapter, readers are expected to possess a comprehensive and practical understanding of the storage landscape within the EKS framework. The insights garnered throughout the section enable readers to architect storage solutions effectively for their EKS applications, ensuring an optimal balance between performance, resilience, and scalability. In essence, this chapter acts as a valuable guide, empowering readers to navigate the intricate terrain of storage considerations within the context of Elastic Kubernetes Service.

[Structure](#contents.xhtml#sc2_263a)

In this chapter, we will explore the following topics:

*   Core Kubernetes storage concepts
*   Amazon Elastic Block Store
*   Amazon Elastic File System
*   Amazon FSx for NetApp ONTAP
*   Amazon Simple Storage Service
*   Amazon FSx for Lustre
*   Architectural considerations and decision criteria

[Objectives](#contents.xhtml#sc2_264a)

The prime objective of this document is to empower readers with comprehensive practical understanding so that they can architect optimized, resilient, scalable, and cost-efficient storage solutions for stateful applications running on EKS.

It aims to establish core conceptual foundations first before exploring integrations with various AWS managed storage options built to address EKS workloads like EBS, EFS, FSx ONTAP and FSx Lustre. Each option is covered in depth through the lens of capabilities, use cases, setup, access controls, scalability, resiliency, consumption pricing and example usage patterns paired with EKS clusters.

By assimilating learnings across concepts and capability mappings, the concluding goal is to enable readers to select appropriate storage systems relative to performance, IOPS, throughput, redundancy, backup needs, scalability growth, access patterns, and budgets when designing storage blueprints natively integrated with EKS.

[Core Kubernetes storage concepts](#contents.xhtml#sc2_265a)

Within the field of EKS, the nuanced landscape of storage options necessitates a foundational understanding of key Kubernetes storage concepts. This chapter serves as a gateway to the intricacies of EKS storage by unraveling these fundamental elements. First and foremost, volumes emerge as a cornerstone, facilitating the attachment of storage resources to pods. This integration ensures that applications have the requisite data persistence, fostering seamless data sharing between pods and laying the groundwork for optimal functionality within the dynamic EKS environment.

Venturing further into the storage architecture, Persistent Volumes (PVs) become a focal point. These entities stand as a critical abstraction, allowing for the provision of storage resources independent of pod lifecycles. The significance of PVs lies in their ability to maintain data accessibility and persistence amidst the dynamic changes that pods undergo, contributing to the robustness of EKS storage solutions. Simultaneously, Persistent Volume Claims (PVCs) play a pivotal role, serving as a mechanism through which users and applications articulate their specific storage requirements. This tailored approach to storage allocation empowers users to delineate their needs within the flexible EKS ecosystem.

The exploration continues with the elucidation of Storage Classes, serving as pivotal abstractions that define storage provisioning policies. This standardized approach ensures efficiency and consistency in managing storage resources within EKS. Storage Classes provide a structured means of provision storage based on predetermined criteria, promoting a systematic and streamlined approach to storage management within the EKS environment.

The final piece of the puzzle, Dynamic Provisioning, introduces an automated mechanism for storage provisioning based on the specifications outlined in PVCs. This dynamic allocation of storage resources optimizes the provisioning process, allowing for the adaptive scaling of storage capacity to match the evolving needs of EKS applications seamlessly. As a result, EKS users benefit from a responsive and efficient storage infrastructure that aligns with the dynamic nature of containerized applications.

Collectively, these foundational concepts create a cohesive framework for persistent storage management within EKS pods and applications. Proficiency in these concepts serves as a prerequisite, laying the groundwork for a comprehensive exploration of the diverse EKS storage options. By establishing a solid foundation, readers gain the ability to navigate subsequent chapters with a heightened comprehension of how these storage concepts intricately interplay within the dynamic EKS environment. This sets the stage for a nuanced understanding of the storage landscape within Elastic Kubernetes Service, enriching the overall EKS experience for users.

[Amazon Elastic Block Store](#contents.xhtml#sc2_266a)

Amazon Elastic Block Store (EBS) emerges as a robust solution offering block-level storage volumes, seamlessly attachable to Amazon EC2 instances. These volumes serve as the backbone for supporting a spectrum of workloads, ranging from transactional tasks with low-latency requirements for random IO to more data-intensive workloads demanding high throughput. The versatility of EBS positions it as a foundational component for ensuring the performance and persistence of data within the AWS ecosystem.

Among the key benefits that distinguish Amazon EBS is its provision of persistent block storage for EC2 instances. This persistence is complemented by low-latency access, a critical attribute for meeting the demands of real-time and mission-critical applications. EBS extends its appeal by offering options tailored to diverse needs, including general-purpose storage, provisioned Input/Output Operations Per Second (IOPS), and throughput-optimized storage, thereby catering to a wide range of application requirements.

In the context of EKS, achieving stateful applications often involves the utilization of StatefulSets, a specialized Kubernetes controller designed to manage the deployment and scaling of stateful applications. Unlike traditional pods, StatefulSets provide a level of predictability and stable network identities for each pod, which is crucial for applications requiring persistent storage and unique network identifiers. This section explores how StatefulSets can be effectively coupled with Amazon EBS to facilitate the deployment of stateful applications on EKS.

The combination of EBS and StatefulSets proves particularly potent when addressing use cases that demand persistent, reliable storage. As StatefulSets facilitate the management of stateful applications, EBS complements this by providing the necessary persistent block storage for data that persists across pod restarts and reschedules. This collaboration ensures that each pod within the StatefulSet has its dedicated, resilient storage volume, contributing to data persistence and reliability.

Consider a scenario where a stateful application, such as a database, requires a predictable and stable storage solution. In this case, a StatefulSet is employed to deploy multiple replicas of the database pods. Each pod within the StatefulSet is assigned a unique hostname, allowing for stable network identities even in dynamic environments like EKS. Concurrently, EBS volumes are dynamically provisioned and attached to each pod, ensuring that the data remains intact and accessible even if a pod is rescheduled or restarted.

The practical steps to be taken are as follows:

1.  Define StatefulSet YAML manifest (statefulset.yaml), as shown:
    
    apiVersion: apps/v1
    
    kind: StatefulSet
    
    metadata:
    
     name: mysql-statefulset
    
    spec:
    
     serviceName: "mysql"
    
     replicas: 3
    
     selector:
    
     matchLabels:
    
     app: mysql
    
     template:
    
     metadata:
    
     labels:
    
     app: mysql
    
     spec:
    
     containers:
    
     - name: mysql
    
     image: mysql:latest
    
     env:
    
     - name: MYSQL\_ROOT\_PASSWORD
    
     value: "your-root-password"
    
     ports:
    
     - containerPort: 3306
    
     volumeMounts:
    
     - name: mysql-persistent-storage
    
     mountPath: /var/lib/mysql
    
     volumeClaimTemplates:
    
     - metadata:
    
     name: mysql-persistent-storage
    
     spec:
    
     accessModes: \["ReadWriteOnce"\]
    
     storageClassName: "ebs-sc"
    
     resources:
    
     requests:
    
     storage: 10Gi
    
2.  Define StorageClass YAML manifest (storageclass.yaml) as follows:
    
    apiVersion: storage.k8s.io/v1
    
    kind: StorageClass
    
    metadata:
    
     name: ebs-sc
    
    provisioner: kubernetes.io/aws-ebs
    
    parameters:
    
     type: gp2
    
     encrypted: "true"
    
3.  Apply StorageClass manifest with the following command:
    
    kubectl apply -f storageclass.yaml
    
4.  Apply StatefulSet manifest with the following command:
    
    kubectl apply -f statefulset.yaml
    
5.  Verify deployment with the following command:
    
    kubectl get statefulsets,pods,pvc
    

This example deploys a MySQL stateful application using a StatefulSet with EBS as the storage backend. It dynamically provisions EBS volumes for each MySQL pod, ensuring data persistence even during pod restarts or rescheduling. The StorageClass specifies EBS as the provisioner, and the StatefulSet YAML manifest defines the PVCs and their associated storage requirements. Users can tailor the parameters according to their specific application and storage needs.

[EBS CSI driver](#contents.xhtml#sc3_267a)

The Amazon EBS Container Storage Interface (CSI) driver is an essential component for integrating EBS with Kubernetes clusters. It serves as a dynamic provisioner, allowing for seamless integration of EBS volumes into Kubernetes pods. Utilizing the EBS CSI driver simplifies the process of managing and attaching EBS volumes to Kubernetes workloads, providing a standardized and efficient approach. Let us expand on the previous example to showcase how to leverage the EBS CSI driver for dynamic provisioning in an EKS environment. The steps are as follows:

1.  Define StatefulSet YAML manifest (statefulset\_csi.yaml), as shown:
    
    apiVersion: apps/v1
    
    kind: StatefulSet
    
    metadata:
    
     name: mysql-statefulset-csi
    
    spec:
    
     serviceName: "mysql"
    
     replicas: 3
    
     selector:
    
     matchLabels:
    
     app: mysql
    
     template:
    
     metadata:
    
     labels:
    
     app: mysql
    
     spec:
    
     containers:
    
     - name: mysql
    
     image: mysql:latest
    
     env:
    
     - name: MYSQL\_ROOT\_PASSWORD
    
     value: "your-root-password"
    
     ports:
    
     - containerPort: 3306
    
     volumeMounts:
    
     - name: mysql-persistent-storage
    
     mountPath: /var/lib/mysql
    
     volumeClaimTemplates:
    
     - metadata:
    
     name: mysql-persistent-storage
    
     spec:
    
     accessModes: \["ReadWriteOnce"\]
    
     storageClassName: "ebs-sc-csi"
    
     resources:
    
     requests:
    
     storage: 10Gi
    
2.  Define StorageClass YAML manifest (storageclass\_csi.yaml) as follows:
    
    apiVersion: storage.k8s.io/v1
    
    kind: StorageClass
    
    metadata:
    
     name: ebs-sc-csi
    
    provisioner: ebs.csi.aws.com
    
3.  Apply StorageClass manifest with the following command:
    
    kubectl apply -f storageclass\_csi.yaml
    
4.  Apply StatefulSet manifest with the following command:
    
    kubectl apply -f statefulset\_csi.yaml
    
5.  Verify deployment with the following command:
    
    kubectl get statefulsets,pods,pvc
    

[Amazon Elastic File System](#contents.xhtml#sc2_268a)

Amazon Elastic File System (EFS) stands as a versatile and fully managed elastic Network File System (NFS) designed to seamlessly integrate with AWS cloud services and on-premises resources. Engineered for scalability, it effortlessly scales on demand to petabytes without disrupting applications, dynamically growing and shrinking to accommodate changing storage needs.

Among the notable benefits of Amazon EFS is its status as a fully managed service, significantly reducing administrative overhead. Its scalability on demand eliminates the need for meticulous capacity planning, offering a flexible storage solution that adapts to evolving requirements. Furthermore, EFS ensures Multi-Availability Zone (AZ) redundancy and durability, providing a robust and resilient storage foundation for diverse workloads. Users benefit from consistent sub-millisecond low-latency access, promoting optimal performance for applications with stringent latency requirements. Integrated access controls and encryption enhance security, and EFS adheres to POSIX file system access semantics, facilitating seamless integration with applications that rely on standard file system behaviors.

This section serves as a comprehensive guide on harnessing the capabilities of Amazon EFS. It walks through the process of creating EFS file systems and establishing connections between Elastic Kubernetes Service (EKS) pods, operating on both EC2 and Fargate, and EFS mounts. The example showcases the seamless integration between EKS and EFS, offering readers a practical and hands-on understanding of the concepts discussed.

[EFS CSI driver](#contents.xhtml#sc3_269a)

The Amazon EFS Container Storage Interface (CSI) driver serves as a crucial component for integrating EFS seamlessly with Kubernetes clusters, offering a dynamic and efficient approach to storage provisioning. The EFS CSI driver operates as a dynamic provisioner, enabling the automated and on-demand creation of EFS file systems directly within Kubernetes environments. This functionality streamlines the process of attaching EFS volumes to Kubernetes pods, facilitating a more straightforward and standardized approach to storage management.

The EFS CSI driver not only simplifies the provisioning of EFS volumes but also enhances the overall flexibility and functionality when dealing with persistent storage in Kubernetes. It enables users to leverage features such as access control and encryption seamlessly. By abstracting the complexities of EFS integration, the CSI driver ensures a consistent and reliable experience for users deploying stateful applications that require shared file storage. This abstraction shields users from the intricacies of EFS configuration, allowing them to focus more on the application logic rather than the underlying storage infrastructure.

In addition to dynamic provisioning, the EFS CSI driver supports other essential features such as volume resizing, snapshotting, and cloning. This versatility further enhances the capabilities of EFS within Kubernetes environments, providing users with a comprehensive toolkit for managing and optimizing their storage resources. The EFS CSI driver thus stands as a pivotal tool in the Kubernetes ecosystem, enabling users to seamlessly integrate EFS into their applications, delivering a reliable and scalable solution for persistent shared storage within Kubernetes clusters. The practical steps are as follows:

1.  Define StorageClass YAML manifest (efs-sc.yaml), as shown:
    
    apiVersion: storage.k8s.io/v1
    
    kind: StorageClass
    
    metadata:
    
     name: efs-sc
    
    provisioner: efs.csi.aws.com
    
2.  Apply StorageClass manifest with the following command:
    
    kubectl apply -f efs-sc.yaml
    
3.  Define PersistentVolumeClaim YAML manifest (efs-pvc.yaml) as follows:
    
    apiVersion: v1
    
    kind: PersistentVolumeClaim
    
    metadata:
    
     name: efs-pvc
    
    spec:
    
     accessModes:
    
     - ReadWriteMany
    
     storageClassName: efs-sc
    
     resources:
    
     requests:
    
     storage: 5Gi
    
4.  Apply PersistentVolumeClaim manifest with the following command:
    
    kubectl apply -f efs-pvc.yaml
    
5.  Define Pod YAML manifest (efs-pod.yaml), as shown:
    
    apiVersion: v1
    
    kind: Pod
    
    metadata:
    
     name: efs-pod
    
    spec:
    
     containers:
    
     - name: efs-container
    
     image: nginx
    
     volumeMounts:
    
     - name: efs-volume
    
     mountPath: /usr/share/nginx/html
    
     volumes:
    
     - name: efs-volume
    
     persistentVolumeClaim:
    
     claimName: efs-pvc
    
6.  Apply Pod manifest with the following command:
    
    kubectl apply -f efs-pod.yaml
    
7.  Verify deployment with the following command:
    
    kubectl get pods,pvc
    

In this practical example, the EFS CSI driver is utilized for dynamic provisioning of an EFS file system. The StorageClass (efs-sc.yaml) specifies the EFS CSI driver (efs.csi.aws.com) as the provisioner. A PersistentVolumeClaim (efs-pvc.yaml) is defined to request storage resources using the EFS-backed StorageClass. Finally, a Pod (efs-pod.yaml) is deployed, and the EFS volume is mounted to the pod's file system. The example offers a hands-on experience, showcasing the seamless integration between EKS pods and EFS using the EFS CSI driver.

[Amazon FSx for NetApp ONTAP](#contents.xhtml#sc2_270a)

Amazon FSx for NetApp ONTAP stands as a fully managed shared storage solution, leveraging NetApp's renowned ONTAP file system. This service provides an advanced and efficient storage infrastructure, offering a host of benefits such as high performance, redundancy, security, and ease of administration. With the capability to scale up to 64TB and deliver an impressive 100GBps throughput, FSx for NetApp ONTAP ensures the seamless management of shared storage for diverse workloads.

The key advantages of FSx for NetApp ONTAP are multifaceted. It delivers fully managed ONTAP shared storage, sparing users the administrative overhead associated with traditional storage solutions. The scalability of FSx for NetApp ONTAP, coupled with sub-millisecond latencies, ensures optimal performance for applications with stringent latency requirements. Additionally, features like data compression, deduplication, and encryption contribute to the efficiency and security of the storage solution. Supporting multiple access protocols, including NFS and SMB, FSx for NetApp ONTAP caters to a broad range of application requirements. Furthermore, the service offers application-consistent snapshots and data replication, enhancing data resilience and disaster recovery capabilities. The hands-on example walks users through the steps of defining a StorageClass, PersistentVolumeClaim, and a pod to demonstrate the seamless integration between FSx for NetApp ONTAP and EKS. The example is designed to provide a practical and tangible experience, allowing users to grasp the implementation nuances and considerations when utilizing FSx for NetApp ONTAP in conjunction with Kubernetes.

[FSxN CSI driver](#contents.xhtml#sc3_271a)

The Amazon FSx for NetApp ONTAP Container Storage Interface (CSI) driver is an instrumental component that bridges the gap between Kubernetes clusters and the fully managed shared storage solution provided by FSx for NetApp ONTAP. This CSI driver plays a pivotal role in enabling dynamic provisioning of ONTAP volumes within Kubernetes environments, facilitating seamless integration and efficient storage management. By abstracting the complexities of interacting with FSx for NetApp ONTAP, the CSI driver empowers users to effortlessly leverage the advanced capabilities of this shared storage solution within their Kubernetes workloads.

The FSx for NetApp ONTAP CSI driver offers a set of robust features that enhance the overall storage experience in Kubernetes clusters. It supports dynamic provisioning, allowing for the automated creation of ONTAP volumes based on user-defined specifications. This capability streamlines the storage lifecycle management process, enabling users to focus on application logic rather than the intricacies of storage provisioning. Moreover, the CSI driver facilitates the integration of ONTAP volumes into Kubernetes pods, ensuring a consistent and reliable experience for applications requiring shared file storage. Additionally, the driver supports essential functionalities such as volume expansion, snapshots, and cloning, providing users with a comprehensive toolkit to address diverse storage needs within their Kubernetes workloads. The result is a cohesive and efficient storage solution that seamlessly aligns with the dynamic nature of containerized applications in Kubernetes clusters. Let us look at a practical example of dynamic provisioning of ONTAP Volumes in EKS, as follows:

1.  Define StorageClass YAML manifest (ontap-sc.yaml), as shown:
    
    apiVersion: storage.k8s.io/v1
    
    kind: StorageClass
    
    metadata:
    
     name: ontap-sc
    
    provisioner: fsx.csi.aws.com
    
2.  Apply StorageClass manifest with the following command:
    
    kubectl apply -f ontap-sc.yaml
    
3.  Define PersistentVolumeClaim YAML manifest (ontap-pvc.yaml) as follows:
    
    apiVersion: v1
    
    kind: PersistentVolumeClaim
    
    metadata:
    
     name: ontap-pvc
    
    spec:
    
     accessModes:
    
     - ReadWriteOnce
    
     storageClassName: ontap-sc
    
     resources:
    
     requests:
    
     storage: 5Gi
    
4.  Apply PersistentVolumeClaim manifest with the following command:
    
    kubectl apply -f ontap-pvc.yaml
    
5.  Define Pod YAML manifest (ontap-pod.yaml) as follows:
    
    apiVersion: v1
    
    kind: Pod
    
    metadata:
    
     name: ontap-pod
    
    spec:
    
     containers:
    
     - name: ontap-container
    
     image: nginx
    
     volumeMounts:
    
     - name: ontap-volume
    
     mountPath: /usr/share/nginx/html
    
     volumes:
    
     - name: ontap-volume
    
     persistentVolumeClaim:
    
     claimName: ontap-pvc
    
6.  Apply the Pod manifest with the following command:
    
    kubectl apply -f ontap-pod.yaml
    
7.  Verify deployment with the following command:
    
    kubectl get pods,pvc
    

This practical example demonstrates the dynamic provisioning of ONTAP volumes within an EKS environment using the FSx for NetApp ONTAP CSI driver. The StorageClass (ontap-sc.yaml) specifies the CSI driver (fsx.csi.aws.com) as the provisioner. A PersistentVolumeClaim (ontap-pvc.yaml) is defined to request storage resources using the ONTAP-backed StorageClass. Finally, a Pod (ontap-pod.yaml) is deployed, and the ONTAP volume is mounted to the pod's file system. The example offers a hands-on experience, illustrating the seamless integration between EKS and FSx for NetApp ONTAP using the CSI driver for dynamic provisioning.

[Amazon Simple Storage Service](#contents.xhtml#sc2_272a)

Amazon Simple Storage Service (S3) stands as a highly scalable and durable object storage service, designed to store and retrieve any amount of data from anywhere on the web. Renowned for its simplicity, cost-effectiveness, and versatility, S3 provides a secure and reliable solution for storing and managing vast datasets. With features like automatic scaling, versioning, and comprehensive access controls, S3 is a cornerstone in many cloud-based architectures.

The S3 CSI driver serves as a crucial link between Kubernetes clusters and the powerful object storage capabilities of Amazon S3. This CSI driver enables seamless integration and dynamic provisioning of S3 buckets within Kubernetes environments. By abstracting the complexities of interacting with S3, the CSI driver empowers users to effortlessly leverage scalable and cost-effective object storage for their containerized applications.

The Amazon S3 CSI driver serves as a vital bridge between Kubernetes clusters and the versatile object storage capabilities offered by Amazon S3. This CSI driver is designed to facilitate seamless integration and dynamic provisioning of S3 buckets within Kubernetes environments, bringing the power and scalability of S3 directly to containerized applications. By abstracting the intricacies of interacting with S3, the CSI driver streamlines the process of utilizing cloud-native storage solutions, allowing users to effortlessly incorporate scalable and cost-effective object storage into their Kubernetes workloads.

The S3 CSI driver not only simplifies the provisioning of S3 buckets but also enhances the overall storage experience within Kubernetes clusters. It supports dynamic provisioning, enabling the automated creation of S3 buckets based on specified parameters. This capability simplifies storage lifecycle management, allowing users to focus on their application logic rather than dealing with the complexities of storage setup. Moreover, the CSI driver facilitates the seamless integration of S3 buckets into Kubernetes pods, providing a consistent and reliable experience for applications requiring object storage. With support for features like access controls, encryption, and versioning, the S3 CSI driver ensures that Kubernetes users can leverage the full capabilities of S3 without compromising on security or functionality. This adaptability makes it an essential tool for deploying cloud-native applications that demand scalable and durable object storage within Kubernetes clusters.

In a practical example showcasing the integration of S3 with EKS, users can dynamically provision S3 buckets using the S3 CSI driver. Let us go through the steps to set up and deploy a Kubernetes pod with a dynamically provisioned S3 volume in the following section:

1.  Define StorageClass YAML manifest (s3-sc.yaml), as shown:
    
    apiVersion: storage.k8s.io/v1
    
    kind: StorageClass
    
    metadata:
    
     name: s3-sc
    
    provisioner: s3.csi.aws.com
    
2.  Apply StorageClass manifest with the following command:
    
    kubectl apply -f s3-sc.yaml
    
3.  Define PersistentVolumeClaim YAML manifest (s3-pvc.yaml) as follows:
    
    apiVersion: v1
    
    kind: PersistentVolumeClaim
    
    metadata:
    
     name: s3-pvc
    
    spec:
    
     accessModes:
    
     - ReadWriteOnce
    
     storageClassName: s3-sc
    
     resources:
    
     requests:
    
     storage: 5Gi
    
4.  Apply PersistentVolumeClaim manifest with the following command:
    
    kubectl apply -f s3-pvc.yaml
    
5.  Define Pod YAML manifest (s3-pod.yaml), as shown:
    
    apiVersion: v1
    
    kind: Pod
    
    metadata:
    
     name: s3-pod
    
    spec:
    
     containers:
    
     - name: s3-container
    
     image: nginx
    
     volumeMounts:
    
     - name: s3-volume
    
     mountPath: /usr/share/nginx/html
    
     volumes:
    
     - name: s3-volume
    
     persistentVolumeClaim:
    
     claimName: s3-pvc
    
6.  Apply Pod manifest with the following command:
    
    kubectl apply -f s3-pod.yaml
    
7.  Verify deployment with the following command:
    
    kubectl get pods,pvc
    

In this example, the StorageClass (s3-sc.yaml) specifies the CSI driver (s3.csi.aws.com) as the provisioner. A PersistentVolumeClaim (s3-pvc.yaml) is defined to request storage resources using the S3-backed StorageClass. Finally, a pod (s3-pod.yaml) is deployed, and the dynamically provisioned S3 volume is mounted to the pod's file system. This hands-on example illustrates the seamless integration between EKS and S3 using the CSI driver for dynamic provisioning, showcasing the flexibility and simplicity of utilizing Amazon S3 as a storage backend for Kubernetes workloads.

[Amazon FSx for Lustre](#contents.xhtml#sc2_273a)

Amazon FSx for Lustre stands as a powerful and high-performance distributed file system tailored to meet the demands of complex workloads, including ML, high-performance computing (HPC), video processing, financial modeling, and more. The design philosophy of FSx for Lustre revolves around providing an efficient and scalable file system that can handle the intensive processing requirements of these diverse workloads.

A significant advantage of FSx for Lustre lies in its seamless integration with Amazon S3 data lakes. This integration enables users to effortlessly access and leverage the data stored in S3 directly within the FSx for Lustre file system. This feature is particularly advantageous for workflows that involve processing large datasets, as it allows for a cohesive and efficient data flow between storage and compute layers.

Scalability is a core tenet of FSx for Lustre, with the capability to scale up to hundreds of gigabytes per second (GBps) throughput, supporting millions of I/O operations per second (IOPS), and delivering sub-millisecond latencies. This ensures that the file system can handle the demanding performance requirements of advanced computational tasks, making it well-suited for applications that demand rapid data processing.

A notable feature is the dual accessibility of data, which can be accessed both from FSx for Lustre and directly from S3. This flexibility provides users with multiple avenues for interacting with their data, catering to a variety of use cases and application architectures. Moreover, FSx for Lustre operates as a fully managed service, relieving users of the burdens of file system administration. This hands-off approach allows organizations to focus on their core tasks without the overhead of managing and maintaining the underlying file system infrastructure.

FSx for Lustre employs SSD disks to deliver EBS-like persistent storage, ensuring high durability and low-latency access to data. This design choice makes it well-suited for applications that demand reliable and performant storage solutions. Additionally, FSx for Lustre seamlessly integrates with Virtual Private Cloud (VPC), providing a secure and isolated environment for the file system within the AWS ecosystem. This integration enhances data security and allows organizations to define and enforce access controls, further fortifying the overall security posture of their file system.

In essence, Amazon FSx for Lustre brings a versatile and high-performance file system to AWS, catering to the intricate demands of modern workloads and offering a myriad of benefits, from seamless data integration with S3 to robust scalability and fully managed operations.

[Architectural considerations and decision criteria](#contents.xhtml#sc2_274a)

When architecting storage solutions for Elastic Kubernetes Service (EKS), it is paramount to carefully consider various factors and decision criteria to align the chosen storage options with specific requirements, use cases, and trade-offs. This section serves as a comprehensive guide, systematically exploring the available storage options for EKS and offering decision criteria to aid in making informed choices.

[Performance needs](#contents.xhtml#sc3_275a)

One of the primary considerations is the performance requirements of the EKS workloads. Factors such as latency, Input/Output Operations Per Second (IOPS), and throughput play a crucial role in determining the suitability of different storage solutions. High-performance workloads, like those in machine learning or financial modeling, may demand low-latency access and high IOPS, influencing the choice of storage type.

[Scalability requirements](#contents.xhtml#sc3_276a)

Scalability is another key dimension that varies across different storage options. Capacity scalability, handling concurrent access, and accommodating the growth of workloads are critical aspects. EKS workloads with dynamic scaling demands may necessitate storage solutions that seamlessly scale in both capacity and concurrency to meet evolving requirements.

[Access patterns](#contents.xhtml#sc3_277a)

Understanding the access patterns of applications is fundamental to selecting the appropriate storage type. Whether the workload requires block-level access, file-based storage, or object storage, each has distinct advantages depending on the nature of the applications deployed in EKS. Tailoring the storage solution to match the specific access patterns optimizes performance and efficiency.

[Resiliency needs](#contents.xhtml#sc3_278a)

Ensuring the resiliency of storage solutions is crucial for maintaining the integrity and availability of EKS workloads. Considerations include redundancy mechanisms, backup, and disaster recovery strategies. Depending on the criticality of the data and applications, storage solutions must provide adequate resiliency features to safeguard against potential failures.

[Cost budgets](#contents.xhtml#sc3_279a)

Balancing the cost considerations is an essential aspect of storage decision-making. Understanding whether a pay-as-you-go model or a provisioned approach aligns with the budgetary constraints is pivotal. Cost implications should be evaluated in the context of usage patterns, ensuring that the chosen storage solution is both economical and aligned with performance expectations.

[Administration overhead](#contents.xhtml#sc3_280a)

The administrative burden associated with managing storage solutions cannot be overlooked. The complexity of setup, ongoing maintenance, and monitoring requirements may vary among different storage options. Minimizing administration overhead is critical to streamlining operations and ensuring efficient management of EKS workloads.

[Learning curves](#contents.xhtml#sc3_281a)

Considering the learning curves associated with different storage solutions is vital, especially in environments where expertise varies. Solutions with simpler configurations and more straightforward management interfaces might be preferable, particularly for teams with diverse skill levels.

[Application architectures](#contents.xhtml#sc3_282a)

Finally, aligning storage choices with the overall architecture of EKS applications is imperative. Different workloads, such as microservices-based applications or data-intensive analytics, may have unique storage requirements. Tailoring storage solutions to fit seamlessly within the broader application architecture enhances overall performance and reliability.

[Conclusion](#contents.xhtml#sc2_283a)

In conclusion, the integration of the right storage systems with Amazon EKS is pivotal for achieving production-grade application deployments. Throughout this chapter, we have meticulously explored the landscape of managed storage services on AWS that are purpose-built to seamlessly collaborate with EKS across a diverse range of workloads. The insights gained from this exploration empower readers with foundational understanding and actionable knowledge to make informed decisions in the realm of Kubernetes storage.

Key takeaways from the section encompass a foundational grasp of Kubernetes storage concepts, presenting options for block storage, shared filesystems, and S3 object access. By understanding these options, readers are better equipped to match specific use cases with the most fitting storage service, ensuring an optimal fit for their application's requirements. The section has also delved into the intricacies of architecting composite storage blueprints based on specified criteria, providing a holistic approach to storage design within the EKS ecosystem.

Moreover, the exploration extends to provisioning and lifecycle management integrations, offering practical guidance on not just choosing the right storage solution but also implementing and managing it effectively. Armed with this knowledge, readers can confidently navigate the myriad choices available for providing essential attributes like data persistence, shareability, redundancy, and resiliency for stateful applications on Amazon EKS.

In essence, this chapter serves as a valuable resource for anyone seeking a comprehensive understanding of storage considerations within the Amazon EKS environment. By synthesizing complex concepts into practical takeaways, it empowers readers to make well-informed decisions that are aligned with the specific requirements of their applications, ultimately contributing to the success of their Amazon EKS deployments.

In the next chapter, we will discuss the various options to monitor your EKS clusters.

[Questions](#contents.xhtml#sc2_284a)

1.  Explain Kubernetes Volumes vs. Persistent Volumes vs Storage Classes. What problems do they each solve?
    
2.  What are the access semantics of block storage vs file storage vs object storage? What use cases are they optimized for?
    
3.  What are some key differences between EBS and EFS storage systems on AWS? When would you choose one over the other?
    
4.  Amazon FSx provides managed file systems including ONTAP and Lustre. What are benefits of each? What use cases do they serve?
    
5.  Describe how to architect storage for a large-scale ML training workload on Amazon EKS. What storage system would you choose and why?
    

[Exercises](#contents.xhtml#sc2_285a)

1.  Provision a simple stateful application using Amazon EBS volumes dynamically provisioned via storage classes.
    
2.  Create an EFS file system accessed by pods spread across multiple EKS worker node AZs.
    
3.  Deploy a shared home directory for users using Amazon FSx for NetApp ONTAP accessed from EKS worker nodes.
    

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 15Monitoring AWS EKS Clusters](#contents.xhtml#ch15a)

[Introduction](#contents.xhtml#sc2_286a)

Monitoring Amazon EKS clusters is crucial for optimizing the performance, resource use, and cost-effectiveness of Kubernetes workloads. AWS provides native tools that integrate with Amazon EKS, giving administrators and DevOps teams valuable insights. The AWS Management Console for Amazon EKS offers a centralized hub for visualizing metrics and tracking cluster health, allowing users to make informed decisions based on real-time data. CloudWatch Container Insights is a powerful monitoring solution designed specifically for containerized environments, including Amazon EKS. It collects, aggregates, and analyzes performance metrics, logs, and traces from containers running within EKS clusters. This granular visibility enables users to troubleshoot issues and set up automated alerts for proactive problem-solving.

The following figure shows the EKS monitoring with control and data plane components:

![](images/Figure_15.1.png)

Figure 15.1: EKS monitoring with control and data plane components

Cost management is also essential for EKS clusters. Kubecost integrates with Amazon EKS to track resource consumption at cluster and workload levels, enabling informed decision-making on resource allocation and cost optimization. By leveraging these tools, users can gain deep insights into their Kubernetes workloads, identify trends, and optimize cluster efficiency, leading to enhanced availability and effective cost management.

[Structure](#contents.xhtml#sc2_287a)

This chapter covers the following topics:

*   Overview of monitoring options for Amazon EKS clusters
*   AWS console EKS monitoring
*   Container Insights
*   Cost management with Kubecost

[Objectives](#contents.xhtml#sc2_288a)

Upon completing this chapter, you will possess a comprehensive understanding of the native monitoring tools tailored for Amazon EKS within the AWS ecosystem. This knowledge will empower you to adeptly navigate and leverage AWS console dashboards, providing high-level overviews of your EKS clusters' performance and health. Additionally, you will have the capability to enable and interpret detailed Container Insights performance metrics, ensuring a nuanced understanding of containerized workloads. Furthermore, the chapter equips you with the skills to gain visibility into Kubernetes resource costs through Kubecost, enabling effective cost management strategies. Armed with this knowledge, you will be well-prepared to implement an integrated monitoring stack, seamlessly combining these AWS-native tools for comprehensive observability and optimized operational efficiency within your Amazon EKS environment.

EKS cluster monitoring using Container Insights and Kubecost provides valuable benefits for managing Kubernetes environments. It offers enhanced visibility into container performance and resource utilization, enabling teams to quickly identify and resolve issues. The detailed cost breakdowns help optimize expenses and improve budget allocation. Additionally, these tools facilitate better capacity planning and resource management, ensuring efficient cluster operations. Together, they empower teams to maintain healthier, more cost-effective Kubernetes deployments on AWS.

[Overview of monitoring options](#contents.xhtml#sc2_289a)

AWS offers a robust suite of purpose-built tools designed to address the intricacies of monitoring Amazon EKS environments comprehensively, spanning various levels of infrastructure, clusters, and individual workloads. The AWS Console Monitoring feature provides a user-friendly interface for obtaining high-level resource views and receiving real-time status alerts. This functionality empowers users with a quick and intuitive assessment of the overall health and performance of their EKS clusters, facilitating prompt responses to potential issues.

For a more granular understanding of containerized workloads, AWS provides Container Insights, a tool that goes beyond surface-level monitoring. It furnishes in-depth performance metrics and logs, allowing administrators and DevOps teams to troubleshoot and optimize containerized applications effectively. Container Insights offers a holistic view of container health, resource utilization, and application performance, enabling informed decision-making for enhanced operational efficiency.

Kubecost adds another layer of sophistication by providing comprehensive cost visibility, encompassing both actual and projected spending on Kubernetes resources. This tool enables users to manage and optimize costs effectively, ensuring that resource allocation aligns with budgetary constraints and strategic objectives.

[AWS console EKS monitoring](#contents.xhtml#sc2_290a)

AWS console EKS monitoring serves as a centralized hub for administrators and DevOps teams to gain critical insights into the health and performance of their Amazon EKS clusters. This native monitoring tool offers an intuitive and user-friendly interface, allowing users to effortlessly navigate through high-level resource views and receive real-time status alerts. Through the console, users can track key metrics, assess cluster health, and promptly respond to potential issues, ensuring the continuous availability of their Kubernetes workloads. The AWS Console EKS Monitoring feature provides a seamless experience for visualizing data, facilitating quick decision-making, and enhancing overall operational efficiency within the Amazon EKS environment.

When you log into the AWS EKS console, you will be presented with various tabs. Get started with Resources tab. This has various resource types, as shown in the following figure:

![](images/Figure_15.2.png)

Figure 15.2: EKS cluster resources view

When you get into Workloads, you can see the Pod information as shown in the following figure:

![](images/Figure_15.3.png)

Figure 15.3: EKS cluster resources – Pods view

Also, you should be able to see the replica sets, as shown in the following figure:

![](images/Figure_15.4.png)

Figure 15.4: EKS cluster resources – ReplicaSets view

The following figure shows the coredns deployment view:

![](images/Figure_15.5.png)

Figure 15.5: EKS cluster resources – Deployments view

If you have any stateful sets, HPAs or jobs you could be able to monitor as well. Also, it will show the various daemonsets as follows:

![](images/Figure_15.6.png)

Figure 15.6: EKS cluster resources – Daemonsets view

Under Cluster, you can monitor the node information. The following figure shows the two t3.medium nodes that are running in the EKS cluster:

![](images/Figure_15.7.png)

Figure 15.7: EKS cluster resources – Nodes view

You can also monitor the Namespaces information. This also has the details about leases, APIServices, etc., as shown in the following figure:

![](images/Figure_15.8.png)

Figure 15.8: EKS cluster resources – Namespaces view

Under the Services tab, you can see the various services. This one also has the details about Ingress, Endpoints, EndpointSlices, etc. Here, the various services that are running in the cluster are seen like kube-dns and Kubernetes services (refer to the following figure):

![](images/Figure_15.9.png)

Figure 15.9: EKS cluster resources – Services view

Under the Config and Secrets section, you can view the config Maps and Secrets as follows. As you can see from the following figure, there are various config Maps running in the cluster, such as the VPC CNI config map as well as the aws-auth configmap:

![](images/Figure_15.10.png)

Figure 15.10: EKS cluster resources – ConfigMaps view

Under the Storage section, you can check various information, including but not limited to PV, PVCs, Storage Classes, CSI drivers etc. In the following figure, it shows the gp2 storage class which is running in the cluster:

![](images/Figure_15.11.png)

Figure 15.11: EKS cluster resources – StorageClasses view

As well as the EFS CSI driver as follows. The following figure shows the EFS CSI driver with the name efs.csi.aws.com running in the cluster:

![](images/Figure_15.12.png)

Figure 15.12: EKS cluster resources- CSIDrivers view

Under Authentication section, you can track the service account details, as shown in the following figure. Service accounts provide the guardrails for the various resources running. The following figure shows the various service accounts running in the clusters. Some of the notable are the aws-node service account, aws-cloud-provider service account etc:

![](images/Figure_15.13.png)

Figure 15.13: EKS cluster resources – ServiceAccounts view

Authorization has details related to Cluster roles, Cluster role bindings, roles and role bindings. Cluster roles are applicable for the entire cluster, whilst roles are applicable only in the namespace in which it was created. The following figure shows the various cluster roles created, such as admin, cluster-admin, aws-node, etc:

![](images/Figure_15.14.png)

Figure 15.14: EKS cluster resources – Cluster roles view

The next section, Policy, tracks the limit ranges, resource quotas, network policies, and Pod Disruption Budgets (PDB). Amazon EKS PDBs are Kubernetes objects that limit the number of pods that can be unavailable during voluntary disruptions. They help maintain application availability by ensuring a minimum number of replicas remain running during cluster operations like node drains or updates (refer to the following figure):

![](images/Figure_15.15.png)

Figure 15.15: EKS cluster resources – PDBs view

Finally, the Extensions section tracks the custom resource definitions (CRDs) and various webhook configurations, as shown in the following figure. CRDs in Amazon EKS allow users to extend Kubernetes API with custom resources tailored to their specific needs. CRDs enable the creation of custom objects that can be managed like native Kubernetes resources, facilitating the implementation of complex, application-specific workflows and configurations within EKS clusters:

![](images/Figure_15.16.png)

Figure 15.16: EKS cluster resources – CRDs view

[Container Insights](#contents.xhtml#sc2_291a)

Container Insights stands out as Amazon's fully managed monitoring and observability service, tailored specifically for containerized applications and Kubernetes clusters within the AWS ecosystem. This comprehensive tool offers immediate visibility into crucial infrastructure telemetry metrics such as CPU, memory, network, and disk usage for clusters, services, and pods. With the recent introduction of Container Insights with enhanced observability for Amazon EKS, this service now extends its capabilities to provide additional telemetry data from Kubernetes control plane components like the API server and etcd. Furthermore, it includes granular per-pod, per-container, and kube-state metrics, enhancing troubleshooting capabilities and enabling quicker problem isolation. The key benefits of Container Insights are manifold. It offers a holistic view of Kubernetes cluster health and real-time state, allowing users to swiftly detect issues. Users can visually drill down across cluster layers to identify specific concerns, such as memory leaks in individual containers, facilitating faster and more targeted troubleshooting. The service empowers proactive risk identification even before alarms are set up, mitigating potential problems and preventing issues that could adversely impact end-user experience.

Once Container Insights is enabled, users can leverage the overview page in the AWS console to access a high-level summary of their Kubernetes clusters. This page displays kube-state and control-plane metrics for monitoring overall cluster health. The Container Insights dashboard complements this by visualizing cluster status and alarms, utilizing predefined thresholds for CPU and memory utilization. This intuitive approach enables users to swiftly identify resource-intensive components, empowering them to take proactive measures to avoid performance impacts and ensure the seamless operation of their containerized applications within Amazon EKS.

The following figure shows a CloudWatch Container Insights dashboard for Amazon EKS. The left side displays a cluster state summary with twenty-one clusters represented by hexagons, color-coded to indicate their status (ten OK, two high utilization, and nine low utilization). On the right, there are performance summaries showing cluster CPU and memory utilization, pod and node counts, and control plane metrics, including API server requests and latency. Please refer to the following figure:

![](images/Figure_15.17.png)

Figure 15.17: EKS Container Insights Dashboard view

Container Insights surfaces the top ten resource consumption lists at multiple levels: Cluster, Node, Pod, Workload, and Container. These highlight the heaviest users to enable proactive risk identification without alarms. Checking the leading resource consumers allows you to get ahead of emerging issues before end user impact. Container Insights provides easy visibility into critical focus areas to prevent problems.

The following figure shows two graphs comparing CPU and Memory Utilization for the top three clusters over the last three hours. The left graph displays CPU utilization, with prodstaging showing significant spikes up to 60-70%. The right graph shows memory utilization, where all three clusters maintain relatively stable usage, around 40-50%, with prodstaging showing a brief spike. A red dotted line at 80% indicates the threshold for high utilization on both graphs:

![](images/Figure_15.18.png)

Figure 15.18: EKS container insights top contributors view

The cluster overview is prioritized by criticality. Alarmed clusters surface first, followed by top resource consumers. This enables users to quickly focus on clusters needing attention. The sortable list view allows clusters to be filtered based on specific needs. The following figure shows a Clusters Overview table for three EKS clusters. The table displays information for each cluster, including its name, state, last state update time, maximum CPU usage, and maximum memory usage. The prodcatalog cluster shows as OK with the most recent update and highest resource utilization (61% CPU, 57% memory), while genaieks and oam clusters have no alarms detected and lower resource usage, as shown in the following figure:

![](images/Figure_15.19.png)

Figure 15.19: EKS Container Insights Clusters overview view

The prodcatalog cluster exceeds 50% utilization. Clicking the name opens performance monitoring dashboards with an overview and drill-down views from cluster-wide to nodes to pods to containers to methodically isolate the root causes. The following figure displays the CloudWatch Container Insights Performance monitoring dashboard for the prodcatalog EKS cluster. It shows a cluster summary with six ready nodes, no container restarts, 3.22% node CPU utilization, and 49% node memory utilization. The bottom graphs illustrate pod CPU and memory utilization over time, with recent spikes in both metrics. The left sidebar lists various performance dashboard views, all showing no alarms detected. Please refer to the following figure:

![](images/Figure_15.20.png)

Figure 15.20: EKS Container Insights Performance monitoring view

As you can see in the following figure, it looks like the CPU and memory utilization at the node level max spikes almost 60%. The following figure shows the Nodes Performance dashboard in CloudWatch Container Insights for an EKS cluster. It displays four graphs: Node CPU Utilization with a recent spike to about 60%, Node Memory Utilization hovering around 40-50%, Filesystem Utilization at about 6%, and Node Network Total Bytes with occasional spikes. The left sidebar indicates no alarms are detected across various performance dashboard views. Please refer to the following figure:

![](images/Figure_15.21.png)

Figure 15.21: EKS Container Insights Clusters view

Container Insights provides drill-down dashboards from cluster to node to pod to container levels. This enables isolating root causes by analyzing telemetry data from different dimensions. The containers view revealed that a fluent-bit container peaked at 77% CPU utilization. Drilling down auto-populates related filters to quickly spot risks to neighboring components on that node. Nested views and automatic filtering streamline troubleshooting containerized workloads. Container Insights delivers visibility from high-level monitoring to granular pod and container metrics to optimize performance. The following figure shows the container view for the EKS cluster:

![](images/Figure_15.22.png)

Figure 15.22: EKS cluster container insights containers view

Node Performance dashboard view includes per node running pods, CPU and memory utilization etc. If you are interested to know more about the specific instance, you could use the filters to achieve the same. The following figure shows the various nodes running in the cluster. As you can see, there are six nodes running with varying pods. The following figure also shows the CPU, memory, and filesystem utilization in the nodes:

![](images/Figure_15.23.png)

Figure 15.23: EKS cluster container insights nodes view

The service dashboard view in Container Insights provides metrics for CPU, memory, and network performance of the pods of your Kubernetes service. With these insights, you can better optimize resource utilization and troubleshoot problems with your containerized services. The following figure shows the various services running in the cluster and their utilization in terms of CPU, memory, network, etc:

![](images/Figure_15.24.png)

Figure 15.24: EKS container insights services view

[Cost management with Kubecost](#contents.xhtml#sc2_292a)

Kubecost plays a pivotal role in addressing the inherent challenges of cost management within Kubernetes environments, particularly for those adopting Amazon EKS or ECS. The dynamic nature of containerized applications, characterized by ephemeral scaling and varying resource demands, necessitates a robust cost visibility solution. Kubecost efficiently tackles this complexity by leveraging Kubernetes APIs to query resource usage data, enabling the revelation of spend patterns and efficiency insights. This approach allows organizations to gain a comprehensive understanding of their Kubernetes spending, facilitating informed decision-making for resource optimization and cost control.

Available on the AWS Marketplace, this integration ensures a seamless experience for users, offering a familiar environment for data analysis and visualization. The combination of Prometheus and Grafana provides a powerful foundation for Kubecost to deliver actionable insights into container costs, enabling users to track spending trends, identify resource-intensive components, and implement cost-saving measures effectively, as shown in the following figure:

![](images/Figure_15.25.png)

Figure 15.25: EKS cost management with Kubecost architecture flow

Kubecost's ability to unlock container cost control is particularly valuable in the context of Kubernetes adoption within AWS environments. By providing transparency into the financial aspects of containerized workloads, Kubecost empowers organizations to optimize resource allocation, align spending with budgetary constraints, and achieve overall operational efficiency. This cost visibility is essential for organizations leveraging EKS, ensuring that they can effectively manage and control their container-related expenses while enjoying the benefits of scalable and dynamic containerized applications. Now Kubecost is available as an EKS addon and you can deploy through the following step:

aws eks create-addon --addon-name kubecost\_kubecost --cluster-name $YOUR\_CLUSTER\_NAME --region $AWS\_REGION

Once enabled, you should be able to view them as follows:

$kubectl get deployment -n kubecost

kubecost-cost-analyzer 1/1 1 1 16m

kubecost-kube-state-metrics 1/1 1 1 16m

kubecost-prometheus-server 1/1 1 1 16m

You can get the Kubecost monitoring endpoint as follows:

kubectl get service -n kubecost kubecost-cost-analyzer \\

 -o jsonpath="{.status.loadBalancer.ingress\[\*\].hostname}:9090{'\\n'}"

If you paste the URL from the above command output, you might see something as shown in the following figure:

![](images/Figure_15.26.png)

Figure 15.26: EKS cost management with Kubecost dashboard view

The cost allocation shows the details with sub menu view. As you can see in the following figure, the allocation view shows the aggregation in terms of namespaces:

![](images/Figure_15.27.png)

Figure 15.27: EKS cost management with Kubecost namespaces allocation view

The following figure shows the various filters to perform the aggregation. There are both single aggregation as well as multi aggregation options available:

![](images/Figure_15.28.png)

Figure 15.28: EKS cost management with Kubecost aggregation view

You should be able to aggregate with various dimensions. The following figure shows the aggregation by namespace, deployment, and pod level:

![](images/Figure_15.29.png)

Figure 15.29: EKS cost management with Kubecost deployment view

The following figure shows the cumulative cost for the last seven days by namespace, which is a single aggregation. This is useful information to see by namespace when you are running per workload by namespace:

![](images/Figure_15.30.png)

Figure 15.30: EKS cost management with Kubecost namespaces view

If you are looking for savings opportunities, this helps as well. The following screenshot shows the estimated monthly savings over $252, by varying means like right sizing cluster nodes, by using reserved instances, etc. Please refer to the following figure:

![](images/Figure_15.31.png)

Figure 15.31: EKS cost management with Kubecost savings view

Also, Kubecost captures the health of the cluster components as well. The following figure shows the overall health score of 97, which is pretty good. Additionally, there are various statuses of individual components like compute pressure, crash looping pods, nodes facing Process ID (PID) pressure, etc. This color coding of various components provides an easy way to track the health of the system, as shown:

![](images/Figure_15.32.png)

Figure 15.32: EKS cost management with Kubecost health view

[Conclusion](#contents.xhtml#sc2_293a)

This chapter underscores the efficiency and power of AWS's native monitoring solutions for Amazon EKS, offering a seamless monitoring experience through console dashboards, Container Insights, and Kubecost cost management. By adhering to best practices for enabling these tools, users can achieve comprehensive observability across various dimensions, including cluster health, node resource utilization, workload performance, and the associated hourly and monthly spend. Leveraging the console's data visualizations, users can swiftly surface actionable insights, facilitating quick decision-making and proactive responses to potential issues. It is crucial to align monitoring priorities with the specific needs of applications and environments. The native AWS toolset, comprising console dashboards, Container Insights, and Kubecost, provides a solid foundation for monitoring, but organizations can enhance their capabilities by integrating third-party solutions like Prometheus and Grafana. This supplementation offers additional metrics and flexibility, enabling users to tailor their monitoring approach to meet specific requirements.

Proactive instrumentation of Amazon EKS with logging and metrics is emphasized as a key practice in this section. This approach ensures the visibility required to operate clusters with reliability, security, and cost efficiency. By consistently monitoring and collecting data on cluster performance, resource utilization, and spending patterns, organizations can preemptively address issues, enhance security measures, and optimize costs, ultimately fostering a robust and well-managed Amazon EKS environment.

[Questions](#contents.xhtml#sc2_294a)

1.  What high-level visibility does the AWS console provide for EKS?
2.  How does Container Insights extend monitoring capabilities?
3.  What unique value does Kubecost offer over native tools?
4.  What best practices should section effective instrumentation?
5.  How can integrating tools enable a comprehensive view?

[Exercises](#contents.xhtml#sc2_295a)

1.  Explore an EKS console dashboard and enable performance metrics in Container Insights.
2.  Import the Kubecost EKS add-on and analyze daily cost savings from right-sizing.
3.  Research a third-party tool that augments AWS native capabilities.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 16Logging and Troubleshooting AWS EKS Clusters](#contents.xhtml#ch16a)

[Introduction](#contents.xhtml#sc2_296a)

In the dynamic landscape of Kubernetes clusters hosted on Amazon EKS, robust logging, and effective troubleshooting practices stand as indispensable pillars for guaranteeing the overall reliability, security, and optimal performance of containerized applications. This comprehensive section offers multifaceted insights into key aspects of cluster management. It meticulously addresses the significance of EKS control plane logging, demonstrating how administrators can gain a comprehensive understanding of their cluster's operations by enabling and strategically leveraging CloudWatch Logs Insights for advanced log analytics. Furthermore, the chapter delves into the intricacies of Kubernetes native logging architecture, aligning with best practices to ensure logs are appropriately directed to stdout and stderr in accordance with the Twelve-Factor App manifesto. The guidance extends to troubleshooting, providing a systematic approach to identifying and resolving common issues related to nodes, pods, networking, authentication, and more.

By emphasizing these critical elements, the chapter empowers EKS cluster administrators and DevOps teams to navigate the complexities inherent in containerized environments. It equips them with the knowledge and tools needed to proactively manage and maintain their Kubernetes clusters, fostering a robust and resilient infrastructure that meets the stringent demands of modern cloud-native applications. In summary, this chapter serves as a comprehensive resource, not only highlighting the importance of logging and troubleshooting in the context of EKS clusters but also providing practical guidance that aligns with industry best practices, ultimately contributing to the overarching goals of reliability, security, and performance within the Amazon EKS ecosystem.

[Structure](#contents.xhtml#sc2_297a)

In this chapter, we will cover the following topics:

*   EKS control plane logging
*   CloudWatch Log Insights
*   Logging components
*   EKS troubleshooting

[Objectives](#contents.xhtml#sc2_298a)

This chapter provides a comprehensive exploration of key aspects in managing Amazon EKS clusters, guiding users through crucial steps to enhance operational efficiency. First and foremost, it elucidates the significance of EKS control plane logging, offering insights into API server activities and cluster-wide events. The chapter walks users through the process of enabling this logging, ensuring administrators have a robust foundation for monitoring and troubleshooting. Additionally, the chapter introduces the usage of CloudWatch Logs Insights, empowering users with interactive analysis tools to navigate and derive meaningful insights from logs. Delving deeper into the intricacies of Kubernetes, the chapter explores the multi-tiered logging architecture, aligning with best practices for optimal cluster observability. Lastly, the chapter equips users with essential skills to diagnose and troubleshoot common issues, encompassing nodes, pods, networking, permissions, and the control plane. By providing a holistic approach to EKS management, this chapter serves as a valuable resource for administrators and DevOps teams seeking to optimize the reliability and performance of their Kubernetes clusters on Amazon EKS.

[EKS control plane logging](#contents.xhtml#sc2_299a)

One critical aspect of managing Kubernetes clusters is monitoring and logging, which plays a crucial role in ensuring the security, reliability, and performance of your applications. In this regard, Amazon EKS offers a comprehensive control plane logging feature, providing audit and diagnostic logs directly from the EKS control plane to CloudWatch Logs in your AWS account. Enabling control plane logging in Amazon EKS is a straightforward process, offering flexibility in selecting the exact log types needed for a particular cluster. Users can customize their logging configuration on a per-cluster basis using various methods, including the AWS Management Console, AWS CLI (version 1.16.139 or higher), or through the Amazon EKS API. This flexibility allows users to tailor their logging strategy to meet specific security and operational requirements.

While leveraging Amazon EKS control plane logging, it is essential to be aware of the associated costs. Standard Amazon EKS pricing applies to each cluster, and users will incur standard CloudWatch Logs data ingestion and storage costs for logs sent to CloudWatch from their clusters. Understanding the cost implications ensures effective budgeting and resource allocation for organizations utilizing Amazon EKS at scale.

Amazon EKS provides several log types, each corresponding to a specific component of the Kubernetes control plane. This segmentation allows for a granular approach to logging, enhancing the ability to troubleshoot and analyze different aspects of cluster behavior. The available log types are as follows:

*   Kubernetes API server component logs (api): This log type pertains to the control plane component responsible for exposing the Kubernetes API. Monitoring these logs is crucial for understanding API server activities and interactions with the cluster.
*   Audit logs (audit): Kubernetes audit logs offer a comprehensive record of individual users, administrators, or system components that have affected the cluster. These logs play a vital role in security and compliance by providing an audit trail of cluster activity.
*   Authenticator logs (authenticator): Unique to Amazon EKS, these logs represent the control plane component used for Kubernetes RBAC authentication using AWS IAM credentials. Monitoring authenticator logs is essential for tracking access and ensuring secure authentication within the cluster.
*   Controller manager logs (controllerManager): The controller manager is responsible for managing core control loops within Kubernetes. Monitoring these logs allows operators to gain insights into the functioning of controllers and their impact on the overall cluster state.
*   Scheduler logs (scheduler): The scheduler component determines when and where to run pods in the cluster. Analyzing scheduler logs provides valuable information about pod scheduling decisions, aiding in optimization and resource allocation.

To fully harness the advantages of Amazon EKS control plane logging, adherence to best practices is paramount. Regular and proactive review and analysis of logs form the cornerstone of a robust monitoring strategy. By routinely scrutinizing logs, operators can swiftly identify and address potential issues before they escalate, ensuring the continuous health and security of their Kubernetes clusters. Moreover, customizing logging configurations according to specific security and compliance requirements enhances the precision and relevance of the log data, tailoring it to the unique operational context. In addition to customization, the implementation of automated alerting mechanisms based on log analysis plays a pivotal role in maintaining a responsive and resilient infrastructure. By setting up alerts triggered by predefined patterns or anomalies within the logs, organizations can receive timely notifications of critical events. This proactive approach enables swift intervention, reducing downtime and minimizing the impact of potential issues on the overall system performance. Furthermore, the strategic leveraging of log data extends beyond mere issue detection, it becomes an asset for performance optimization and capacity planning. Analyzing historical log data allows organizations to gain insights into usage patterns, resource utilization, and potential bottlenecks, facilitating informed decision-making and proactive adjustments to meet evolving operational demands. In essence, the best practices outlined form a holistic approach to maximize the utility of Amazon EKS control plane logging, ensuring a resilient and optimized Kubernetes environment on the AWS platform.

Enabling Amazon EKS control plane logs on a per-cluster basis is a crucial step in establishing a comprehensive monitoring and diagnostic framework for Kubernetes clusters. This process is typically executed through the EKS API, allowing users to customize logging configurations based on their specific operational requirements. While infrastructure-as-code tools like Terraform or CloudFormation are commonly employed for this purpose, the AWS Command Line Interface (CLI) offers a straightforward and accessible method to enable this functionality. The AWS CLI provides a command-line interface for interacting with various AWS services, offering a convenient way to configure and manage resources. To enable EKS control plane logs, users can utilize the update-cluster-config command, specifying the desired log types and their respective settings. This approach allows for quick and efficient integration of logging capabilities without the need for extensive script development or configuration file management.

Utilizing the AWS CLI for enabling EKS control plane logs is particularly advantageous in scenarios where immediate action is required or for users who prefer a more interactive and command-driven approach to resource management. The process begins by authenticating with AWS credentials using the aws configure command, ensuring that the necessary permissions are granted to modify EKS cluster configurations. Once authenticated, the eks update-cluster-config command is employed, allowing users to modify the logging configurations on a per-cluster basis. This involves specifying parameters such as the log types to enable (e.g., api, audit, authenticator, controllerManager, scheduler), determining the destination CloudWatch Logs group, and configuring other relevant settings. For example, to enable EKS control plane logs, the following AWS CLI command can be utilized:

aws eks update-cluster-config --name <cluster-name> --logging '{"clusterLogging":\[{"types":\["api","audit","authenticator",  
"controllerManager","scheduler"\],"enabled":true}\]}'

This command effectively communicates with the EKS API, updating the cluster configuration to enable the specified log types. The provided JSON structure allows for a clear and concise representation of the logging settings, facilitating ease of modification and integration into automated deployment pipelines. Whether used in conjunction with infrastructure-as-code tools or as a standalone solution, the AWS CLI streamlines the process, allowing users to swiftly configure and adapt logging settings to meet the dynamic demands of their containerized applications on Amazon EKS. Let us look at this configuration in the EKS console.

The Observability tab shows the current configuration for control plane logs for the cluster, as shown:

![](images/Figure_16.1.png)

Figure 16.1: EKS console control plane logging

You can alter the logging configuration by clicking the Manage button, as shown:

![](images/Figure_16.2.png)

Figure 16.2: Enable EKS console control plane logging

Let us look at the logs in the CloudWatch Logs console. Filter for /aws/eks prefix and select the cluster you want to verify the logs, as shown:

![](images/Figure_16.3.png)

Figure 16.3: AWS CloudWatch log group

You will be presented with log streams in the group, as shown:

![](images/Figure_16.4.png)

Figure 16.4: AWS CloudWatch cluster log streams

You can select any of these log streams to view the entries being sent to CloudWatch Logs by the EKS control plane.

[CloudWatch Log Insights](#contents.xhtml#sc2_300a)

CloudWatch Logs Insights, a feature within the broader CloudWatch Logs service, stands as a powerful tool for interactively searching and analyzing log data, providing organizations with a sophisticated means to respond to operational challenges efficiently and effectively. This tool becomes indispensable when troubleshooting issues within AWS environments, offering a comprehensive solution for identifying root causes, validating deployed fixes, and gaining valuable insights from log data. At its core, CloudWatch Logs Insights facilitates a dynamic and interactive approach to log analysis. Its user-friendly interface allows operators to craft and execute queries seamlessly, enabling them to sift through vast amounts of log data with precision. This interactive search capability is particularly valuable during critical incidents or when investigating performance anomalies, providing a real-time window into the behavior of systems and applications.

The feature empowers users with purpose-built query language that is designed to be both simple and powerful. Leveraging this language, operators can construct queries using a few intuitive commands, making it accessible to users with varying levels of expertise in log analysis. Whether pinpointing specific error messages, tracking the execution of critical processes, or investigating user interactions, CloudWatch Logs Insights enables users to tailor their queries to the unique characteristics of their log data. In the event of an operational issue, CloudWatch Logs Insights becomes a go-to resource for incident response. By executing targeted queries, operators can swiftly identify potential causes, facilitating a faster and more accurate resolution process. The ability to explore log data interactively enhances the troubleshooting experience, enabling users to navigate through logs in a flexible and iterative manner, refining queries based on the evolving understanding of the issue.

Moreover, CloudWatch Logs Insights plays a pivotal role in the post-incident analysis phase. After deploying fixes or updates, operators can use the tool to validate the effectiveness of the changes by running queries against the log data. This iterative feedback loop contributes to a continuous improvement cycle, fostering a proactive approach to system maintenance and optimization. First navigate to CloudWatch Log Insights in the console, as shown:

![](images/Figure_16.5.png)

Figure 16.5: AWS CloudWatch Log Insights

CloudWatch Logs Insights proves especially valuable in addressing common use-cases within Amazon Elastic Kubernetes Service (EKS) clusters, such as identifying components that generate a high volume of requests to the Kubernetes API server. This capability is crucial for maintaining the performance, security, and overall health of EKS clusters. A specific query exemplifies how operators can leverage CloudWatch Logs Insights to gain insights into Kubernetes audit logs and pinpoint the sources of API requests, as shown:

fields userAgent, requestURI, @timestamp, @message

| filter @logStream ~= "kube-apiserver-audit"

| stats count(userAgent) as count by userAgent

| sort count desc

The provided query is tailored to analyze Kubernetes audit logs and focuses on extracting key information related to API requests, including the user agent, request URI, timestamp, and the log message itself. The query structure is designed for clarity and efficiency, employing a series of commands to filter, aggregate, and sort the log data effectively.

The breakdown of the query is as follows:

*   Selection of fields: The initial part of the query selects specific fields from the log data, namely userAgent, requestURI, @timestamp, and @message. These fields provide essential context for understanding the nature and source of API requests.
*   Filtering by log stream: The query filters log entries based on the @logStream attribute, specifically targeting logs originating from the Kubernetes API server audit component (kube-apiserver-audit). This ensures that the subsequent analysis focuses exclusively on relevant audit logs.
*   Aggregation and sorting: The query then employs the stats command to count the occurrences of user agents, grouping them by userAgent. The results are then sorted in descending order (sort count desc), providing a clear ranking of the components making the highest volume of API requests.

To execute this query within the CloudWatch Logs Insights console, users can select the appropriate log group associated with their EKS cluster. Copying and pasting the query into the console and running it initiates the analysis, returning valuable results detailing the components identified by user agents that are actively interacting with the Kubernetes API server. This information is instrumental in understanding the behavior of components within the EKS cluster, shedding light on which specific elements are driving API activity. Armed with this knowledge, operators can make informed decisions regarding resource allocation, optimization, and potential troubleshooting efforts.

In summary, CloudWatch Logs Insights represents a crucial component of AWS's observability toolkit, providing a robust and interactive solution for log analysis. Its purpose-built query language, coupled with a user-friendly interface, empowers operators to efficiently navigate and analyze log data, facilitating rapid issue resolution and ongoing system optimization. As organizations navigate the complexities of cloud-based environments, CloudWatch Logs Insights stands as a valuable ally, offering a data-driven approach to operational excellence.

[Logging components](#contents.xhtml#sc2_301a)

The Twelve-Factor App manifesto, authored by developers at Heroku, outlines a set of guiding principles for building modern, scalable, and maintainable cloud-native applications. These factors encapsulate best practices that promote consistency, flexibility, and ease of deployment across various environments. One of the central tenets of the Twelve-Factor App is the emphasis on treating logs as event streams and directing them to stdout and stderr.

The Twelve-Factor App manifesto serves as a guiding principle for modern application development, emphasizing best practices that contribute to scalability, maintainability, and resilience. One key factor, as outlined in the manifesto, underscores the importance of containerized applications directing their logs to stdout and stderr. This principle aligns with industry best practices, particularly in Kubernetes, where the architecture supports and builds upon this approach for efficient log management. The Kubernetes logging architecture delineates three distinct levels of logging, each catering to different aspects of monitoring and troubleshooting, as follows:

*   Basic level logging: At the basic logging level in Kubernetes, users have the capability to effortlessly retrieve pod logs using a straightforward command, exemplified by kubectl logs myapp—where myapp signifies a specific pod within the cluster. This functionality empowers users to directly access logs pertaining to a particular pod, providing a quick and accessible means for troubleshooting and diagnostics at the individual pod level. This direct and immediate access to pod logs proves invaluable in scenarios where swift analysis and identification of issues are paramount, facilitating a streamlined approach to resolving challenges within the Kubernetes environment.
*   Node level logging: Operating at the node level in Kubernetes, the container engine plays a pivotal role by capturing logs emanating from an application's stdout and stderr, channeling them into a designated log file. This level of logging is deeply entrenched in the Twelve-Factor App principles, emphasizing the importance of directing logs to standard output and standard error streams. By adhering to this fundamental aspect, Kubernetes ensures that logs are structured in a manner consistent with industry best practices, aligning seamlessly with the broader philosophy of modern application development. This approach not only facilitates efficient log management but also supports the overarching goal of creating scalable, maintainable, and cloud-native applications.
*   Cluster level logging: Expanding beyond the node-level logging infrastructure, Kubernetes incorporates a log capturing agent that operates on every node within the cluster. This agent performs a dual role by collecting two distinct types of logs: firstly, the container logs captured by the container engine on the node, and secondly, the system logs. The amalgamation of these logs is crucial for gaining comprehensive insights into both application-specific and system-level activities within the cluster. Subsequently, these aggregated logs are directed to a centralized logging destination, exemplified by platforms like Elasticsearch or CloudWatch. This centralized approach to log management ensures not only efficient storage but also facilitates cluster-wide visibility, enabling operators to monitor, analyze, and respond to events across the entire Kubernetes infrastructure.

Kubernetes itself does not provide a native solution for collecting and storing logs; instead, it configures the container runtime (for example, Docker) to save logs in JSON format on the local filesystem. Container runtimes redirect the container's stdout and stderr streams to a logging driver, and in Kubernetes, container logs are typically written to /var/log/pods/\*.log on the node. Additionally, both Kubelet and the container runtime generate their own logs, stored in /var/logs or in journald in operating systems with systemd.

To enhance cluster-wide log collection, log collector systems like Fluentd are employed. These systems operate as DaemonSets on worker nodes, tailing the log files generated by containers and system components. They aggregate and ship logs to centralized storage or analytics platforms, enabling efficient log retention, analysis, and alerting. In summary, the Kubernetes logging architecture embraces the Twelve-Factor App principle of directing logs to stdout and stderr, offering a multi-tiered approach to logging that spans from basic pod-level access to comprehensive cluster-wide log collection and analysis. This structured approach aligns with industry best practices, facilitating robust monitoring and troubleshooting in dynamic containerized environments.

[EKS troubleshooting](#contents.xhtml#sc2_302a)

Amazon Elastic Kubernetes Service (EKS) provides a managed environment for deploying, managing, and scaling containerized applications using Kubernetes. While EKS abstracts away much of the complexity of Kubernetes cluster management, troubleshooting remains a crucial skill for ensuring the health and performance of your applications. In this section, we will explore common EKS troubleshooting scenarios, along with useful commands to diagnose and resolve issues.

[Node and pod status checks](#contents.xhtml#sc3_303a)

Using kubectl, the Kubernetes command-line tool, is essential for inspecting and managing EKS clusters. To check the status of nodes and pods:

*   Verify node status: To gain insights into the health and availability of worker nodes within the EKS cluster, the kubectl get nodes command serves as the go-to tool. Executing this command provides a snapshot of the status of each node, including information such as their names, conditions, and availability. This simple yet powerful command is instrumental in assessing the foundational components of the cluster and quickly identifying any nodes that may be experiencing issues or are in an undesirable state.
    
    kubectl get nodes
    
*   List all pods in a namespace: When troubleshooting or monitoring specific applications or services within the EKS cluster, it is often necessary to list all pods within a designated namespace. The kubectl get pods command, coupled with the -n flag specifying the namespace, facilitates this task. This command delivers a comprehensive view of the pods, their current states, and relevant metadata. It is particularly valuable when tracking the overall health of applications, identifying any pods in a pending state, or verifying the distribution of workloads across the cluster.
    
    kubectl get pods -n <namespace>
    
*   Describing a pod for detailed information: In scenarios where a deeper understanding of a specific pod's configuration, events, or environmental variables is required, the kubectl describe pod command becomes an invaluable resource. By providing detailed information about the pod's current state, resource allocations, and associated events, this command assists in pinpointing issues, understanding the pod's lifecycle, and gathering context for effective troubleshooting.
    
    kubectl describe pod <pod-name> -n <namespace>
    

[Network issues](#contents.xhtml#sc3_304a)

Network-related issues within an Amazon EKS cluster can pose challenges to the seamless communication between pods, nodes, and external services. Effectively troubleshooting these issues requires a combination of diagnostic insights and targeted commands using kubectl, the Kubernetes command-line tool. Here, we explore how specific kubectl commands can be instrumental in identifying and resolving network-related challenges:

*   Checking the networking configuration of a pod: When communication issues arise within a pod, inspecting its networking configuration becomes paramount. The kubectl exec command allows direct execution of a shell within a pod, enabling users to investigate the network settings, diagnose potential misconfigurations, or run network-related tests.
    
    kubectl exec -it <pod-name> -n <namespace> -- /bin/sh
    
    By accessing the pod's shell, users can explore network configurations, test connectivity to external services, and gather real-time insights into the network environment. This command proves valuable in scenarios where direct interaction with a pod is necessary for diagnosing network issues.
    
*   Inspecting network policies: Kubernetes network policies play a crucial role in governing communication between pods within a namespace. Issues with network policies can lead to unexpected behavior or connectivity problems. The kubectl get networkpolicies command provides a comprehensive view of the existing network policies within a specified namespace.
    
    kubectl get networkpolicies -n <namespace>
    
    This command assists administrators in verifying the applied policies, understanding ingress and egress rules, and identifying any restrictions that might be affecting communication between pods. By inspecting network policies, users gain insights into the security and connectivity configurations that may impact the flow of traffic within the cluster.
    
*   Investigating service configurations: Services in Kubernetes act as a crucial abstraction layer for communication between pods, enabling a dynamic and scalable network infrastructure. When network issues involve services, the kubectl get services command becomes instrumental in examining service configurations within a specific namespace.
    
    kubectl get services -n <namespace>
    
    By executing this command, users can review details such as service type, cluster IP, external IP, and ports. Investigating service configurations is crucial for identifying misconfigurations or discrepancies that might hinder external access or inter-pod communication. This command provides a quick overview of the current service landscape, aiding in the identification and resolution of network-related challenges.
    

[Cluster logs and events](#contents.xhtml#sc3_305a)

Monitoring and logging are integral components of maintaining a healthy and resilient Amazon EKS cluster. Amazon EKS seamlessly integrates with Amazon CloudWatch, a comprehensive monitoring service, to provide insights into cluster events and facilitate effective log analysis. Here, we delve into the significance of inspecting cluster logs and events using specific commands, primarily interfacing with Amazon CloudWatch:

*   Checking EKS cluster events: Understanding the events occurring within an EKS cluster is crucial for identifying issues, tracking changes, and ensuring optimal performance. The aws eks describe-cluster command, combined with the \--query flag, allows users to retrieve valuable information about the events associated with a specific EKS cluster.
    
    aws eks describe-cluster --name <cluster-name> --region <region> --query cluster.events
    
    Executing this command provides a detailed overview of the events within the cluster, encompassing activities such as node terminations, configuration updates, or any other noteworthy occurrences. This real-time visibility into cluster events is instrumental in proactive monitoring and swift issue resolution.
    
*   Exploring CloudWatch logs for worker nodes: Worker nodes play a critical role in EKS clusters, and logs generated by these nodes offer valuable insights into their behavior and performance. Amazon CloudWatch Logs serve as a centralized repository for these logs, enabling administrators to explore and analyze them for diagnostic purposes. The aws logs describe-log-groups command, with the \--log-group-prefix flag, facilitates the exploration of CloudWatch log groups associated with worker nodes.
    
    aws logs describe-log-groups --log-group-prefix /aws/eks/<cluster-name>/worker
    
    By executing this command, users can obtain a comprehensive list of log groups specific to worker nodes in the EKS cluster. Subsequently, these logs can be further examined using CloudWatch Logs Insights or other analytics tools to gain detailed insights into node activities, identify errors, and track node-level events that contribute to the overall cluster health.
    

[Authentication and authorization](#contents.xhtml#sc3_306a)

Authentication and authorization are fundamental components of Kubernetes security, particularly in Amazon EKS, where precise control over pod and user permissions is crucial. Issues in these domains can manifest as permission errors, hindering the smooth operation of your EKS clusters. In this section, we will delve into the significance of authentication and authorization in EKS and explore specific kubectl commands to diagnose and resolve potential problems. The following are some of the ways to authenticate and authorize using the kubectl commands:

*   Verifying the current context: The kubectl config current-context command serves as a starting point for diagnosing authentication and authorization issues. It provides information about the current context, which includes details about the cluster, user, and namespace that kubectl is currently configured to interact with.
    
    kubectl config current-context
    
    This command ensures that you are operating within the expected context and helps identify any misconfigurations that might lead to authentication failures or unauthorized access.
    
*   Checking cluster roles and role bindings: Cluster roles and role bindings are central to RBAC in Kubernetes, defining what actions are allowed within the cluster and who can perform them. The following kubectl commands enable you to inspect these roles and bindings:
    
    kubectl get clusterroles
    
    kubectl get clusterrolebindings
    
    By executing these commands, you gain visibility into the existing cluster roles and their associated role bindings. Examining this information is crucial for identifying potential misconfigurations or inconsistencies that might result in permission errors. Ensure that roles and bindings are appropriately defined and that service accounts and users are correctly associated with their respective roles.
    
*   Inspecting role and role binding details: For a more granular analysis, you can use the kubectl describe command to inspect the details of specific roles and role bindings:
    
    kubectl describe clusterrole <clusterrole-name>
    
    kubectl describe clusterrolebinding <clusterrolebinding-name>
    
    These commands provide detailed information about the permissions granted by a particular cluster role and the subjects (users or service accounts) associated with a specific role binding. It helps in pinpointing the source of permission-related issues, enabling administrators to adjust configurations accordingly.
    

[EKS control plane logs](#contents.xhtml#sc3_307a)

In Amazon EKS, the control plane serves as the central orchestrator, managing the various components of the Kubernetes cluster. Understanding the activities within the EKS control plane is crucial for troubleshooting, auditing, and maintaining the overall health of the cluster. Enabling and analyzing control plane logs is a pivotal aspect of this process, providing insights into API server activities and cluster-wide events. In this section, we will explore the significance of EKS control plane logs and delve into specific AWS CLI commands for enabling and viewing these logs. The following list provides the command to update the EKS cluster configuration:

*   Enabling control plane logging: The aws eks update-cluster-config command with the \--logging flag allows administrators to enable logging for specific control plane components. This command modifies the configuration of the EKS cluster to enable logging for API server activities, audit logs, authenticator logs, controller manager logs, and scheduler logs. The enabled: true parameter indicates the activation of logging for the specified components.
    
    aws eks update-cluster-config --name <cluster-name> --logging '{"clusterLogging":\[{"types":\["api","audit","authenticator",  
    "controllerManager","scheduler"\],"enabled":true}\]}'
    
    By executing this command, administrators ensure that the specified control plane components generate logs, which are crucial for gaining visibility into the inner workings of the EKS cluster. These logs are subsequently sent to CloudWatch for centralized storage and analysis.
    
*   Viewing CloudWatch logs for control plane components: Once control plane logging is enabled, administrators can use CloudWatch Logs to view and analyze the generated logs. The specifics of where the logs are stored depend on the configuration and CloudWatch Log Groups associated with the EKS cluster. However, the general command to retrieve information about these log groups is:
    
    aws logs describe-log-groups --log-group-prefix /aws/eks/<cluster-name>/
    
    By executing this command, administrators obtain details about the CloudWatch Log Groups associated with the specified EKS cluster. Subsequently, they can navigate to the CloudWatch console or utilize the AWS CLI to query and analyze the logs, gaining valuable insights into API server activities, audit events, and the performance of key control plane components.
    

[Conclusion](#contents.xhtml#sc2_308a)

Amazon EKS control plane logging is a powerful tool for enhancing the observability and management of Kubernetes clusters on AWS. By providing a comprehensive set of log types and flexible configuration options, EKS empowers users to tailor their logging strategy to meet the unique needs of their applications and infrastructure. As organizations continue to embrace containerized applications and Kubernetes orchestration, the role of logging becomes increasingly critical. Amazon EKS, with its robust control plane logging capabilities, is well-positioned to support the evolving needs of modern cloud-native environments. Continuous innovation in logging and monitoring tools, coupled with adherence to best practices, will contribute to the overall success of organizations leveraging Amazon EKS for their containerized workloads.

[Questions](#contents.xhtml#sc2_309a)

1.  What log types are available in EKS control plane logging?
2.  How can CloudWatch Logs Insights be used to analyze Kubernetes audit logs?
3.  What are the three distinct levels of logging in Kubernetes?
4.  What kubectl command checks pod status and events?
5.  How do you enable control plane logging for an EKS cluster?

[Exercises](#contents.xhtml#sc2_310a)

1.  Use kubectl to diagnose a CrashLoopBackOff error for a pod.
2.  Write a Logs Insights query to identify top API callers.
3.  Configure Fluentd as a logging agent for your cluster.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 17Integrating EKS with Other AWS Services](#contents.xhtml#ch17a)

[Introduction](#contents.xhtml#sc2_311a)

As organizations continue embracing cloud-native approaches to application development, orchestrating containerized workloads has become a strategic imperative. Addressing the complexities associated with container orchestration, Amazon Elastic Kubernetes Service (EKS) has emerged as a managed offering seamlessly integrating Kubernetes with AWS. However, the true capabilities of Amazon EKS extend far beyond just cluster management. Integrating EKS with the wider array of AWS managed services unlocks tremendous potential for architecting complete, production-grade solutions. Blending the simplicity of EKS with purpose-built databases, serverless computing, advanced monitoring, and other specialized AWS offerings enables organizations to concentrate on application innovation rather than infrastructure management.

This chapter serves as a comprehensive section for organizations exploring EKS integrations for enhancing the security, observability, efficiency, and reliability of their Kubernetes applications. It undertakes a multi-faceted exploration of integrating Amazon EKS with five pivotal AWS services — AWS Lambda, Amazon Relational Database Service (RDS), Elastic Container Service (ECS), CloudWatch, and DynamoDB. Whilst the possible integrations with EKS are endless, we will focus on these areas, to taste a few. With a blend of architectural overviews, step-by-step configurations, real-world examples, and best practices, the chapter aims to equip readers with practical knowledge to build seamless integrations based on application requirements. The examples and use cases provide hands-on experience with EKS integration while illustrating the tangible benefits firsthand for container-based application architectures.

Whether you are just getting started with Amazon EKS or looking to make your EKS applications enterprise-grade, this chapter serves as an actionable reference for unlocking the multitude of possibilities through EKS integration. The integrations discussed herein reflect mature and proven patterns for developing cloud-native applications, setting you up for success as you progress into production environments and plan for scale.

[Structure](#contents.xhtml#sc2_312a)

The chapter covers the following sections:

*   Integration with AWS Lambda
*   EKS and Amazon RDS collaboration
*   Amazon EKS and Amazon ECS integration
*   EKS and AWS CloudWatch integration
*   EKS and AWS DynamoDB integration

[Objectives](#contents.xhtml#sc2_313a)

This chapter aims to offer a comprehensive insight into the integration process, covering essential aspects such as benefits, use cases, and detailed implementation steps for seamlessly incorporating AWS Lambda, Amazon RDS, Amazon ECS, AWS CloudWatch, and AWS DynamoDB into an EKS environment. To enhance clarity, architectural diagrams, sample configurations, and code examples are meticulously included, offering readers practical visualizations and tangible resources for implementation.

We will also explore valuable best practices, optimization strategies, and troubleshooting tips, fostering robust and efficient integrations. Real-world examples and case studies are woven into the narrative, presenting readers with tangible integration scenarios that reflect the challenges and solutions encountered in practical applications. The goal is to empower readers with practical knowledge, enabling them to architect well-integrated EKS applications that not only meet the demands of the present but are also positioned for future scalability and adaptability in the dynamic landscape of cloud-native development.

[Integration with AWS Lambda](#contents.xhtml#sc2_314a)

Let us focus on the synergy between EKS and AWS Lambda, exploring the integration points for achieving serverless computing within Kubernetes clusters. Real-world scenarios illustrate how the combination of EKS and Lambda can enhance application performance, providing a deeper understanding of the practical applications of serverless architecture. Hands-on examples section readers through the process of setting up serverless functions within an EKS environment, showcasing the power of this dynamic integration.

[Understanding the integration points](#contents.xhtml#sc3_315a)

Before embarking on the implementation journey, it is essential to grasp the fundamental integration points between Amazon EKS and AWS Lambda. This involves a nuanced exploration of the collaboration between Kubeless, a serverless framework tailored for Kubernetes, and AWS Lambda functions. By delving into this integration, one can comprehend the seamless deployment and management of Lambda functions within the EKS cluster, unlocking the potential for serverless computing in a Kubernetes environment. Furthermore, a critical aspect to consider is the event trigger mechanism that underpins the responsiveness of Lambda functions to specific events within the EKS environment. This analysis involves a meticulous examination of the triggers that can be employed, such as changes in cluster status or application scaling events. Understanding this mechanism is pivotal for orchestrating a dynamic and responsive infrastructure that leverages the capabilities of both EKS and AWS Lambda seamlessly.

[Setting up EKS cluster for Lambda integration](#contents.xhtml#sc3_316a)

Let us proceed with the step-by-step process of setting up an EKS cluster for seamless integration with AWS Lambda. To configure an Amazon EKS cluster, start by creating the cluster using either the AWS Management Console or AWS CLI. Employ the eksctl command to initiate the cluster creation process with parameters such as the cluster name and region, as demonstrated: eksctl create cluster --name <your-cluster-name> --region <your-region>. Following cluster creation, ensure proper interaction with the cluster using kubectl by updating its configuration with the EKS cluster details: aws eks --region <your-region> update-kubeconfig --name <your-cluster-name>. Please note that if Lambda needs to be integrated with EKS, appropriate IAM roles and policies must be configured to grant necessary permissions.

Subsequently, to integrate Kubeless with EKS, initiate the installation process by employing kubectl to install the Kubeless CLI. Create a dedicated namespace for Kubeless using kubectl create ns kubeless. Then, proceed to install Kubeless by applying the provided YAML configuration file, ensuring the desired version (e.g., v1.0.7) is specified: kubectl create -f https://github.com/kubeless/kubeless/releases/download/v1.0.7/kubeless-v1.0.7.yaml. Finally, deploy the Kubeless controller onto the EKS cluster, and validate the deployment status using the command kubectl get deployments -n kubeless. This configuration sets the stage for leveraging serverless capabilities seamlessly within the EKS environment.

[Deploying a Lambda function in EKS](#contents.xhtml#sc3_317a)

To initiate the deployment of an AWS Lambda function, start by creating the function's code, typically written in a language such as Python, and package it into a ZIP file. Once the code is prepared, employ the AWS Command Line Interface (CLI) to seamlessly deploy the Lambda function. Use the aws lambda create-function command, specifying essential parameters such as the function name, runtime (e.g., python3.11), handler, the path to the ZIP file, and the associated IAM role ARN:

aws lambda create-function --function-name <your-function-name> --runtime python3.11 --handler <your-handler> --zip-file fileb://<path-to-zip-file> --role <your-iam-role-arn>

Following the deployment, retrieve the Amazon Resource Name (ARN) of the deployed Lambda function using the aws lambda get-function command:

aws lambda get-function --function-name <your-function-name> --query 'Configuration.FunctionArn'

This process ensures the seamless creation and deployment of a Lambda function, ready to be integrated into your broader AWS ecosystem.

[Real-world scenarios](#contents.xhtml#sc3_318a)

To exemplify the tangible benefits of integrating Amazon EKS with AWS Lambda, let us delve into real-world scenarios. One practical application involves configuring a Lambda function to facilitate the automatic scaling of the EKS cluster based on predefined metrics. In this scenario, Lambda acts as an intelligent orchestrator, dynamically adjusting the cluster size to meet fluctuating workloads, optimizing resource utilization, and enhancing overall operational efficiency.

In another scenario, the integration demonstrates its prowess through an event-driven mechanism. Here, a Lambda function responds dynamically to changes in application load, promptly triggering scaling actions within the EKS environment. This event-driven approach ensures that the EKS cluster adapts seamlessly to varying demands, providing a responsive and resilient infrastructure that aligns with the specific needs of the applications running within the Kubernetes environment. These real-world applications underscore the flexibility and efficiency achieved through the strategic integration of EKS and Lambda, showcasing the dynamic capabilities of cloud-native architectures.

[EKS and Amazon RDS collaboration](#contents.xhtml#sc2_319a)

The collaboration between EKS and Amazon Relational Database Service (RDS) is a critical integration point for managing databases within Kubernetes clusters. This chapter explores strategies for seamlessly integrating EKS with RDS, covering topics such as database management best practices, security considerations, and performance optimization. Real-world case studies illustrate the advantages of this collaboration, offering valuable insights for organizations seeking efficient database solutions within their EKS environments. It is a best practice to validate the EKS setup by running commands like kubectl get nodes and ensuring all nodes are ready. For RDS, ensure that the database is accessible from the EKS environment using connection tests.

[Preparing EKS and RDS](#contents.xhtml#sc3_320a)

Before embarking on the exploration of integration possibilities, it is paramount to ensure that both Amazon EKS and Amazon RDS are properly configured. This begins by creating an EKS cluster using the eksctl command, a powerful tool designed for EKS cluster management. Execute the following command to initiate the creation of the EKS cluster, tailoring it to your specific requirements by providing a unique cluster name and selecting the appropriate region:

eksctl create cluster --name <your-cluster-name> --region <your-region>

Once the EKS cluster is established, the next crucial step is to configure the Kubernetes command-line tool, kubectl, ensuring seamless interaction with the newly created EKS cluster. This is achieved by running the command:

aws eks --region <your-region> update-kubeconfig --name <your-cluster-name>

These commands collectively set the groundwork for a well-configured EKS environment, facilitating the subsequent integration steps with Amazon RDS. It is imperative that these initial configurations are executed accurately to ensure a smooth and effective integration process, enabling organizations to leverage the combined capabilities of EKS and RDS for their containerized applications.

[Amazon RDS configuration](#contents.xhtml#sc3_321a)

Before delving into the intricacies of integration, it is crucial to establish that both Amazon EKS and Amazon RDS are properly configured. Starting with RDS, the initial step involves creating an RDS instance using either the AWS Management Console or the AWS Command Line Interface (CLI). Employ the following AWS CLI command, customizing it with the relevant parameters such as the database instance identifier, engine type, master username, password, allocated storage, and database instance class:

aws rds create-db-instance --db-instance-identifier <your-db-instance-id> --engine <your-db-engine> --master-username <your-username> --master-user-password <your-password> --allocated-storage <your-storage> --db-instance-class <your-instance-type>

This command initiates the creation of the RDS instance, specifying essential configuration details for the database engine, storage capacity, and instance type. Once the RDS instance is successfully created, it is imperative to retrieve crucial information for subsequent use. Execute the following AWS CLI command to obtain the RDS endpoint and database credentials:

aws rds describe-db-instances --db-instance-identifier <your-db-instance-id> --query 'DBInstances\[0\].\[Endpoint.Address,MasterUsername,MasterUserPassword\]' --output text

This command fetches the RDS instance's endpoint address, master username, and master user password, providing the necessary details for establishing a connection between EKS and RDS. These preparatory steps ensure that both EKS and RDS are properly configured, laying the groundwork for a seamless and effective integration process.

[Integrating EKS with Amazon RDS](#contents.xhtml#sc3_322a)

With the foundational setup of both Amazon EKS and Amazon RDS complete, the next crucial step in the integration process is to manage sensitive information securely. To achieve this, we create a Kubernetes Secret to store the RDS database credentials, ensuring that sensitive information is handled with the utmost security. Execute the following kubectl command to create a generic Kubernetes Secret named rds-credentials. This Secret will encapsulate the critical RDS database credentials, including the username, password, and the RDS endpoint:

kubectl create secret generic rds-credentials --from-literal=username=<your-username> --from-literal=password=<your-password> --from-literal=host=<your-rds-endpoint>

This command establishes a secure container within the Kubernetes cluster to hold the sensitive information required for the EKS-RDS integration. The created Secret will be instrumental in ensuring that the database credentials are accessible to authorized entities within the Kubernetes environment while maintaining confidentiality. To confirm the successful creation of the Secret, execute the following command:

kubectl get secrets rds-credentials

This command verifies that the rds-credentials Secret has been successfully created and is available within the Kubernetes cluster, providing a secure repository for the necessary RDS database credentials. These integration steps set the stage for a seamless connection between the EKS cluster and the RDS instance, facilitating the secure exchange of data between these two vital components within the AWS ecosystem.

[Deploying applications with RDS integration](#contents.xhtml#sc3_323a)

Modify your application configuration files to include RDS connection details, as shown in the following code snippet:

 apiVersion: apps/v1

 kind: Deployment

 metadata:

 name: your-app

 spec:

 replicas: 3

 template:

 metadata:

 labels:

 app: your-app

 spec:

 containers:

 - name: your-app-container

 image: your-app-image

 env:

 - name: DATABASE\_URL

 valueFrom:

 secretKeyRef:

 name: rds-credentials

 key: host

 - name: DATABASE\_USERNAME

 valueFrom:

 secretKeyRef:

 name: rds-credentials

 key: username

 - name: DATABASE\_PASSWORD

 valueFrom:

 secretKeyRef:

 name: rds-credentials

 key: password

Apply the updated configuration to deploy the application with RDS integration, as follows:

kubectl apply -f your-app-deployment.yaml

Scale the application as needed and monitor the logs to ensure successful database connections, as shown in the following code:

kubectl scale deployment your-app --replicas=5

kubectl logs -l app=your-app

[Database management best practices](#contents.xhtml#sc3_324a)

With the integration seamlessly established between Amazon EKS and Amazon RDS, it is essential to delve into best practices for effective database management within the EKS environment. Ensuring the resilience and security of your database is paramount. One crucial best practice involves enabling automated backups for the RDS instance. This is achieved through the AWS CLI using the modify-db-instance command, where you can set the desired backup retention period. The following command, for example, configures automated backups for a specified RDS instance with a retention period of seven days:

aws rds modify-db-instance --db-instance-identifier <your-db-instance-id> --backup-retention-period 7 --apply-immediately

This practice ensures that regular automated backups are maintained, providing a safety net for data recovery in the event of unforeseen incidents. In addition to automated backups, creating manual snapshots further enhances backup security. A manual snapshot is a point-in-time copy of your database instance, providing an additional layer of data protection. Execute the following command to create a manual snapshot:

aws rds create-db-snapshot --db-instance-identifier <your-db-instance-id> --db-snapshot-identifier <your-snapshot-id>

By incorporating these best practices into your database management strategy within EKS, you fortify the resilience of your data, ensuring that you have both automated and manual backup mechanisms in place for comprehensive data protection and recovery capabilities.

[Security considerations](#contents.xhtml#sc3_325a)

Ensuring the security of the EKS and RDS collaboration is paramount. Set up VPC peering between the EKS cluster and RDS VPC with the following command:

aws eks update-kubeconfig --name <your-cluster-name> --region <your-region>

eksctl create vpc-peering --vpc-id <your-eks-vpc-id> --peer-vpc-id <your-rds-vpc-id> --name <your-peering-connection-name>

Ensure that the security groups of both EKS and RDS allow communication, as shown:

aws ec2 authorize-security-group-ingress --group-id <your-eks-security-group> --protocol tcp --port 3306 --source <your-rds-security-group>

aws ec2 authorize-security-group-ingress --group-id <your-rds-security-group> --protocol tcp --port 3306 --source <your-eks-security-group>

[Performance optimization](#contents.xhtml#sc3_326a)

In the pursuit of optimizing the performance of the database within the Amazon EKS environment, it becomes imperative to fine-tune database parameters for optimal efficiency. This is achieved by modifying the Parameter Group using the AWS CLI. By adjusting specific database parameters, organizations can tailor the configuration to suit their workload and performance requirements. The following command exemplifies this process:

aws rds modify-db-parameter-group --db-parameter-group-name <your-parameter-group-name> --parameters "name=parameter\_name,value=new\_value,method=immediate" —apply-immediately

This command initiates an immediate adjustment to the specified database parameters, ensuring that changes take effect promptly to enhance the overall performance of the RDS instance within the EKS cluster. In addition to parameter optimization, monitoring database performance metrics is crucial for identifying potential bottlenecks and ensuring optimal functionality. Leveraging Amazon CloudWatch, organizations can gain insights into various performance metrics. Utilize the AWS CLI to retrieve these metrics, specifying the necessary parameters such as metric name, start and end times, monitoring period, statistics, and dimensions:

aws cloudwatch get-metric-statistics --namespace AWS/RDS --metric-name <your-metric-name> --start-time <start-time> --end-time <end-time> --period <period> --statistics <statistics> --dimensions Name=DBInstanceIdentifier,Value=<your-db-instance-id>

By consistently monitoring performance metrics, organizations can proactively identify and address any performance issues, ensuring the database operates at its optimum capacity within the EKS environment. These practices collectively contribute to a well-optimized and high-performing database infrastructure tailored to the dynamic demands of cloud-native applications.

[Real-world case studies](#contents.xhtml#sc3_327a)

Delving into real-world case studies sheds light on the tangible advantages and versatility of integrating Amazon EKS with Amazon RDS. In the context of a highly scalable e-commerce platform, organizations can leverage the collaborative capabilities of EKS and RDS to ensure efficient and secure database management. The seamless integration allows for dynamic scaling of the EKS cluster to meet the fluctuating demands of an e-commerce platform, while RDS provides a robust and scalable database solution. This collaboration not only optimizes resource utilization but also enhances the platform's responsiveness, contributing to a resilient and high-performance e-commerce infrastructure.

In another scenario, the integration of RDS within an EKS environment proves instrumental in establishing a global content delivery network (CDN). By strategically deploying RDS to store and manage content-related data within the EKS cluster, organizations can optimize performance and reduce latency for users across the globe. This synergy ensures that data is efficiently distributed and accessed, enhancing the overall user experience for a global audience. Such real-world implementations highlight the adaptability and scalability achieved through the collaboration of EKS and RDS, providing organizations with powerful tools to architect versatile and high-performance solutions tailored to specific business needs.

[Amazon EKS and Amazon ECS integration](#contents.xhtml#sc2_328a)

This section undertakes a comparative analysis of EKS and Elastic Container Service (ECS) integration scenarios. By understanding the strengths and weaknesses of each approach, readers can make informed decisions based on their specific application requirements and architecture. Practical considerations, performance benchmarks, and best practices section organizations in choosing the most suitable integration strategy for their containerized applications.

[Understanding EKS and ECS integration](#contents.xhtml#sc3_329a)

Before diving into the comparative analysis, let us gain a foundational understanding of both EKS and ECS integration. Let us create an EKS Cluster by using the eksctl to create an EKS cluster, as shown:

eksctl create cluster --name <your-eks-cluster> --region <your-region>

Ensure kubectl is configured to interact with the EKS cluster, as shown:

aws eks --region <your-region> update-kubeconfig --name <your-eks-cluster>

Create an ECS cluster by using the AWS Management Console or AWS CLI to create an ECS cluster, as shown:

aws ecs create-cluster --cluster-name <your-ecs-cluster>

Configure ECS CLI by installing and configuring the ECS CLI for managing ECS clusters, as shown: ecs-cli configure --cluster <your-ecs-cluster> --region <your-region> --default-launch-type EC2

[Comparative analysis](#contents.xhtml#sc3_330a)

Let us explore the strengths and weaknesses of integrating EKS and ECS in this section.

[EKS integration analysis](#contents.xhtml#sc4_331a)

Examining the strengths of Amazon EKS unveils its notable compatibility and community support. EKS stands out for its compatibility, supporting any standard Kubernetes application and offering organizations unparalleled flexibility in deploying and managing containerized workloads. Moreover, as a Kubernetes-based service, EKS enjoys the advantage of a vast and active community. This robust community support ensures that EKS users have access to a wealth of resources, shared knowledge, and continuous improvements, enhancing the platform's reliability and adaptability.

However, acknowledging the strengths also involves recognizing the potential weaknesses of EKS. One significant drawback lies in the complexity associated with setting up and managing EKS clusters, especially when compared to its counterpart, Elastic Container Service (ECS). The intricate configurations and fine-tuning required for EKS may pose challenges for users less familiar with Kubernetes environments. Additionally, it is essential to consider costs, as EKS may entail higher associated expenses due to the underlying infrastructure of Kubernetes. Organizations should carefully weigh the benefits against the complexities and costs to make informed decisions based on their specific requirements and technical expertise.

[ECS integration analysis](#contents.xhtml#sc4_332a)

Evaluating the strengths of Amazon ECS underscores its simplicity and cost-efficiency. ECS is lauded for its straightforward setup and management processes, making it particularly well-suited for smaller projects or teams with limited resources. The ease of use associated with ECS allows developers to quickly deploy and manage containerized applications without the complexities often associated with larger container orchestration platforms. Moreover, ECS can prove to be more cost-efficient for certain workloads, especially those that do not necessitate the comprehensive capabilities offered by more feature-rich solutions like Kubernetes.

However, these strengths are accompanied by certain limitations that organizations must consider. One notable weakness is the limited compatibility of ECS, which is specific to the Amazon Web Services (AWS) ecosystem. This restricts its use to AWS environments and diminishes its interoperability with other cloud providers, limiting flexibility for organizations with diverse infrastructure requirements. Additionally, ECS possesses a smaller community compared to Kubernetes-based solutions like Amazon EKS, potentially resulting in fewer shared resources and community-driven support. Organizations should carefully weigh these factors to determine if ECS aligns with their specific project scope, infrastructure preferences, and long-term scalability needs.

[Practical considerations and performance benchmarks](#contents.xhtml#sc3_333a)

When confronted with the decision to integrate either Amazon EKS or ECS, practical considerations and performance benchmarks become paramount in making an informed choice. In the realm of application characteristics, a crucial step involves evaluating the specific requirements of the application in question. Factors such as scalability, flexibility, and compatibility play pivotal roles in determining whether EKS or ECS is the more suitable choice. For instance, applications with varying scalability demands and a need for compatibility with diverse environments may find EKS, with its support for any standard Kubernetes application, more fitting. On the other hand, ECS, with its simplicity and specific compatibility with AWS, may be ideal for smaller projects with less intricate requirements.

In the domain of performance benchmarks, it is imperative to conduct thorough assessments on representative workloads to gauge the efficiency of EKS and ECS. Running performance benchmarks provides valuable insights into how each service handles specific workloads, aiding in the decision-making process. Additionally, analyzing resource utilization during benchmark tests, facilitated by tools like CloudWatch, allows for a comprehensive understanding of how EKS and ECS manage resources under different circumstances. This empirical approach ensures that the chosen integration aligns seamlessly with the performance expectations and resource utilization patterns of the applications in consideration.

[Best practices for integration](#contents.xhtml#sc3_334a)

Regardless of the chosen integration approach, certain best practices should be followed. We will discuss them in this section.

[EKS integration best practices](#contents.xhtml#sc4_335a)

When integrating Amazon EKS into your infrastructure, adhering to best practices is essential for optimal performance and security. Firstly, cluster sizing is a critical consideration. It is advisable to right-size EKS clusters based on specific workload requirements, ensuring that the allocated resources align with the demands of the applications. This practice not only enhances performance but also helps optimize costs by avoiding over-provisioning. Security considerations are equally paramount in EKS integration. Implementing robust security best practices safeguards the integrity and confidentiality of your Kubernetes environment. This includes the implementation of network policies to control communication between pods, defining IAM roles to manage access permissions, and employing encryption mechanisms to protect data in transit and at rest. By incorporating these security measures, organizations can establish a secure foundation for their EKS integration, mitigating potential vulnerabilities and ensuring a resilient and protected Kubernetes environment.

[ECS integration best practices](#contents.xhtml#sc4_336a)

For seamless integration of Amazon ECS into your architecture, it is imperative to follow best practices to enhance efficiency and scalability. Firstly, careful attention to task definitions is crucial. Efficiently defining tasks ensures optimal resource utilization, allowing ECS to effectively manage and allocate resources according to application requirements. This practice not only contributes to enhanced performance but also aids in resource cost optimization by preventing underutilization or over-provisioning. Additionally, implementing robust scaling strategies is vital for dynamic workload management. Leveraging auto-scaling strategies tailored to ECS tasks based on demand ensures that the infrastructure scales seamlessly in response to varying workloads. This adaptive scaling approach not only optimizes resource utilization but also enhances the responsiveness of the ECS environment, accommodating fluctuations in demand efficiently. By incorporating these best practices, organizations can maximize the benefits of ECS integration, fostering a scalable, resource-efficient, and resilient containerized application environment.

[EKS and AWS CloudWatch integration](#contents.xhtml#sc2_337a)

Configuring Amazon EKS to work seamlessly with AWS CloudWatch is essential for monitoring, logging, and maintaining the health of Kubernetes clusters. This section provides a comprehensive section to setting up CloudWatch integration, including the configuration of custom metrics and alarms for EKS clusters. Real-world examples showcase how organizations can proactively manage and optimize their EKS environments through effective monitoring and alerting.

[Understanding CloudWatch integration](#contents.xhtml#sc3_338a)

Before delving into the setup process, it is crucial to establish a foundational understanding of the significance of CloudWatch integration with Amazon EKS. Exploring the benefits of CloudWatch integration illuminates its pivotal role in enhancing the management and performance of EKS clusters. Firstly, CloudWatch integration provides real-time monitoring capabilities for EKS clusters. This immediate visibility into resource utilization empowers administrators and developers with timely insights, facilitating proactive responses to dynamic workload changes and potential performance issues. Furthermore, CloudWatch excels in log aggregation, allowing organizations to centralize their logs for efficient management. This centralized approach aids in troubleshooting and comprehensive log analysis, streamlining the identification and resolution of issues within the EKS environment.

Additionally, CloudWatch facilitates the creation of custom metrics and alarms, enabling organizations to establish proactive alerts. This capability ensures that teams can respond promptly to emerging issues and optimize cluster performance based on predefined thresholds. By leveraging these benefits, CloudWatch integration becomes a cornerstone for efficient monitoring, troubleshooting, and performance optimization within Amazon EKS clusters.

[Setting up CloudWatch integration](#contents.xhtml#sc3_339a)

Now, let us proceed with the step-by-step process of setting up CloudWatch integration for Amazon EKS. Enable EKS Cluster Logging by using the AWS Management Console or AWS CLI to enable EKS cluster logging to CloudWatch, as shown:

aws eks --region <your-region> update-cluster-config --name <your-cluster-name> --logging '{"clusterLogging":\[{"types":\["api","audit",

"authenticator","controllerManager","scheduler"\],"enabled":true}\]}'

Confirm that cluster logging is enabled with the following command:

kubectl get configmap cluster-info -o jsonpath='{.data.cluster\\.yaml}' -n kube-system

[CloudWatch agent installation](#contents.xhtml#sc3_340a)

To enable CloudWatch integration on Amazon EKS worker nodes, follow these step-by-step instructions. Begin by installing the CloudWatch agent on the worker nodes, as follows:

wget https://s3.amazonaws.com/amazoncloudwatch-agent/linux/amd64/latest/AmazonCloudWatchAgent.zip

unzip AmazonCloudWatchAgent.zip

sudo ./install.sh

This set of commands downloads the CloudWatch agent package, extracts it, and then runs the installation script to set up the agent on the EKS worker nodes. Next, configure the CloudWatch agent to collect and send metrics by editing the agent's configuration file:

sudo nano /opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json

This command opens the configuration file in the nano text editor, allowing you to specify the metrics and configurations you want the agent to monitor and send to CloudWatch. Once the configuration is set, start the CloudWatch agent with the following command:

sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json -s

[Creating custom metrics and alarms](#contents.xhtml#sc3_341a)

For a tailored approach to monitoring your Amazon EKS cluster, it is essential to define custom metrics based on specific requirements. Utilize the AWS CLI to put custom metrics into CloudWatch, as follows:

aws cloudwatch put-metric-data --namespace <your-namespace> --metric-name <your-metric-name> --value <your-metric-value>

This command allows you to define custom metrics within your specified namespace, providing granular insights into the aspects of your EKS cluster that matter most to your operations. To bolster proactive alerting, create CloudWatch alarms based on these custom metrics:

aws cloudwatch put-metric-alarm --alarm-name <your-alarm-name> --metric-name <your-metric-name> --namespace <your-namespace> --statistic <your-statistic> --period <your-period> --threshold <your-threshold> --comparison-operator <your-comparison-operator> --evaluation-periods <your-evaluation-periods> --actions-enabled --alarm-actions <your-SNS-topic-arn>

This command establishes an alarm in CloudWatch, allowing you to define thresholds and conditions that trigger alerts when specific metrics breach predefined limits. Integrating these custom metrics and alarms provides a tailored monitoring solution, enabling proactive response mechanisms to ensure the health and performance of your EKS cluster align with your specific operational requirements.

[Real-world examples](#contents.xhtml#sc3_342a)

Examining real-world examples provides tangible insights into the practical application of CloudWatch integration with Amazon EKS. For pod resource utilization, a critical aspect of EKS monitoring, you can leverage CloudWatch to monitor and create alarms for pod CPU and memory utilization. Utilize the following Kubernetes command to gather real-time information on pod resource utilization across all namespaces:

kubectl top pod --all-namespaces

This command enables administrators to monitor resource consumption, aiding in the identification of potential bottlenecks and ensuring optimal resource allocation within the EKS cluster. In the context of Cluster Autoscaler, a fundamental component of EKS, defining custom metrics and alarms becomes essential. This ensures proactive monitoring of the Autoscaler's performance. The following AWS CLI command illustrates how to put custom metrics into CloudWatch, focusing on the nodes metric within the KubernetesClusterAutoscaler namespace:

aws cloudwatch put-metric-data --namespace KubernetesClusterAutoscaler --metric-name nodes --value <your-metric-value>

By implementing these examples, organizations can effectively utilize CloudWatch to gain actionable insights into pod resource utilization and maintain optimal performance of the Cluster Autoscaler within their EKS environment. These real-world scenarios demonstrate the versatility and adaptability of CloudWatch integration for tailored and effective monitoring in an Amazon EKS setup.

[Proactive management and optimization](#contents.xhtml#sc3_343a)

The integration of CloudWatch into Amazon EKS empowers organizations to proactively manage and optimize their EKS environments. A key practice in achieving this is the creation of custom CloudWatch Dashboards, providing a centralized view of critical metrics and insights. To create custom dashboards, organizations can utilize either the AWS Management Console or CloudFormation. The AWS CLI command below exemplifies how to create a dashboard named <your-dashboard-name> by specifying a JSON file (eks-dashboard.json) containing the dashboard configuration:

aws cloudwatch put-dashboard --dashboard-name <your-dashboard-name> --dashboard-body file://eks-dashboard.json

This command enables the seamless deployment of tailored dashboards, consolidating essential metrics and visualizations for a comprehensive view of the EKS environment. Additionally, exploring key metrics directly in the CloudWatch console enhances visibility into crucial aspects of the EKS cluster. Metrics such as CPU utilization, memory utilization, and pod counts provide valuable insights that aid administrators and operators in making informed decisions. By regularly monitoring and analyzing these metrics, organizations can ensure optimal performance, troubleshoot potential issues, and continuously refine their EKS environments for maximum efficiency.

[Scaling actions based on metrics](#contents.xhtml#sc3_344a)

To dynamically adapt to varying workloads, organizations can implement auto-scaling policies for their Amazon EKS clusters, leveraging CloudWatch metrics for informed decisions. Configure auto-scaling policies with the following AWS CLI command, customizing parameters such as <your-policy-name>, <your-auto-scaling-group>, <your-scaling-adjustment>, <your-adjustment-type>, and <your-cooldown> to suit specific requirements:

aws autoscaling put-scaling-policy --policy-name <your-policy-name> --auto-scaling-group-name <your-auto-scaling-group> --scaling-adjustment <your-scaling-adjustment> --adjustment-type <your-adjustment-type> --cooldown <your-cooldown>

This command establishes policies that dynamically scale the EKS clusters based on defined thresholds and conditions, ensuring responsiveness to changes in demand. To validate the impact of these scaling policies, organizations can verify scaling events and their repercussions on EKS cluster performance. Utilize the AWS CLI command below, replacing <your-auto-scaling-group> with the specific auto-scaling group name:

aws autoscaling describe-scaling-activities --auto-scaling-group-name <your-auto-scaling-group>

This command provides insights into scaling events, allowing organizations to assess the effectiveness of their auto-scaling policies and adjust as needed to optimize the performance and resource utilization of their EKS clusters.

[EKS and AWS DynamoDB integration](#contents.xhtml#sc2_345a)

This section focuses on the integration of Amazon EKS with AWS DynamoDB, showcasing the seamless collaboration between containerized applications and a fully managed NoSQL database. In-depth working commands and step-by-step instructions will be provided, guiding readers through the process of setting up and optimizing the integration. Real-world use cases and examples will illustrate the advantages of leveraging DynamoDB within EKS environments for scalable and high-performance data storage.

[Benefits of DynamoDB integration](#contents.xhtml#sc3_346a)

DynamoDB stands out as a robust solution for data storage and retrieval in dynamic containerized environments, primarily due to its unparalleled scalability. Its seamless scalability enables organizations to handle varying workloads effortlessly, making it an ideal choice for applications operating within dynamic and containerized ecosystems. One of DynamoDB's key advantages lies in its status as a fully managed service. This characteristic relieves developers of operational burdens associated with database management, allowing them to channel their efforts and resources toward application development. By providing a managed service, DynamoDB streamlines database administration tasks, promoting a more efficient and focused development process.

In addition to its scalability and managed service model, DynamoDB boasts high-performance capabilities. The database engine ensures low-latency performance, catering to the demands of applications with stringent data access requirements. This attribute positions DynamoDB as a high-performing solution suitable for scenarios where quick and efficient data retrieval is paramount, contributing to an optimal user experience in a wide range of applications.

[Setting up DynamoDB integration](#contents.xhtml#sc3_347a)

To set up DynamoDB integration within an Amazon EKS cluster, follow these detailed steps:

1.  Access DynamoDB console: Navigate to the AWS Management Console and access the DynamoDB service. This provides you with the interface to manage and configure your DynamoDB tables.
    
2.  Create DynamoDB table: Create a DynamoDB table by specifying essential details such as the table name, primary key, and any additional attributes required for your specific use case. Define the structure of your table to suit the data storage and retrieval needs of your application.
    
3.  Create an IAM role: Create an IAM role with DynamoDB permissions to enable EKS pods to interact with DynamoDB. Utilize the AWS CLI with the following commands:
    
    aws iam create-role --role-name eks-dynamodb-role --assume-role-policy-section file://trust-policy.json
    
4.  Attach a necessary policy: Attach the necessary policy to the IAM role, granting it access to DynamoDB resources. Execute the following command:
    
    aws iam attach-role-policy --role-name eks-dynamodb-role --policy-arn arn:aws:iam::aws:policy/AmazonDynamoDBFullAccess
    
5.  Associate IAM role with EKS cluster: Associate the IAM role created with the EKS cluster, enabling pods within the cluster to assume this role. Use the following eksctl command, customizing the parameters such as <your-region>, <your-namespace>, and <your-cluster-name>:
    
    eksctl create iamserviceaccount --region <your-region> --name dynamodb-sa --namespace <your-namespace> --cluster <your-cluster-name> --attach-policy-arn arn:aws:iam::aws:policy/AmazonDynamoDBFullAccess --approve
    

By following these steps, you establish the necessary configurations for DynamoDB integration within your Amazon EKS cluster, ensuring seamless interaction between your containerized applications and DynamoDB resources.

[Deploy application with DynamoDB integration](#contents.xhtml#sc3_348a)

Modify your application configuration to include DynamoDB connection details as follows:

 apiVersion: apps/v1

 kind: Deployment

 metadata:

 name: your-app

 spec:

 replicas: 3

 template:

 metadata:

 labels:

 app: your-app

 spec:

 containers:

  - name: your-app-container

 image: your-app-image

 env:

 - name: DYNAMODB\_REGION

 value: <your-region>

 - name: DYNAMODB\_TABLE

 value: <your-dynamodb-table>

Apply the updated configuration to deploy the application with DynamoDB integration:

kubectl apply -f your-app-deployment.yaml

[Real-world use cases and examples](#contents.xhtml#sc3_349a)

To better understand the advantages of DynamoDB integration, let us explore real-world use cases and examples.

[Use case 1: Session storage in web applications](#contents.xhtml#sc4_350a)

Configure your web application to use DynamoDB for session storage:

  apiVersion: apps/v1

 kind: Deployment

 metadata:

 name: web-app

 spec:

 replicas: 3

 template:

 metadata:

 labels:

 app: web-app

 spec:

 containers:

 - name: web-app-container

 image: web-app-image

 env:

 - name: DYNAMODB\_REGION

 value: <your-region>

 - name: DYNAMODB\_TABLE

 value: <your-session-table>

Create a DynamoDB table specifically for session storage:

aws dynamodb create-table --table-name <your-session-table> --attribute-definitions AttributeName=sessionID,AttributeType=S --key-schema AttributeName=sessionID,KeyType=HASH --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5

[Use case 2: Real-time analytics data storage](#contents.xhtml#sc4_351a)

Configure your analytics application to use DynamoDB for storing real-time data:

 apiVersion: apps/v1

 kind: Deployment

 metadata:

 name: analytics-app

 spec:

 replicas: 3

 template:

 metadata:

 labels:

 app: analytics-app

 spec:

 containers:

 - name: analytics-app-container

 image: analytics-app-image

 env:

 - name: DYNAMODB\_REGION

 value: <your-region>

 - name: DYNAMODB\_TABLE

 value: <your-analytics-table>

Create a DynamoDB table specifically for storing real-time analytics data:

aws dynamodb create-table --table-name <your-analytics-table> --attribute-definitions AttributeName=eventID,AttributeType=S --key-schema AttributeName=eventID,KeyType=HASH --provisioned-throughput ReadCapacityUnits=10,WriteCapacityUnits=10

[Optimization strategies](#contents.xhtml#sc3_352a)

To ensure optimal performance, consider the following optimization strategies for DynamoDB integration.

[Use of DynamoDB Accelerator](#contents.xhtml#sc4_353a)

Deploy a DynamoDB Accelerator (DAX) cluster to enhance read performance:

aws dax create-cluster --cluster-name <your-dax-cluster> --node-type <your-node-type> --replication-factor <your-replication-factor>

Modify your application configuration to use DAX for DynamoDB caching:

  apiVersion: apps/v1

 kind: Deployment

 metadata:

 name: your-app

 spec:

 replicas: 3

 template:

 metadata:

 labels:

 app: your-app

 spec:

 containers:

 - name: your-app-container

 image: your-app-image

 env:

 - name: DYNAMODB\_REGION

 value: <your-region>

 - name: DYNAMODB\_TABLE

 value: <your-dynamodb-table>

 - name: DAX\_ENDPOINT

 value: <your-dax-endpoint>

[Conclusion](#contents.xhtml#sc2_354a)

In conclusion, the integration of Amazon EKS with a spectrum of AWS services presents an unparalleled opportunity for organizations to architect and deploy robust, production-grade applications. The array of integrations discussed within this chapter not only enriches the capabilities of EKS but also provides organizations with the tools to seamlessly incorporate diverse functionalities into their Kubernetes clusters. The empowerment derived from these integrations is profound, allowing organizations to seamlessly integrate serverless computing through AWS Lambda, leverage the robust capabilities of relational databases with Amazon Relational Database Service (RDS), make informed decisions about container orchestration with a comparative analysis ECS, and implement effective monitoring and logging through AWS CloudWatch. Additionally, the integration with NoSQL databases like DynamoDB further diversifies the data storage options within EKS environments.

As the AWS service catalogue continues to evolve, the integration of EKS with cutting-edge offerings is poised to become even more streamlined. The commitment of AWS to innovation ensures that organizations embracing EKS will have access to the latest advancements in cloud-native technologies, further enhancing their ability to stay at the forefront of application development practices. In essence, the integration of EKS with AWS services is not just a snapshot of current capabilities but a strategic investment in future-proofing application architectures and ensuring adaptability in the ever-evolving landscape of cloud computing.

[Questions](#contents.xhtml#sc2_355a)

1.  Which AWS service enables serverless functions within EKS clusters?
    
2.  What command retrieves RDS instance credentials needed for EKS integration?
    
3.  What are the two key advantages of ECS over EKS?
    
4.  What CloudWatch feature allows custom metrics and alarms for EKS?
    
5.  How does DynamoDB integration improve application scalability in EKS?
    

[Exercises](#contents.xhtml#sc2_356a)

1.  Deploy a sample Lambda function triggered by EKS autoscaling events.
    
2.  Configure a WordPress site on EKS integrated with the RDS MySQL instance.
    
3.  Set up AWS X-Ray tracing to troubleshoot requests between EKS and DynamoDB.
    

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 18Continuous Integration and Continuous Deployment Pipelines for Amazon EKS](#contents.xhtml#ch18a)

[Introduction](#contents.xhtml#sc2_357a)

In the dynamic landscape of cloud-native application development, orchestrating CI/CD pipelines is pivotal for organizations aiming to achieve efficiency and reliability in their deployment workflows. Amazon Elastic Kubernetes Service (EKS) has emerged as a robust solution, providing a scalable and managed Kubernetes environment. This chapter delves into the intricacies of building CI/CD pipelines for Amazon EKS applications, harnessing the capabilities of various AWS services for source control, build/test automation, container image management, deployment mechanisms, monitoring, and more. Real-world patterns and detailed configurations are presented to guide organizations towards achieving agility and reliability in their CI/CD practices.

Amazon EKS has rapidly become a cornerstone for organizations embracing container orchestration, providing a managed Kubernetes service that eliminates the complexities associated with deploying and managing clusters. EKS ensures seamless integration with other AWS services, fostering a cohesive ecosystem for deploying, managing, and scaling containerized applications. As organizations pivot towards microservices architecture and containerization, EKS emerges as a linchpin, empowering developers to focus on building applications without the burden of intricate infrastructure management.

This chapter spotlights key AWS services essential for constructing effective CI/CD pipelines on Amazon EKS. From source code management with AWS CodeCommit to automated build and test processes using AWS CodeBuild, and secure container image management with Amazon Elastic Container Registry (ECR), each service plays a pivotal role in enhancing the CI/CD lifecycle. Additionally, deployment techniques are optimized through AWS CodeDeploy, validation and testing are enriched with AWS X-Ray, and comprehensive monitoring is achieved via Amazon CloudWatch. The chapter unfolds a cohesive narrative, illustrating how these services seamlessly integrate to create a robust CI/CD pipeline tailored for Amazon EKS applications.

[Structure](#contents.xhtml#sc2_358a)

This chapter contains the following topics:

*   Overview of CI/CD on EKS
*   Source code management
*   Container images
*   Deployment techniques
*   Validation and testing
*   Monitoring and logging
*   Identity and access management
*   Pipeline orchestration

[Objectives](#contents.xhtml#sc2_359a)

This chapter aims to comprehensively address the objectives of providing a thorough understanding of best practices in continuous integration and continuous deployment (CI/CD) specifically tailored for Amazon EKS. It explores the essential AWS services, including CodeCommit, CodeBuild, CodeDeploy, and CodePipeline, offering detailed insights into their functionalities and roles in facilitating effective CI/CD workflows on EKS. The chapter provides practical configuration guidance, reference architectures, and code samples to empower readers to implement these services seamlessly within their CI/CD pipelines.

Covering critical aspects of testing, monitoring, and troubleshooting deployments, the section equips readers with techniques to enhance the reliability and performance of their EKS workloads. Additionally, it delves into identity management, permissions, and security considerations, ensuring a robust and secure CI/CD environment for organizations leveraging Amazon EKS. Ultimately, the chapter aims to empower readers with the knowledge and practical insights necessary to implement tailored CI/CD pipelines optimized for the dynamic nature of EKS workloads.

[Overview of CI/CD on EKS](#contents.xhtml#sc2_360a)

CI/CD stands as a linchpin in the contemporary software development landscape, offering a systematic approach to code delivery and deployment. In the context of Amazon Web Services (AWS) and specifically Amazon EKS, CI/CD becomes a critical enabler for orchestrating the seamless deployment of containerized applications on Kubernetes clusters. As organizations pivot towards microservices architecture and containerization, EKS emerges as a foundational solution, providing a fully managed Kubernetes service that alleviates the complexities of cluster management. This abstraction empowers developers to concentrate on building and deploying applications, promoting agility and efficiency in the development lifecycle.

Within CI/CD for Amazon EKS, a myriad of AWS services collaborate to fortify the pipeline's efficiency and reliability. AWS CodeCommit serves as a secure repository for source code, offering a version-controlled environment. AWS CodeBuild automates the build and test processes, generating deployable artifacts for containerized applications. Amazon Elastic Container Registry (ECR) complements the pipeline, providing a secure and scalable repository for Docker container images. This integration ensures a streamlined flow from source code to containerized deployment, fostering consistency and reliability.

AWS CodeDeploy extends its capabilities to EKS clusters, facilitating the automation of application deployments. This includes support for various deployment strategies such as blue/green and canary deployments, offering organizations flexibility in managing releases and minimizing downtime. The deployment phase is further complemented by monitoring and performance insights through Amazon CloudWatch and AWS X-Ray. CloudWatch provides comprehensive monitoring, enabling organizations to keep a vigilant eye on the health and performance of their EKS clusters and applications. AWS X-Ray facilitates a deeper understanding of application performance, offering insights into requests, latencies, and errors.

IAM roles and AWS CodePipeline orchestrate the end-to-end CI/CD workflow, ensuring a seamless integration of services. The robust integration between these AWS services and EKS positions organizations to harness the full potential of containerized applications in a cloud-native environment. This comprehensive CI/CD approach not only enhances reliability and scalability but also aligns with the principles of DevOps, fostering collaboration and efficiency across development and operations teams.

To summarize, the combination of AWS services and Amazon EKS in a CI/CD pipeline provides organizations with a powerful framework to modernize their software delivery practices. It empowers them to adapt to the rapidly changing software landscape, where agility, efficiency, and reliability are paramount. As organizations embrace this holistic approach to CI/CD, they position themselves at the forefront of modern software development practices, capable of meeting the demands of a fast-paced and dynamic digital era.

[Source code management](#contents.xhtml#sc2_361a)

In Amazon EKS, the journey of continuous integration and deployment commences with robust source code management and efficient build processes. AWS CodeCommit stands as a stalwart, providing a secure and scalable Git repository for organizations to manage their source code. The integration of CodeCommit ensures version-controlled environments, enabling development teams to collaborate seamlessly and maintain a consistent codebase. This secure foundation is paramount for organizations deploying applications on EKS, where version control is fundamental to managing containerized workloads.

A vital component in the CI/CD pipeline for EKS, AWS CodeBuild automates the build and test processes, offering a streamlined mechanism to generate deployable artifacts. CodeBuild supports a variety of programming languages and build scenarios, making it adaptable to the diverse needs of containerized applications. This automation reduces manual intervention, accelerates the build phase, and ensures the reliability of artifacts, enhancing the overall efficiency of the development lifecycle on EKS. As organizations leverage EKS for orchestrating their containerized applications, the integration of CodeCommit and CodeBuild becomes instrumental in maintaining a secure and efficient CI/CD workflow. CodeCommit provides the version-controlled foundation for code collaboration, while CodeBuild automates the compilation, testing, and packaging of applications. The synergy between these services ensures that the build artifacts align with the intended application state, contributing to the overall reliability of the CI/CD pipeline on EKS.

The significance of AWS CodeCommit and CodeBuild extends beyond source code management and build automation. These services integrate seamlessly with EKS, aligning with the principles of DevOps and supporting a culture of continuous improvement. The traceability and auditability provided by CodeCommit ensure that development teams have a clear understanding of code changes, contributing to the stability and security of applications deployed on EKS.

You can create a new CodeCommit repository with the following command:

aws codecommit create-repository --repository-name <your-repo-name>

You can clone a CodeCommit repository to your local machine with the following command:

git clone https://git-codecommit.<your-region>.amazonaws.com/v1/repos/<your-repo-name>

You can create a CodeBuild project with the following command:

aws codebuild create-project --name <your-project-name> --source "type=NO\_SOURCE" --artifacts "type=NO\_ARTIFACTS" --environment "type=LINUX\_CONTAINER,computeType=BUILD\_GENERAL1\_SMALL" --service-role <your-service-role-arn> --buildspec buildspec.yml

You can start a build in CodeBuild with the following command:

aws codebuild start-build --project-name <your-project-name>

These commands provide a basic setup for creating a CodeCommit repository and a CodeBuild project. Please replace placeholders like <your-repo-name>, <your-region>, <your-project-name>, and <your-service-role-arn> with your specific values.

The integration of AWS CodeCommit and CodeBuild forms the foundational layer of CI/CD for organizations utilizing Amazon EKS. These services not only facilitate secure source code management but also automate the build and test processes, enabling a streamlined and efficient delivery pipeline. As organizations strive for agility and reliability in their EKS-based deployments, the combination of CodeCommit and CodeBuild emerges as a cornerstone in the journey towards efficient, secure, and automated software delivery.

[Container images](#contents.xhtml#sc2_362a)

Within the intricate landscape of Amazon EKS, the management of container images is a critical aspect of ensuring a secure and efficient deployment pipeline. Amazon ECR emerges as a robust solution, offering organizations a secure and scalable repository for storing and managing Docker container images. ECR seamlessly integrates with EKS, forming a pivotal component in the containerization journey. By leveraging ECR, organizations can streamline their image management processes, fostering a consistent and reliable deployment environment on EKS. Using AWS CodeBuild to build and push Docker images to Amazon ECR involves creating a build specification file and configuring the CodeBuild project. Sample build spec.yaml is as below. You could use the above mentioned aws codebuild commands as well.

version: 0.2

phases:

 pre\_build:

 commands:

 - echo Logging in to Amazon ECR...

 - aws ecr get-login-password --region <your-region> | docker login --username AWS --password-stdin <your-ecr-repository-uri>

 build:

 commands:

 - echo Build started on \`date\`

 - echo Building the Docker image...

 - docker build -t <your-ecr-repository-uri>/<your-image-name>:<tag> .

 - echo Build completed on \`date\`

 post\_build:

 commands:

 - echo Pushing the Docker image to ECR...

 - docker push <your-ecr-repository-uri>/<your-image-name>:<tag>

The integration of ECR in the CI/CD pipeline for EKS provides development teams with a centralized and secure location to store and retrieve container images. This centralized repository ensures version control and traceability, key factors in maintaining the integrity of containerized applications. ECR's scalability aligns with the dynamic nature of EKS, accommodating the evolving demands of container-based workloads while maintaining efficiency and reliability in the image storage and retrieval process. As organizations navigate the security landscape of EKS, the implementation of image scanning practices becomes imperative. ECR offers native image scanning capabilities, allowing organizations to identify and address security vulnerabilities within their container images. This proactive approach to security aligns with best practices, ensuring that only secure and compliant container images progress through the CI/CD pipeline onto EKS clusters.

Amazon ECR not only provides a secure repository for container images but also aligns with the broader security goals of EKS deployments. The integration of image scanning practices enhances the overall security posture, reducing the risk of vulnerabilities within the containerized applications running on EKS clusters. This focus on security is particularly crucial in the context of EKS, where orchestrating containerized workloads requires a meticulous approach to maintaining the integrity of the entire deployment.

[Deployment techniques](#contents.xhtml#sc2_363a)

The orchestration of the deployment pipeline involves strategic planning and the implementation of deployment strategies. AWS CodeDeploy, as a deployment service, plays a crucial role in automating and simplifying deployments onto EKS clusters. This seamless integration ensures that organizations can leverage the capabilities of EKS while benefitting from the streamlined deployment processes facilitated by CodeDeploy. As organizations transition from development to production, the integration of AWS CodeDeploy in the CI/CD pipeline becomes pivotal. Practical steps include configuring deployment groups, defining deployment specifications, and associating deployments with the EKS cluster. This process ensures that applications move seamlessly through the deployment pipeline, minimizing downtime and maximizing efficiency. The flexibility and automation provided by CodeDeploy align with the dynamic nature of EKS, allowing organizations to adapt and scale their deployments according to evolving requirements.

Blue/green deployment strategies provide organizations with a reliable approach to minimize downtime during updates. By maintaining two identical environments (blue for production and green for testing new versions), organizations can smoothly transition between the two. This process involves creating separate EKS clusters, updating deployment configurations in CodeDeploy, and gradually shifting traffic from the blue to green environment after validating the new version. This phased approach ensures a controlled transition, mitigating potential disruptions to end-users.

Canary deployments, another valuable strategy, offer organizations a controlled means to test updates with a subset of users before a full-scale rollout. The practical steps for implementing Canary deployments in EKS involve gradually routing a small percentage of traffic to the new version, closely monitoring performance metrics, and incrementally increasing traffic based on successful validation. This iterative process allows organizations to identify and address potential issues early, maintaining stability throughout the deployment.

Practical examples illustrate the application of these deployment strategies in real-world scenarios. For instance, updating a microservices-based application running on EKS involves configuring separate deployment groups for different components, ensuring a phased and controlled rollout. Blue/green and canary strategies can be applied to specific microservices, allowing organizations to balance the need for rapid deployment with the imperative to maintain a stable production environment.

When considering the intricacies of deploying applications on EKS, organizations benefit from the robust capabilities of AWS CodeDeploy. The tool seamlessly integrates with EKS, providing a streamlined and automated deployment process. Blue/green and Canary deployment strategies enhance this process, offering organizations flexibility and control over their release cycles. These strategies empower organizations to deploy with confidence, knowing that the integrity and reliability of their applications on EKS are maintained throughout the deployment lifecycle.

The following AWS CLI commands can be used to perform blue/green and canary deployments using AWS CodeDeploy in the context of Amazon EKS. Please note that these commands provide a simplified representation, and you may need to customize them based on your specific deployment configurations. Security considerations for blue/green and canary deployments:

*   IAM role configuration: 
    *   Ensure that IAM roles and policies are properly configured to grant least privilege access for deployment processes.
    *   Regularly review and audit IAM permissions to remove unnecessary access.
*   Secure communication: 
    *   Use encrypted communication channels (e.g., HTTPS) for all interactions with AWS services and between application components.
    *   Implement VPC endpoints for AWS services to keep traffic within the AWS network.
*   Secrets management: 
    *   Utilize AWS Secrets Manager or AWS Systems Manager Parameter Store to securely store and manage sensitive data such as API keys, database credentials, and other secrets.
    *   Avoid hardcoding sensitive information in application code or configuration files.
*   Network security: 
    *   Implement proper network segmentation using security groups and network ACLs.
    *   Use private subnets for your EKS worker nodes and only expose necessary services through load balancers.
*   Image security: 
    *   Scan container images for vulnerabilities before deployment using tools like Amazon ECR image scanning or third-party solutions.
    *   Use trusted base images and keep them updated.
*   Kubernetes RBAC: 
    *   Implement and maintain proper Kubernetes RBAC to limit access to cluster resources.
*   Monitoring and logging: 
    *   Enable AWS CloudTrail to log API calls and monitor for suspicious activity.
    *   Implement comprehensive logging and monitoring for both the deployment process and the running applications.
*   Compliance and auditing: 
    *   Ensure that your deployment processes comply with relevant industry standards and regulations (e.g., PCI DSS, HIPAA).
    *   Regularly conduct security audits of your deployment pipelines and environments.
*   Rollback strategy: 
    *   Have a well-defined and tested rollback strategy in case security issues are detected after deployment.
*   Access control: 
    *   Implement strong authentication mechanisms for accessing deployment tools and environments.
    *   Use multi-factor authentication (MFA) for AWS account access.

By considering these security aspects, you can help ensure that your blue/green and canary deployments are not only efficient but also secure. 

[Blue/green deployment](#contents.xhtml#sc3_364a)

The steps to create a blue deployment is as follows:

1.  Create a deployment configuration:
    
    aws deploy create-deployment-config --deployment-config-name eks-bluegreen
    
2.  Create an application:
    
    aws deploy create-application --application-name eks-bluegreen
    
3.  Create a deployment group for blue environment:
    
    aws deploy create-deployment-group --application-name eks-bluegreen --deployment-group-name eks-blue-group --deployment-config-name eks-bluegreen --service-role-arn <your-service-role-arn> --blue-green-deployment-config terminateBlueInstances
    
4.  Deploy to blue environment:
    
    aws deploy create-deployment --application-name eks-bluegreen --deployment-group-name eks-blue-group --revision revisionType=GitHub,repository=https://github.com/<your-repo>,commitId=<your-commit-id>
    

[Canary deployment](#contents.xhtml#sc3_365a)

The steps to create a canary deployment is as follows:

1.  Create a canary deployment configuration:
    
    aws deploy create-deployment-config --deployment-config-name eks-canary
    
2.  Create a deployment group for canary environment:
    
    aws deploy create-deployment-group --application-name eks-canary --deployment-group-name eks-canary-group --deployment-config-name eks-canary --service-role-arn <your-service-role-arn> --deployment-style deploymentType=BLUE\_GREEN,deploymentOption=WITH\_TRAFFIC\_CONTROL
    
3.  Deploy to canary environment:
    
    aws deploy create-deployment --application-name eks-canary --deployment-group-name eks-canary-group --revision revisionType=GitHub,repository=https://github.com/<your-repo>,commitId=<your-commit-id>
    

These commands provide a high-level overview, and you should replace placeholders such as <your-service-role-arn>, <your-repo>, and <your-commit-id> with your actual values. Additionally, AWS CodeDeploy requires proper configurations in the appspec.yml file within your application source code repository. Adjust the parameters based on your specific use case and deployment scenarios.

As organizations embrace the dynamic nature of EKS, the synergy between deployment strategies and automation tools becomes increasingly crucial. AWS CodeDeploy, with its intuitive integration capabilities, allows organizations to achieve a balance between agility and reliability. Whether opting for blue/green deployments to ensure a seamless transition or Canary deployments to validate updates incrementally, organizations can tailor their deployment strategies to meet the unique demands of their EKS-based applications.

[Validation and testing](#contents.xhtml#sc2_366a)

In the context of deploying applications on Amazon EKS, the validation and testing phase is a critical component of the CI/CD pipeline. This phase ensures that applications not only meet functional requirements but also exhibit optimal performance and reliability when running on EKS clusters. AWS X-Ray, a distributed tracing service, and service integration testing play pivotal roles in validating and testing applications before they are deployed into production. Load testing on EKS with AWS X-Ray provides organizations with valuable performance insights into their applications. Practical steps involve configuring and instrumenting the application with X-Ray, defining test scenarios, and utilizing X-Ray to trace requests across microservices during load testing. This process enables organizations to identify bottlenecks, analyze latency, and optimize their applications for peak performance on EKS.

Service integration testing is an essential step in ensuring the reliability of applications deployed on EKS. This testing phase focuses on validating the interactions and interfaces between different microservices within the application. Practical steps include designing test cases that mimic real-world scenarios, creating test environments that mirror the EKS production cluster, and executing comprehensive tests to verify the seamless integration of services. Service integration testing provides organizations with confidence in the functionality and interoperability of their EKS applications.

The synergy between load testing and service integration testing ensures a comprehensive approach to validating applications on EKS. Load testing identifies how an application performs under varying levels of demand, simulating real-world scenarios to uncover performance bottlenecks. Service integration testing complements this by verifying that individual microservices work seamlessly together, minimizing the risk of integration issues when deployed on EKS.

Practical examples illustrate the application of load testing and service integration testing in real-world scenarios. For instance, an e-commerce application running on EKS might undergo load testing to assess its ability to handle concurrent user interactions. Simultaneously, service integration testing ensures that order processing, inventory management, and payment processing microservices work cohesively to provide a reliable and seamless user experience.

Considering the intricacies of validation and testing on EKS, organizations can leverage AWS X-Ray and service integration testing to ensure their applications meet performance and reliability standards. The combination of load testing for performance insights and service integration testing for interoperability provides a holistic view of an application's readiness for deployment on EKS.

[Load testing with AWS X-Ray](#contents.xhtml#sc3_367a)

The steps for load testing with AWS X-Ray is as follows:

1.  Enable X-Ray tracing for your EKS cluster:
    
    aws eks update-cluster-config --name <your-cluster-name> --region <your-region> --logging ‘{"clusterLogging":\[{"types" \["api","audit",  
    "authenticator","controllerManager","scheduler"\],"enabled":true}\]}'
    
2.  Instrument your application code with X-Ray SDK.
    
    Integrate the X-Ray SDK into your application code based on the programming language used.
    
3.  Configure load testing tool (e.g., Locust) to use X-Ray.
    
    Ensure your load testing tool is configured to propagate X-Ray trace headers during load testing.
    
4.  Define test scenarios and execute load testing.
    
    Use your preferred load testing tool to define test scenarios and execute load tests against your EKS application.
    
5.  Analyze X-Ray traces:
    
    aws xray get-trace-summaries --start-time $(date -d "15 minutes ago" +%s) --end-time $(date +%s) --filter-expression 'service("your-service-name")' --region <your-region>
    

As organizations embrace the dynamic nature of EKS, the importance of thorough validation and testing cannot be overstated. AWS X-Ray and service integration testing offer powerful tools to ensure applications not only function as intended but also deliver optimal performance in the EKS environment. By incorporating these testing methodologies into the CI/CD pipeline, organizations can confidently deploy applications on EKS, knowing they have been rigorously validated and tested for performance and reliability.

[Monitoring and logging](#contents.xhtml#sc2_368a)

Monitoring and logging play pivotal roles in ensuring the health, performance, and reliability of applications deployed on Amazon EKS. Amazon CloudWatch, a comprehensive monitoring service, and AWS X-Ray, a distributed tracing service, provide organizations with the tools needed to gain insights into their EKS applications, enabling proactive management and troubleshooting. Amazon CloudWatch offers organizations a robust solution for monitoring EKS clusters, providing real-time visibility into resource utilization, application performance, and operational health. Practical steps involve configuring CloudWatch Alarms, defining custom metrics, and utilizing the CloudWatch dashboard to visualize key performance indicators. This comprehensive monitoring ensures that organizations can promptly identify and address issues, optimizing the overall performance of their EKS applications.

AWS X-Ray enhances monitoring capabilities by providing detailed insights into the performance of applications running on EKS. Through distributed tracing, X-Ray allows organizations to visualize the entire request flow across microservices, identify latency bottlenecks, and diagnose issues affecting application performance. Integrating X-Ray into EKS applications involves instrumenting the code, enabling tracing, and utilizing the X-Ray console to analyze traces and pinpoint performance bottlenecks. The synergy between Amazon CloudWatch and AWS X-Ray provides a holistic approach to monitoring EKS applications. CloudWatch monitors infrastructure metrics, such as CPU utilization, memory usage, and networking, offering a macro-level view of the EKS cluster's health. Simultaneously, AWS X-Ray delves into the microservices, providing a granular understanding of the application's performance at the code level. Together, these tools offer organizations a comprehensive monitoring solution for their EKS deployments. The AWS CLI commands for monitoring and logging with Amazon CloudWatch is as follows:

1.  Create a CloudWatch Alarm for CPU utilization:
    
    aws cloudwatch put-metric-alarm --alarm-name <your-cpu-alarm-name> --metric-name CPUUtilization --namespace AWS/EKS --statistic Average --period 300 --threshold <your-threshold> --comparison-operator GreaterThanThreshold --dimensions Name=ClusterName,Value=<your-cluster-name> --evaluation-periods 2 --alarm-actions <your-SNS-topic-arn>
    
2.  Define custom metric in CloudWatch:
    
    aws cloudwatch put-metric-data --namespace <your-namespace> --metric-name <your-metric-name> --value <your-metric-value> --dimensions Name=ClusterName,Value=<your-cluster-name>
    
3.  Create a CloudWatch Dashboard:
    
    aws cloudwatch put-dashboard --dashboard-name <your-dashboard-name> --dashboard-body file://eks-dashboard.json
    

Practical examples illustrate the application of monitoring and logging in real-world scenarios. For instance, organizations can set up CloudWatch Alarms to notify them when CPU utilization exceeds a certain threshold, enabling proactive scaling of EKS clusters. Meanwhile, AWS X-Ray can be utilized to trace and analyze the performance of specific microservices, aiding in identifying and resolving latency issues within the application.

Considering the dynamic nature of EKS, monitoring and logging are indispensable components of a robust CI/CD pipeline. Amazon CloudWatch and AWS X-Ray empower organizations to gain insights into the performance, health, and efficiency of their EKS applications. By configuring alarms, visualizing metrics, and tracing requests, organizations can proactively manage their EKS clusters, ensuring optimal performance and reliability.

As organizations navigate the complexities of EKS, the monitoring and logging capabilities provided by Amazon CloudWatch and AWS X-Ray offer invaluable insights into the inner workings of their applications. The ability to monitor infrastructure metrics and trace microservices enables organizations to maintain a proactive stance, swiftly addressing issues before they impact end-users. In the evolving landscape of cloud-native application development, effective monitoring and logging are fundamental to achieving success with EKS.

[Identity and access management](#contents.xhtml#sc2_369a)

In the realm of Amazon EKS, identity and access management (IAM) is a critical aspect, ensuring secure and controlled access to resources within the EKS environment. The implementation of IAM roles for pipeline permissions and the integration of Amazon EKS with AWS IAM contribute to a robust security posture, safeguarding organizations against unauthorized access and potential security threats. Implementing IAM roles for secure pipeline permissions involves defining granular permissions for entities within the CI/CD pipeline. Practical steps include creating IAM roles with the necessary policies, assigning permissions based on the principle of least privilege, and configuring role assumptions to ensure secure access. This meticulous approach ensures that only authorized entities can interact with the CI/CD pipeline, mitigating the risk of unauthorized access or inadvertent security breaches.

Amazon EKS seamlessly integrates with AWS IAM, providing a unified approach to identity management within Kubernetes clusters. Organizations can leverage AWS IAM to define and manage Kubernetes RBAC, ensuring that only authenticated and authorized entities can perform specific actions within the EKS environment. Practical steps involve creating IAM roles, mapping them to Kubernetes RBAC roles, and defining policies that govern access to EKS resources.

The collaboration between IAM roles and Amazon EKS within the CI/CD pipeline ensures a secure and controlled workflow. IAM roles define the scope of actions that entities within the pipeline can perform, preventing unauthorized operations and enhancing overall security. Simultaneously, the integration of EKS with AWS IAM extends these identity and access management capabilities to the Kubernetes cluster, establishing a unified and consistent security framework.

This section discusses AWS CLI commands for implementing IAM roles and integrating Amazon EKS with AWS IAM.

[IAM roles for pipeline permissions](#contents.xhtml#sc3_370a)

The following steps are used for implementing IAM roles:

1.  Create an IAM role for CodeBuild:
    
    aws iam create-role --role-name <your-codebuild-role-name> --assume-role-policy-section file://trust-policy-codebuild.json
    
2.  Attach policies to the CodeBuild role:
    
    aws iam attach-role-policy --role-name <your-codebuild-role-name> --policy-arn arn:aws:iam::aws:policy/AWSCodeBuildDeveloperAccess
    
3.  Create an IAM role for EKS:
    
    aws iam create-role --role-name <your-eks-role-name> --assume-role-policy-section file://trust-policy-eks.json
    
4.  Attach policies to the EKS role:
    
    aws iam attach-role-policy --role-name <your-eks-role-name> --policy-arn arn:aws:iam::aws:policy/AmazonEKSClusterPolicy
    

[Integration of Amazon EKS with AWS IAM](#contents.xhtml#sc3_371a)

To seamlessly integrate Amazon EKS with AWS IAM for controlled access to resources, follow these steps:

1.  Update the EKS cluster configuration:
    
    aws eks update-cluster-config --name <your-cluster-name> --region <your-region> --logging '{"clusterLogging":\[{"types":\["api","audit",  
    "authenticator","controllerManager","scheduler"\],"enabled":true}\]}'
    
2.  Create IAM roles for Kubernetes service accounts:
    
    eksctl create iamserviceaccount --region <your-region> --name <your-service-account-name> --namespace <your-namespace> --cluster <your-cluster-name> --attach-policy-arn arn:aws:iam::aws:policy/AmazonEKSClusterPolicy --approve
    
3.  Define RBAC policies for Kubernetes roles:
    
    kubectl apply -f rbac-policy.yaml
    

Replace placeholders such as <your-codebuild-role-name>, <your-eks-role-name>, <your-cluster-name>, <your-region>, <your-service-account-name>, <your-namespace>, trust-policy-codebuild.json, trust-policy-eks.json, rbac-policy.yaml, and others with your actual values. Adjust the parameters based on your specific use case and security requirements.

Practical examples highlight the application of IAM roles and EKS integration in real-world scenarios. For instance, IAM roles can be configured to grant specific permissions for CodeBuild to pull container images from Amazon ECR and deploy them to an EKS cluster. This level of granularity ensures that each component within the CI/CD pipeline operates with the appropriate permissions, reducing the risk of security vulnerabilities.

Considering the dynamic and multi-faceted nature of EKS environments, IAM roles and AWS IAM integration provide a foundation for robust security practices. By implementing fine-grained permissions, organizations can establish a secure CI/CD pipeline, safeguarding against unauthorized access and potential security breaches. The synergy between IAM roles and EKS integration creates a cohesive and secure IAM framework for organizations embracing cloud-native application development.

[Pipeline orchestration](#contents.xhtml#sc2_372a)

Pipeline orchestration is a pivotal element in the continuous integration and continuous deployment (CI/CD) process, and Amazon EKS leverages the capabilities of AWS CodePipeline for streamlined and automated workflow management. This integration provides organizations with a cohesive and efficient approach to orchestrating the various stages of the CI/CD pipeline, from source code management to deployment on EKS clusters. AWS CodePipeline serves as a central hub for orchestrating the entire CI/CD workflow. It allows organizations to define and visualize the stages of their pipeline, including source code integration, build and test automation, container image management, deployment to EKS, and other relevant processes. This centralized orchestration simplifies pipeline management, making it easier for organizations to monitor, control, and optimize their CI/CD processes.

Trigger mechanisms are essential components of pipeline orchestration, enabling the automated execution of pipeline stages based on specific events or changes in the source code repository. CodePipeline supports a variety of trigger mechanisms, such as changes to the source code repository, webhooks, or manual initiation. These triggers facilitate automation by ensuring that relevant pipeline stages are executed automatically in response to specific events, reducing manual intervention and accelerating the overall deployment process.

API integration further enhances pipeline orchestration by allowing external systems, tools, or services to interact with and trigger CodePipeline executions. This capability opens possibilities for integrating the CI/CD pipeline with other tools in the DevOps toolchain, automating workflows, and enabling end-to-end automation. Organizations can leverage APIs to customize and extend pipeline orchestration, tailoring it to their specific requirements and integrating it seamlessly into their existing development and operations processes.

Practical steps for integrating AWS CodePipeline involve defining the pipeline structure, specifying source code repositories, configuring build and deployment actions, and setting up trigger mechanisms. API integration may involve the use of AWS SDKs or custom scripts to interact with the CodePipeline API, allowing organizations to automate and customize pipeline orchestration according to their needs.

[Define AWS CodePipeline](#contents.xhtml#sc3_373a)

The AWS CLI commands for pipeline orchestration using AWS CodePipeline is as follows:

1.  Create CodePipeline:
    
    aws codepipeline create-pipeline --cli-input-json file://codepipeline-definition.json
    
    Sample codepipeline-definition.json could be as follows:
    
    {
    
    "pipeline": {
    
    "name": "YourCodePipelineName",
    
    "roleArn": "arn:aws:iam::your-account-id:role/service-role/AWS-CodePipeline-Service",
    
    "stages": \[
    
    {
    
    "name": "Source",
    
    "actions": \[
    
    {
    
    "name": "SourceAction",
    
    "actionTypeId": {
    
    "category": "Source",
    
    "owner": "AWS",
    
    "provider": "CodeCommit",
    
    "version": "1"
    
    },
    
    "configuration": {
    
    "RepositoryName": "YourCodeCommitRepo",
    
    "BranchName": "main"
    
    },
    
    "outputArtifacts": \[
    
    {
    
    "name": "SourceOutput"
    
    }
    
    \]
    
    }
    
    \]
    
    },
    
    {
    
    "name": "Build",
    
    "actions": \[
    
    {
    
    "name": "BuildAction",
    
    "actionTypeId": {
    
    "category": "Build",
    
    "owner": "AWS",
    
    "provider": "CodeBuild",
    
    "version": "1"
    
    },
    
    "configuration": {
    
    "ProjectName": "YourCodeBuildProject"
    
    },
    
    "outputArtifacts": \[
    
    {
    
    "name": "BuildOutput"
    
    }
    
    \],
    
    "inputArtifacts": \[
    
    {
    
    "name": "SourceOutput"
    
    }
    
    \]
    
    }
    
    \]
    
    },
    
    {
    
    "name": "Deploy",
    
    "actions": \[
    
    {
    
    "name": "DeployAction",
    
    "actionTypeId": {
    
    "category": "Deploy",
    
    "owner": "AWS",
    
    "provider": "ECS",
    
    "version": "1"
    
    },
    
    "configuration": {
    
    "ClusterName": "YourEKSCluster",
    
    "ServiceName": "YourECSService",
    
    "FileName": "imagedefinitions.json"
    
    },
    
    "inputArtifacts": \[
    
    {
    
    "name": "BuildOutput"
    
    }
    
    \]
    
    }
    
    \]
    
    }
    
    \]
    
    }
    
    }
    
2.  Start pipeline execution:
    
    aws codepipeline start-pipeline-execution --name YourCodePipelineName
    

[Trigger mechanisms](#contents.xhtml#sc3_374a)

To seamlessly integrate Amazon EKS with AWS IAM for controlled access to resources, follow these steps:

1.  Update the EKS cluster configuration using the aws eks update-cluster-config command.
    
2.  Create IAM roles for Kubernetes service accounts with the eksctl create iamserviceaccount command, attaching the required policies. 
    
3.  Define RBAC policies for Kubernetes roles using kubectl apply -f rbac-policy.yaml. Replace placeholders like <your-codebuild-role-name>, <your-eks-role-name>, <your-cluster-name>, <your-region>, <your-service-account-name>, <your-namespace>, trust-policy-codebuild.json, trust-policy-eks.json, rbac-policy.yaml, and others with your actual values, adjusting parameters based on your use case and security requirements.
    

Practical examples highlight the application of IAM roles and EKS integration in real-world scenarios, such as configuring roles to grant CodeBuild permissions to pull container images from Amazon ECR and deploy them to an EKS cluster. Pipeline orchestration with AWS CodePipeline as a central hub, including trigger mechanisms like changes to the source code repository (automatically triggered on changes to the CodeCommit repository) or manual trigger using aws codepipeline start-pipeline-execution --name YourCodePipelineName. It also covers API integration for automated orchestration of source code integration, build, container image management, deployment, and other relevant processes. Changes to the source code repository are automatically triggered on changes to the CodeCommit repository. If you want to manually start the pipeline execution, do the following:

aws codepipeline start-pipeline-execution --name YourCodePipelineName

[API integration](#contents.xhtml#sc3_375a)

To get pipeline state, use the following:

aws codepipeline get-pipeline-state --name YourCodePipelineName

To list pipelines:

aws codepipeline list-pipelines

Replace placeholders such as YourCodePipelineName, your-account-id, YourCodeCommitRepo, main, YourCodeBuildProject, YourEKSCluster, YourECSService, and imagedefinitions.json with your actual values. Adjust the parameters based on your specific use case and security requirements. Real-world examples showcase the application of pipeline orchestration in diverse scenarios. For instance, organizations can set up CodePipeline to trigger a deployment to an EKS cluster whenever changes are pushed to the main branch of the source code repository. API integration could involve using a custom script to initiate pipeline executions based on external events, such as the successful completion of a pre-deployment validation process.

Considering the dynamic nature of modern software development, pipeline orchestration is crucial for achieving agility, efficiency, and reliability. The integration of AWS CodePipeline with Amazon EKS provides organizations with a robust solution for orchestrating their CI/CD processes. By leveraging trigger mechanisms and API integration, organizations can automate and customize their pipeline orchestration, adapting it to the specific needs of their development workflows.

[Conclusion](#contents.xhtml#sc2_376a)

Implementing robust CI/CD practices is a cornerstone for achieving agility, efficiency, and reliability in the delivery of applications on Amazon Elastic Kubernetes Service (EKS). The utilization of AWS services throughout the CI/CD pipeline empowers organizations to establish end-to-end automation, enhancing the entire software development lifecycle. This approach facilitates the seamless integration of various stages, from source code management and build processes to deployment on Amazon EKS clusters.

Through effective CI/CD practices, organizations can streamline development workflows, reducing manual interventions and accelerating the release cycles of their applications. The automation offered by CI/CD not only speeds up the delivery process but also ensures consistency and repeatability, mitigating the risk of errors associated with manual procedures. This results in more efficient development practices and a faster time-to-market for applications running on EKS.

Moreover, the insights gained through testing and monitoring within the CI/CD pipeline are invaluable. Continuous testing helps identify potential issues early in the development process, ensuring the reliability and functionality of applications on EKS. Continuous Monitoring provides real-time visibility into the health and performance of EKS clusters, enabling organizations to proactively address any anomalies and optimize resource utilization. These insights contribute to the creation of more robust and resilient applications, aligning with the dynamic nature of EKS environments.

Security remains a paramount concern in the CI/CD process and leveraging AWS services allows organizations to maintain a secure development and deployment environment. AWS services such as AWS IAM facilitate the implementation of security best practices, ensuring that only authorized entities have access to critical resources. This integrated security approach aligns with the shared responsibility model, where AWS manages the security of the cloud infrastructure, and organizations are responsible for securing their applications in the cloud.

As the capabilities of AWS services and CI/CD practices continue to evolve, the integration of CI/CD into EKS environments is expected to become even more streamlined. Continuous improvements and updates to AWS offerings, coupled with a growing ecosystem of CI/CD tools and practices, will contribute to making the CI/CD integration process more seamless and efficient. This evolution allows organizations to stay at the forefront of best practices, optimizing their CI/CD pipelines for the unique demands of cloud-native application development on Amazon EKS.

[Questions](#contents.xhtml#sc2_377a)

1.  Which AWS service enables Git-based source control for code?
    
2.  What are the benefits of canary deployments on EKS?
    
3.  How does AWS X-Ray help with testing applications on EKS?
    
4.  What IAM capability helps manage access to EKS resources?
    
5.  Which service orchestrates the pipeline workflow?
    

[Exercises](#contents.xhtml#sc2_378a)

1.  Set up a CodeCommit repository.
    
2.  Perform a blue/green deployment with CodeDeploy.
    
3.  Create a CloudWatch alarm for EKS cluster metrics.
    

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 19GitOps Workflows with Amazon EKS](#contents.xhtml#ch19a)

[Introduction](#contents.xhtml#sc2_379a)

GitOps has risen as a transformative paradigm reshaping infrastructure and application management. This chapter explores implementing GitOps best practices within Amazon EKS, delving into foundational principles like declarative configurations in Git repositories. It further examines key components and practices for a robust GitOps strategy on Amazon EKS. A critical focus is placed on GitOps tools, emphasizing Argo CD and Flux for synchronizing Git repositories with EKS clusters. The narrative compares and considers the right tool choice for informed decisions. Monitoring practices, essential in GitOps, are scrutinized next, introducing Prometheus and Grafana setup commands for tracking EKS health and performance. This ensures proactive issue identification and addresses modern cloud-native practices.

Infrastructure abstractions, represented by Crossplane and KubeVela, are explored in-depth, elucidating how they abstract and streamline resource management for efficient and scalable GitOps. The narrative extends to Internal Developer Platforms (IDPs), underscoring their role in enhancing the development lifecycle. IDPs, complemented by Crossplane and KubeVela, facilitate developers focusing on application logic while GitOps efficiently manages underlying infrastructure. This comprehensive chapter establishes GitOps' importance within Amazon EKS, providing practical instructions with commands for implementation intricacies. It serves as a beacon for organizations seeking optimization in cloud-native application development and delivery workflows, positioning GitOps on EKS as a strategic imperative for thriving in the evolving cloud computing landscape.

[Structure](#contents.xhtml#sc2_380a)

This chapter contains the following topics:

*   Foundations of GitOps
*   GitOps tools and frameworks
*   Importance of GitOps tooling
*   Internal Developer Platforms
*   Monitoring and observability
*   Best practices in GitOps

[Objectives](#contents.xhtml#sc2_381a)

This chapter aims to establish a solid understanding of GitOps foundations on AWS, exploring core concepts and practices for successful implementation using AWS services. It provides step-by-step instructions for initiating a GitOps workflow within cloud-native application development. The chapter explores various GitOps tools, conducting a comparative analysis of options like Argo CD and Flux, equipping users with insights for informed tool selection, and emphasizing effective configuration management practices. It examines the integration of Crossplane and KubeVela within IDPs, elucidating how these tools streamline infrastructure and application abstractions for efficient and collaborative development environments. The chapter underscores the significance of monitoring and observability in GitOps, providing detailed guidelines and commands for implementing monitoring using Prometheus and Grafana. Finally, it encapsulates GitOps best practices across various domains, offering clear and actionable instructions for enhancing GitOps strategies, empowering users with comprehensive knowledge and practical skills for successful GitOps implementation on AWS.

[Foundation of GitOps](#contents.xhtml#sc2_382a)

GitOps stands at the forefront of modern infrastructure management, offering a cutting-edge and efficient approach, especially within the AWS ecosystem. At its core, GitOps revolves around the fundamental principles of declaring and perpetually maintaining the desired state of a system through version-controlled configurations. This practice is predominantly facilitated through Git repositories, which serve as the centralized hub for storing, managing, and tracking changes to the infrastructure code. In the context of AWS, GitOps leverages the robust capabilities of AWS services to create a cohesive and powerful environment for managing infrastructure. The methodology aligns seamlessly with the AWS philosophy, emphasizing scalability, flexibility, and automation. By adhering to GitOps principles on AWS, organizations can achieve a range of benefits, including increased collaboration, improved transparency, and heightened operational efficiency.

The foundations of GitOps on AWS are anchored in a set of key principles and practices designed to create a streamlined and automated workflow. This begins with the initiation of a Git repository using AWS CodeCommit, providing a secure and fully managed Git service integrated into the AWS ecosystem. This repository becomes the central repository for storing infrastructure code, enabling version control, collaboration, and auditability. The integration of Amazon EKS into the GitOps workflow further strengthens the foundations. AWS EKS provides a managed Kubernetes service, seamlessly abstracting the complexities of Kubernetes cluster deployment and management. This integration empowers users to define and maintain the desired state of Kubernetes clusters efficiently.

A vital aspect of GitOps on AWS is the choice of GitOps tools, such as Argo CD or Flux. These tools orchestrate the deployment and synchronization of Kubernetes configurations stored in the Git repository, ensuring that the actual state aligns with the declared state. Helm charts or YAML manifests are utilized to configure and deploy these tools onto the EKS cluster. The GitOps lifecycle involves continuous integration and continuous deployment (CI/CD) pipelines facilitated by AWS CodePipeline and AWS CodeBuild. These services automate the testing, validation, and deployment of changes to the EKS cluster, promoting a consistent and reliable workflow. AWS CodeDeploy further enhances this process by automating rolling updates, minimizing downtime, and ensuring the stability of the Kubernetes environment. Begin by initializing a Git repository for your GitOps workflow. In the AWS environment, you can use AWS CodeCommit to create a repository:

aws codecommit create-repository --repository-name my-gitops-repo

Next, leverage Amazon EKS to set up your Kubernetes cluster, ensuring that it aligns with your desired infrastructure state. Follow the official AWS documentation to create an Amazon EKS cluster. Choose a GitOps tool, such as Argo CD or Flux, and deploy it onto your EKS cluster. Using Helm charts or YAML manifests, configure the tool to point to the CodeCommit repository where your Kubernetes manifests are stored. Define the desired state of your Kubernetes cluster by creating or modifying Kubernetes manifests. Commit these manifests to the AWS CodeCommit repository:

git add

git commit -m "Define Kubernetes manifests"

git push origin master

Implement a CI/CD pipeline using AWS CodePipeline and AWS CodeBuild. Configure the pipeline to trigger on changes to the CodeCommit repository, run tests using CodeBuild, and deploy changes to the EKS cluster. Automate infrastructure updates using AWS CodeDeploy. Integrate CodeDeploy into your GitOps workflow to facilitate rolling updates and ensure zero-downtime deployments:

aws deploy create-application --application-name my-gitops-app

Leverage AWS Identity and Access Management (IAM) to enforce access controls. Define IAM policies that restrict access to the CodeCommit repository and the EKS cluster, ensuring secure collaboration:

aws iam create-policy --policy-name my-gitops-policy --policy-document file://iam-policy.json

Integrate AWS CloudWatch for monitoring your EKS cluster. Configure CloudWatch to provide insights into the health and performance of the Kubernetes infrastructure:

aws eks update-cluster-config --name my-eks-cluster --logging '{"clusterLogging": \[{"types": \["api", "audit", "authenticator", "controllerManager", "scheduler"\]}\]}' --region us-west-2

Enforce the principles of Infrastructure as Code (IaC) using AWS CloudFormation or Terraform. Define AWS resources as code and manage them alongside Kubernetes manifests in the Git repository. These foundational steps lay the groundwork for implementing GitOps on AWS, establishing an automated and efficient workflow for managing Kubernetes infrastructure.

[GitOps tools and frameworks](#contents.xhtml#sc2_383a)

After successfully setting up your Amazon EKS cluster, the integration of GitOps tooling emerges as a pivotal phase in optimizing the management of Kubernetes configurations. This transition marks a shift towards an efficient, automated, and version-controlled workflow, enhancing the overall reliability and maintainability of your EKS environment. The exploration of GitOps in this context involves a comprehensive examination of two noteworthy tools, Argo CD and Flux. These GitOps tools play a fundamental role in automating the deployment, monitoring, and synchronization of Kubernetes configurations, contributing to a seamless operational experience.

Argo CD, as one of the highlighted GitOps tools, brings a declarative and continuous delivery approach to Kubernetes. It stands out for its user-friendly web interface, offering visibility into the state of applications and supporting advanced deployment strategies. Flux, on the other hand, emphasizes simplicity and automation, continuously monitoring Git repositories for changes and automatically updating the EKS cluster accordingly. The choice between Argo CD and Flux requires careful consideration of factors such as ease of use, extensibility, integration capabilities, community support, and the complexity of deployment needs. Considering these aspects, organizations must weigh the trade-offs and preferences of their development and operations teams when selecting the most suitable GitOps tool for their EKS environment. Both tools offer unique features and strengths, making it essential to align the choice with specific organizational requirements.

Additionally, as part of this exploration, it is crucial to underscore the significance of configuration management within Git repositories. Git repositories serve as the central hub for storing Kubernetes manifests and application configurations. This approach ensures that desired states are versioned and controlled, promoting collaboration and traceability. Efficient configuration management involves adhering to best practices in branching strategies, commit messages, versioning, and documentation within the Git repository. These practices not only facilitate a structured workflow but also contribute to the overall transparency and auditability of changes made to the EKS cluster's configurations. To summarize, the integration of GitOps tooling, exemplified by Argo CD and Flux, is a critical step post-establishment of an Amazon EKS cluster. The choice between these tools should be informed by careful consideration of various factors. Moreover, emphasizing effective configuration management within Git repositories is vital for maintaining a well-organized, version-controlled, and auditable history of configurations. This comprehensive approach ensures that your EKS environment is not only efficiently managed but also adheres to best practices in the rapidly evolving landscape of Kubernetes operations.

[Importance of GitOps tooling](#contents.xhtml#sc2_384a)

GitOps tooling holds immense significance in modern IT operations, particularly for managing Kubernetes configurations. Its primary strength lies in the streamlined and automated deployment processes it facilitates. Once an EKS cluster is established, GitOps serves as a crucial bridge between the envisioned infrastructure state, meticulously defined in Git repositories, and the real-time state operationalized on the EKS cluster. This approach not only enhances collaboration among teams but also fosters transparency, as every configuration change is documented and versioned in Git. The comprehensive nature of GitOps ensures a robust version control system, capturing the entire configuration lifecycle, and providing a reliable audit trail for tracking changes and ensuring the consistency of the EKS cluster's infrastructure.

[Exploration of GitOps tools](#contents.xhtml#sc3_385a)

This section delves into popular GitOps tools like Argo CD and Flux, conducting a comparative analysis. It highlights Argo CD's features, such as auto-sync, progressive rollouts, and robust access controls. For Flux, the focus is on its seamless integration with Git providers and declarative configuration approach. The aim is to equip users with insights to choose the right GitOps tool based on their specific requirements.

[Argo CD](#contents.xhtml#sc4_386a)

Argo CD stands out as a powerful GitOps tool, offering a declarative and continuous delivery approach for Kubernetes. It not only simplifies the application deployment process but also provides a centralized and intuitive web interface for managing applications and monitoring their status. Argo CD excels in its support for advanced deployment strategies, making it suitable for organizations with complex application deployment needs. The tool’s ability to handle Helm charts and custom resources enhances its versatility. To deploy Argo CD on your EKS cluster, initiate the following commands:

kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

Argo CD provides not only a visually intuitive interface for managing applications but also supports advanced deployment strategies. This makes it suitable for organizations with complex requirements. Once you log in to the ArgoCD, you will be presented with a UI, as shown in the following screenshot:

![](images/Figure_19.1.png)

Figure 19.1: ArgoCD dashboard post login

[Flux](#contents.xhtml#sc4_387a)

Flux, known for its simplicity and automation, provides an alternative GitOps solution. It continuously monitors Git repositories for changes, automatically applying updates to the EKS cluster. While Flux may lack an extensive web interface, its minimalist design makes it easy to integrate into existing workflows. Flux is particularly appealing for organizations seeking a straightforward GitOps solution without the need for elaborate features, making it well-suited for smaller projects or teams. Flux, focusing on automation and reconciliation, offers a minimalist GitOps tool for Kubernetes. To deploy Flux on your EKS cluster, use the following commands:

kubectl create namespace flux

fluxctl install --namespace=flux | kubectl apply -f -

Flux operates by continuously monitoring a specified Git repository for changes and automatically applying updates to the cluster, embodying a straightforward and minimalist approach.

[Considerations for choosing the right tool](#contents.xhtml#sc3_388a)

When choosing the right GitOps tool, several considerations come into play. Here are some key factors to evaluate. When selecting a GitOps tool like Argo CD or Flux, organizations should evaluate factors such as ease of use, extensibility, integration capabilities, community support, and the desired balance between complexity and simplicity. Argo CD caters to larger, complex deployments with advanced features, while Flux excels in simplicity for streamlined GitOps workflows. Ultimately, the choice depends on an organization's specific requirements and priorities. Let us take a deeper look into it:

*   Ease of use: 
    *   Argo CD: Offers a feature-rich web interface that simplifies application management and monitoring.
    *   Flux: Known for its simplicity and minimalistic design, making it easy to set up and integrate into workflows.
*   Extensibility: 
    *   Argo CD: Highly extensible with support for Helm charts, Rollouts, and hooks, accommodating diverse deployment scenarios.
    *   Flux: Emphasizes simplicity and core GitOps functionality, potentially appealing to those with straightforward use cases.
*   Integration capabilities: 
    *   Argo CD: Integrates well with various CI/CD tools, Git repositories, and Kubernetes-native resources.
    *   Flux: Excellently integrates with Git, aligning with organizations that heavily rely on Git-based workflows.
*   Community support: 
    *   Argo CD: Boasts a robust and active community, contributing to continuous improvement and providing strong support.
    *   Flux: Although its community may be smaller, Flux is steadily growing and is suitable for those who prefer a focused user base.
*   Complexity versus simplicity: 
    *   Argo CD: Suited for larger organizations with complex deployment needs and a desire for advanced features.
    *   Flux: Ideal for smaller teams or projects that prioritize simplicity and streamlined GitOps workflows.

[Configuration management with Git repositories](#contents.xhtml#sc3_389a)

Effective configuration management within Git repositories is essential for the success of a GitOps workflow:

*   Branching strategy: Establish a branching strategy that aligns with your development and deployment workflows. Common strategies include feature branches, release branches, and mainline branching.
*   Committing changes: Encourage descriptive commit messages to provide context and aid in understanding the purpose of each change.
*   Versioning and tagging: Implement versioning and tagging strategies to track changes over time. Use tags for significant releases and versions.
*   Pull requests and code reviews: Introduce a robust pull request and code review process to ensure changes are reviewed, tested, and validated before being merged into the main branch.
*   Git hooks: Leverage Git hooks for automation. For instance, pre-commit hooks can enforce code formatting and linting, ensuring consistent quality.
*   Git repository structure: Organize your Git repository with a clear structure, separating Kubernetes manifests, Helm charts, and other configuration files into distinct directories.
*   Documentation: Maintain comprehensive documentation within the repository, outlining the GitOps workflow, branching strategies, and any specific procedures for your team.
*   Monitoring Git repository changes: Implement tools or scripts to monitor Git repository changes, triggering automated CI/CD pipelines and GitOps tooling when updates occur.
*   Git repository security: Apply access controls and permissions within the Git repository to ensure only authorized individuals can make changes.
*   Auditability: Regularly audit and review the Git repository history for transparency and compliance. Git provides an extensive log that can be utilized for tracking changes and identifying potential issues.

[Internal Developer Platforms](#contents.xhtml#sc2_390a)

An Internal Developer Platform (IDP) is a holistic solution designed to optimize the development lifecycle within an organization, offering a unified environment equipped with tools and services that empower developers at every stage of application development. This comprehensive platform ensures a seamless and efficient workflow, fostering collaboration and innovation among development teams. With a focus on simplifying the complexities of infrastructure and application management, an IDP becomes an essential facilitator for achieving streamlined, scalable, and reliable development processes.

Within the ecosystem of an IDP, two standout components, Crossplane and KubeVela, play vital roles in contributing to its success. Crossplane excels in abstracting and managing infrastructure resources through Kubernetes-style APIs, providing a cloud-agnostic approach for consistent provisioning across diverse environments. Meanwhile, KubeVela complements this by offering an application-centric abstraction layer, simplifying the deployment and management of applications within the IDP. Together, these components create a powerful synergy, ensuring that developers can focus on their core task of building and deploying applications while the IDP takes care of orchestrating the underlying infrastructure seamlessly. This symbiotic relationship enhances collaboration, accelerates development cycles, and establishes the IDP as a cornerstone for efficient application development within the organization.

[Crossplane](#contents.xhtml#sc3_391a)

Crossplane is a revolutionary open-source project that extends the Kubernetes ecosystem to address the challenges of managing IaC in diverse cloud and on-premises environments. Serving as a Kubernetes add-on, Crossplane introduces a cloud-agnostic approach, allowing developers to define and manage infrastructure resources using familiar Kubernetes-style APIs. By abstracting the complexities of multi-cloud provisioning, Crossplane facilitates consistent and declarative infrastructure management, enabling organizations to streamline their operations and deploy applications seamlessly across various cloud providers and on-premises infrastructure. You can install Crossplane using the helm:

helm repo add crossplane-stable https://charts.crossplane.io/stable

helm repo update

helm install crossplane crossplane-stable/crossplane --namespace \\

crossplane-system—create-namespace

Verify the pods as below:

kubectl get pods -n crossplane-system

NAME READY STATUS RESTARTS AGE

crossplane-d4cd8d784-ldcgb 1/1 Running 0 54s

crossplane-rbac-manager-84769b574-6mw6f 1/1 Running 0 54s

[Kubevela](#contents.xhtml#sc3_392a)

KubeVela is a groundbreaking open-source project that enhances the Kubernetes experience by introducing an application-centric approach to configuration and deployment. This framework simplifies and accelerates the management of cloud-native applications by abstracting complex configurations into a higher-level, declarative model. KubeVela streamlines the entire application lifecycle, enabling developers to define, deploy, and scale applications seamlessly while maintaining flexibility and compatibility with Kubernetes and cloud-native ecosystems. You can deploy Kubevela using the helm chart, as shown:

helm repo add kubevela https://charts.kubevela.net/core

helm repo update

helm install --create-namespace -n vela-system kubevela kubevela/vela-core --wait

You can enable the UI, and when you try to login, it appears as shown:

![](images/Figure_19.2.png)

Figure 19.2: Kubevela login screen

[Crossplane in the Internal Developer Platform](#contents.xhtml#sc3_393a)

Crossplane plays a vital role in enhancing the capabilities of an IDP. Here are some key contributions of Crossplane in the IDP context. Crossplane abstracts and manages infrastructure resources using Kubernetes APIs, extending Kubernetes' declarative approach to infrastructure provisioning. It enables cloud-agnostic resource provisioning across multiple providers, aligning with multi-cloud IDP environments. By leveraging familiar Kubernetes concepts, Crossplane enhances collaboration between dev and ops teams within the IDP context. Refer to the following points:

*   Infrastructure abstraction: Crossplane plays a crucial role in an IDP by abstracting and managing infrastructure resources using Kubernetes-style APIs. It extends the declarative nature of Kubernetes to the realm of cloud and on-premises infrastructure, allowing developers to define and manage IaC alongside their application code.
*   Cloud-agnostic resource provisioning: One of Crossplane's key features is its cloud-agnostic approach. It supports provisioning and management of resources across various cloud providers, providing a consistent interface for developers regardless of the underlying infrastructure. This capability aligns well with the goals of an IDP, which often involves working in multi-cloud or hybrid cloud environments.
*   Enhanced collaboration: By allowing developers to define infrastructure using familiar Kubernetes concepts, Crossplane promotes collaboration and a shared understanding between development and operations teams. This aligns with the broader goals of an IDP, fostering a collaborative environment where teams can work seamlessly together.

[KubeVela in the Internal Developer Platform](#contents.xhtml#sc3_394a)

KubeVela complements Crossplane in the IDP by providing application-centric abstraction, declarative application delivery, and seamless integration with GitOps workflows, enabling developers to manage applications more efficiently while fostering collaboration and alignment with modern software delivery practices. Refer to the following points:

*   Application-centric abstraction: KubeVela is another valuable component in an IDP, focusing on the abstraction and management of applications themselves. It introduces a higher-level, application-centric abstraction layer on top of Kubernetes. With KubeVela, developers can define not only the infrastructure but also the entire application configuration, including services, components, and their relationships.
*   Declarative application delivery: Similar to Crossplane, KubeVela embraces a declarative approach to application delivery. Developers can specify the desired state of their applications, and KubeVela takes care of orchestrating the necessary resources and configurations to achieve that state. This simplifies the deployment process and aligns with the principles of IaC.
*   GitOps workflows: KubeVela integrates well with GitOps workflows, enabling developers to manage application configurations using version-controlled repositories. This integration enhances traceability, auditability, and collaboration within the IDP.

[Overall impact on the Internal Developer Platform](#contents.xhtml#sc3_395a)

The integration of Crossplane and KubeVela within an IDP fosters consistency across environments, simplifies application deployment, enhances collaboration and efficiency, and provides scalability and flexibility to adapt to diverse infrastructure and application needs, creating a more streamlined and efficient development experience. Refer to the following points:

*   Consistency across environments: Crossplane ensures a consistent infrastructure provisioning experience across various cloud providers, fostering consistency in multi-cloud or hybrid cloud environments.
*   Simplified application deployment: KubeVela simplifies application deployment by abstracting complex configurations, making it easier for developers to manage the entire application lifecycle.
*   Collaboration and efficiency: Together, Crossplane and KubeVela contribute to the overall collaboration and efficiency within an IDP. Developers can focus on writing application code, relying on these tools to manage infrastructure and application configurations seamlessly.
*   Scalability and flexibility: The combination of Crossplane and KubeVela provides scalability and flexibility, allowing an IDP to adapt to diverse infrastructure and application requirements.

In summary, Crossplane and KubeVela are integral components of an Internal Developer Platform, each contributing unique capabilities to simplify infrastructure and application management. Together, they empower development teams to work more efficiently, collaborate effectively, and seamlessly deploy applications across various environments.

[Monitoring and observability in GitOps](#contents.xhtml#sc2_396a)

Implementing monitoring and observability in a GitOps workflow within an Amazon EKS environment is of paramount importance, constituting a critical layer of operational excellence for Kubernetes clusters and associated applications. The dynamic and scalable nature of containerized environments demands a robust monitoring strategy to ensure the seamless functioning of the infrastructure. The goal is not merely to identify and rectify issues but also to proactively glean insights into performance, resource utilization, and potential bottlenecks.

The first step in this journey involves setting up Prometheus and Grafana, foundational tools in the realm of Kubernetes monitoring. Prometheus, known for its scalability and powerful querying capabilities, becomes the backbone of collecting metrics, while Grafana provides an intuitive visualization layer for these metrics. Deploying Prometheus Operator further enhances the management of Prometheus instances, ensuring a standardized and streamlined approach to monitoring. Conceptually, configuring Prometheus resources involves defining custom resources tailored to the specific requirements of your EKS environment. This includes specifying the desired alerting rules, scraping configurations, and retention policies. The subsequent deployment of Grafana complements Prometheus, offering a user-friendly interface for visualizing metrics, creating dashboards, and gaining real-time insights into the state of the Kubernetes clusters.

Accessing the Grafana dashboard, whether through NodePort or LoadBalancer service, becomes the window into the heartbeat of your infrastructure, allowing for proactive monitoring and rapid response to any anomalies. It serves as a centralized hub for visualizing the health and performance of your EKS environment. Transitioning to the implementation of monitoring practices, Kubernetes events become a crucial aspect to observe. Using kubectl get events --all-namespaces provides a quick overview of events across namespaces, aiding in the identification of potential issues or disruptions. This step adds a layer of granularity to the observability strategy.

Instrumenting applications with Prometheus metrics is the next strategic move, providing developers and operators with deeper insights into application-specific performance. Leveraging Prometheus client libraries, such as those available for popular languages like Node.js or Go, integrates seamlessly into application code, enabling the collection of custom metrics tailored to specific use cases. In tandem with application metrics, effective monitoring extends to application logging. Centralized logging solutions, such as Fluent Bit with Amazon CloudWatch or Elasticsearch, ensure that log data is aggregated and easily accessible for analysis. This not only aids in troubleshooting but also contributes to a comprehensive understanding of application behavior. Expanding the purview, AWS CloudWatch metrics come into play for monitoring AWS-specific metrics. Integrating CloudWatch agents within the Kubernetes cluster allows for the collection and visualization of additional data points specific to AWS services, enhancing the holistic monitoring approach.

[Implementing observability](#contents.xhtml#sc3_397a)

Implementing observability is crucial for monitoring the health and performance of your EKS clusters and applications. Here are the steps to set up Prometheus and Grafana for observability in your GitOps workflow:

1.  Setup Prometheus and Grafana: To begin, install Prometheus and Grafana, foundational tools for monitoring Kubernetes clusters, as shown:
    
    kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/aws/deploy.yaml
    
2.  Deploy Prometheus Operator: Deploy the Prometheus Operator to simplify the management of Prometheus instances, as shown:
    
    kubectl create namespace monitoring
    
    kubectl apply -f https://raw.githubusercontent.com/coreos/prometheus-operator/main/bundle.yaml
    
3.  Configure Prometheus resources: Create custom resources to configure Prometheus according to your EKS monitoring requirements, as shown:
    
    kubectl apply -f https://raw.githubusercontent.com/coreos/prometheus-operator/main/example/prometheus-operator-crd/monitoring.coreos.com\_prometheuses.yaml
    
4.  Deploy Grafana: Deploy Grafana for visualizing Prometheus metrics effectively, as shown:
    
    kubectl apply -f https://raw.githubusercontent.com/coreos/prometheus-operator/main/example/prometheus-operator-crd/monitoring.coreos.com\_servicemonitors.yaml
    
5.  Access Grafana dashboard: Access the Grafana dashboard using NodePort or LoadBalancer service for real-time visualization of metrics.
    

By following these steps, you can set up Prometheus and Grafana within your GitOps workflow, enabling comprehensive monitoring and observability of your EKS clusters and applications. This allows you to proactively identify and address issues, ensuring optimal performance and reliability.

[Implementing monitoring](#contents.xhtml#sc3_398a)

Implementing comprehensive monitoring is crucial for ensuring the health and performance of your EKS clusters and applications. Here are some key steps to consider:

*   Implement Kubernetes event monitoring: Use kubectl to monitor Kubernetes events, gaining insights into potential issues.
    
    kubectl get events --all-namespaces
    
*   Instrument applications with Prometheus metrics: Instrument your applications with Prometheus metrics using client libraries for comprehensive insights.
    
    \# Example for Node.js with Prometheus client library
    
    npm install prom-client
    
*   Implement application logging: Enhance observability by implementing centralized logging for applications using AWS services like Amazon CloudWatch or Amazon Elasticsearch.
    
    \# Example for Fluent Bit logging agent
    
    kubectl apply -f https://raw.githubusercontent.com/fluent/fluent-bit-kubernetes-logging/main/output/elasticsearch/fluent-bit-configmap.yaml
    
*   Utilize AWS CloudWatch metrics: Leverage AWS CloudWatch for monitoring AWS-specific metrics, ensuring a holistic view of your infrastructure.
    
    \# Example for creating a CloudWatch agent DaemonSet
    
    kubectl apply -f https://raw.githubusercontent.com/aws-samples/amazon-cloudwatch-container-insights/latest/k8s-deployment-manifest-templates/deployment-mode/daemonset/container-insights-monitoring/cwagent/cwagent-fluentd-quickstart.yaml
    
*   Implement alerts and notifications: Ensure timely response to issues by setting up alerting rules in Prometheus and Grafana, and configure notifications through tools like AWS SNS.
    
    \# Example for creating a Prometheus AlertManagerConfig
    
    kubectl apply -f https://raw.githubusercontent.com/prometheus/alertmanager/main/doc/example/simple-config/alertmanager.yaml
    

By following these detailed steps, you establish a comprehensive monitoring and observability framework for your GitOps-managed infrastructure on Amazon EKS. This approach ensures that you not only have the necessary tools in place but also understand the broader context and concepts behind effective monitoring and observability practices within the AWS Kubernetes environment.

[Best practices in GitOps](#contents.xhtml#sc2_399a)

Implementing GitOps with Amazon EKS involves adhering to best practices to ensure a secure, efficient, and reliable deployment workflow. Here are detailed instructions and working commands for key GitOps best practices:

*   Infrastructure as Code: Leverage tools like AWS CloudFormation or Terraform to define and manage your EKS infrastructure as code. This enables versioning, collaboration, and consistent provisioning.
*   Git repository structure: Organize your Git repository with a clear structure. Have separate directories for Kubernetes manifests, infrastructure configurations, and any other relevant files. This aids in maintainability and ease of navigation.
*   Immutable infrastructure: Embrace the concept of immutable infrastructure by treating your infrastructure as code and avoiding direct modifications. Use tools like eksctl to update the EKS cluster configuration.
    
    eksctl create cluster -f cluster-config.yaml
    
*   Branching strategy: Adopt a branching strategy in your Git repository, such as Gitflow, to manage different environments, releases, and feature branches. This ensures a structured and controlled promotion of changes.
    
    git checkout -b feature-branch
    
*   Continuous integration: Implement continuous integration (CI) pipelines to automate the testing and validation of changes before deployment. Tools like AWS CodePipeline or Jenkins can be configured to trigger deployments upon successful CI builds.
*   Secrets management: Securely manage and store secrets using tools like AWS Secrets Manager or HashiCorp Vault. Integrate these solutions into your GitOps workflow to ensure sensitive information is handled securely.
*   Rolling updates and rollbacks: Plan for rolling updates to minimize downtime during deployments. Use commands like kubectl set image to update container images, and conduct rollbacks if needed.
    
    kubectl set image deployment/my-app my-app=my-image:tag
    
*   GitOps tools integration: Integrate GitOps tools like Argo CD or Flux into your workflow for automated synchronization of Git repository changes with the EKS cluster. Configure the tools to monitor specific repositories and trigger deployments accordingly.
*   Immutable release artifacts: Create immutable release artifacts for applications and infrastructure configurations. This ensures that the exact versions deployed in staging and production environments are identical, reducing the risk of inconsistencies.
    
    git tag -a v1.0 -m "Release version 1.0"
    
*   Monitoring and observability: Implement monitoring and observability practices as part of GitOps. This is discussed in detail in the preceding section.

Incorporating these best practices into your GitOps workflow with Amazon EKS establishes a solid foundation for managing Kubernetes configurations, promoting collaboration, and ensuring the reliability and security of your cloud-native applications. These instructions, combined with working commands, provide a practical section for implementing GitOps in an AWS EKS environment.

[Conclusion](#contents.xhtml#sc2_400a)

In this chapter, readers gained a comprehensive understanding of implementing GitOps for cloud-native applications on Amazon EKS. The section provided a holistic framework encompassing critical best practices and powerful integrations to optimize GitOps workflows. Readers learned about the foundations of GitOps on AWS, including essential concepts and practices for successful implementation using AWS services like CodeCommit, EKS, and CI/CD tools. The chapter delved into popular GitOps tools like Argo CD and Flux, conducting a comparative analysis to help readers make informed decisions when selecting the right tool based on factors such as ease of use, extensibility, integration capabilities, community support, and the desired balance between complexity and simplicity.

Additionally, the section explored the integration of Crossplane and KubeVela within IDPs. Readers gained insights into how Crossplane abstracts and manages infrastructure resources, enabling cloud-agnostic resource provisioning and fostering collaboration between development and operations teams. Moreover, they learned about KubeVela's application-centric abstraction, declarative application delivery, and seamless integration with GitOps workflows, further enhancing the development experience within an IDP. In the subsequent chapters, we will focus on the best practices to be followed by applying what we learned here.

[Questions](#contents.xhtml#sc2_401a)

1.  What are the core principles of GitOps? How do they benefit Kubernetes operations?
2.  Explain the steps involved in setting up Amazon EKS clusters for GitOps workflows.
3.  Compare and contrast two GitOps tools suitable for Amazon EKS, highlighting their key features.
4.  How does GitOps facilitate continuous delivery in Kubernetes environments?
5.  Why is monitoring and observability crucial in GitOps workflows, and what are the best practices?

[Exercises](#contents.xhtml#sc2_402a)

1.  Set up a basic Amazon EKS cluster and configure it for GitOps using a tool of your choice.
2.  Create a simple CI/CD pipeline for a Kubernetes application, integrating GitOps principles.
3.  Implement monitoring and observability practices in a GitOps workflow for an EKS cluster.

# [CHAPTER 20Backup and Disaster Recovery with Amazon EKS](#contents.xhtml#ch20a)

[Introduction](#contents.xhtml#sc2_403a)

In the dynamic landscape of containerized applications and Kubernetes orchestration, the adoption of Amazon Elastic Kubernetes Service (EKS) marks a significant leap toward streamlined operations. However, as organizations increasingly rely on Amazon EKS to run mission-critical applications, the need for reliable backup and disaster recovery practices becomes paramount. This section serves as a comprehensive resource, offering a thorough exploration of proven strategies and methods for implementing backup and disaster recovery with Amazon EKS. Commencing with foundational concepts, the section establishes a solid understanding of the intricacies involved in architecting durable systems tailored to organizational requirements. Acknowledging the criticality of business continuity, this chapter takes a layered approach, covering various techniques for data protection at different levels: application, cluster, and infrastructure. Readers are guided through the intricacies of backup strategies, ensuring a holistic grasp of the methodologies needed to safeguard against disruptions and data loss.

Moreover, the chapter explores disaster recovery models, shedding light on options to achieve desired Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs). Through real-world examples and code snippets, readers gain practical insights, enabling them to confidently navigate the complexities of building robust and resilient Amazon EKS deployments. This multifaceted approach ensures that readers not only comprehend the theoretical underpinnings of backup and disaster recovery but also acquire hands-on mastery, making them adept at implementing these strategies effectively within the Amazon EKS ecosystem.

[Structure](#contents.xhtml#sc2_404a)

In this chapter, we will cover the following topics:

*   Fundamentals of backup and disaster recovery
*   EKS backup and restore approaches
*   Application-centric data protection
*   Infrastructure and cluster backup practices
*   AWS Fault Injection Simulator
*   Disaster recovery models with Amazon EKS
*   Validating and testing backup DR strategies
*   Monitoring backup and DR operations

[Objectives](#contents.xhtml#sc2_405a)

Upon completing this chapter, readers will attain a comprehensive skill set enabling them to distinguish between backup and disaster recovery, articulating their respective common objectives. The section empowers readers to perform detailed comparisons of diverse backup and restore methods applicable to Amazon EKS, facilitating an informed selection of strategies tailored to their specific requirements. Furthermore, readers will acquire the expertise to design a robust application-level data protection scheme, ensuring the safeguarding of critical application data beyond cluster-level considerations. The chapter extends its focus to practical implementation, guiding readers through the intricacies of executing cluster configuration backups and infrastructure backups within the Amazon EKS environment.

A significant aspect of the chapter lies in enabling readers to make informed decisions on suitable disaster recovery models that align with varying recovery time objective (RTO) and recovery point objective (RPO) needs. By providing insights into validation and testing methodologies, the chapter ensures readers possess the skills to assess and refine their backup and disaster recovery processes proactively.

Lastly, readers will learn how to monitor and audit backup/restore jobs for compliance, ensuring ongoing adherence to best practices and industry standards. This comprehensive skill set equips readers not only with theoretical knowledge but also with practical capabilities, empowering them to confidently implement, validate, and monitor robust backup and disaster recovery strategies within their Amazon EKS deployments.

[Fundamentals of backup and disaster recovery](#contents.xhtml#sc2_406a)

Backup and disaster recovery may seem synonymous, but important distinctions exist. Backup involves creating secondary copies of data to restore after loss or corruption. Disaster recovery focuses on maintaining business functionality when adverse events disrupt operations. Effective strategies incorporate both data protection and continuity planning. AWS defines RTO and RPO as key metrics. RTO represents the target duration to recover applications after an outage to acceptable service levels. RPO indicates the maximum permissible data loss in terms of time since the last recoverable backup. Aligning backup schemes with desired RTOs and RPOs is crucial. For a billing application, an RTO of 24 hours and an RPO of 1 hour may suffice. A real-time IoT analytics platform will demand far lower targets.

AWS offers native and third-party tools for comprehensive backup across application, compute, database, storage, and network layers. EKS backup safeguards cluster configuration data stored in etcd. Compute resources utilize EBS snapshots or AMI images, while managed databases leverage point-in-time recovery. Each layer warrants tailored data protection and continuity schemes. Testing and validation verify that recovery strategies meet expectations. Simulating different failure scenarios helps evaluate recovery workflows. RTO can be measured from the outage to the restoration of core functionality. Comparing data post-recovery against backups assists in determining data loss to calculate RPO. Proper monitoring provides visibility into backup operations, while audit logs help ensure regulatory compliance. AWS Config delivers history and changes to resource configurations. Backup solution metrics should be tracked in CloudWatch Dashboards.

Some key AWS CLI commands are:

*   Check RTO/RPO for DynamoDB PITR:
    
    aws dynamodb describe-continuous-backups --table-name mytable
    
*   Test compute instance recovery:
    
    aws ec2 recover-instances --instance-id i-abcd1234
    
*   Restore EBS volume from snapshot:
    
    aws ec2 restore-volume --snapshot-id snap-abcd5678
    

Robust backup and disaster recovery hinges on understanding three key parameters: RTO, RPO, and the scope of failures being protected against. Each application and workload will have unique RTO and RPO thresholds aligned to technical architectures and business priorities. Scope consideration calls for structured risk assessment, planning for events from isolated issues like erroneous data edits to large outages stemming from natural disasters or infrastructure loss. With cloud-based systems, the elimination of single points of failure is imperative. Deploying resources across multiple physical facilities and AZs provides insulation against failures localized to one facility. Architecting multi-AZ or multi-Region redundancy meets stringent uptime needs. Tools like AWS Backup and AWS Organizations help centralize management and enable policies to propagate changes across multiple accounts.

Cost optimization efforts should strike a balance with investments in business continuity. Strategies like tiered storage, data lifecycle management, and comprehensive retention policies can reduce unnecessary overhead. Regular testing, benchmarking RTO/RPO, access control/encryption reviews, monitoring, and thorough documentation ensure durability aligns with SLA commitments. These measures optimize costs while maintaining resilience for Amazon EKS-powered applications, workloads, and business processes.

[EKS backup and restore approaches](#contents.xhtml#sc2_407a)

Amazon EKS stores critical cluster data and configuration information within etcd, a distributed key-value store. EKS provides native backup tools along with integration with community-driven open-source tools like Velero. The EKS native backup leverages AWS Backup to deliver point-in-time snapshots stored in Amazon S3. This handles scheduling and lifecycle management to reduce overhead. Restores instantiate a new Amazon EKS cluster, retrieving backed up data to recreate worker nodes and control plane configurations. AWS CLI automation streamlines backup and recovery workflows.

Velero offers an open-source alternative, focusing on portability through backups integrated into container images. Scheduled Velero jobs produce backup artifacts consumable across cloud platforms and on-premise clusters. Velero backups encompass wider app data, including volumes, configurations, and namespaces. Advanced customization of retention policies, hooks, schedules, and filters suits diverse environments. Choosing between EKS native backup or community tools depends on several factors. Native options simplify infrastructure dependencies. Open-source tools spur richer functionality for complex policies and cross-platform objectives. Cluster sizes, recovery requirements, and application-integration all influence design decisions. A layered approach can be effective, leveraging EKS native backups for networking and base OS, complemented by Velero for stateful application data residing on PVCs.

Striking a balance calls for understanding trade-offs between native and third-party tools. Recreate workflows lean towards native options but can increase RTO relative to in-place restores. Open-source tooling fosters portability for multi or hybrid cloud objectives. Cost, implementation complexity, and managing infrastructure dependencies also weigh on decisions.

With core building blocks in place via native or customized toolchain, automated testing, and validation should run on fixed intervals to verify viability. Testing real recovery across Regions or accounts unearths gaps in documentation, access roles, or network configurations that only surface when actually rebuilding in a crisis scenario outside normal domains. Conducting true cutover style recovery tests hardens capabilities to meet demanding RTO/RPO commitments to customers relying on Amazon EKS infrastructure.

[Application-centric data protection](#contents.xhtml#sc2_408a)

Application data constitutes a critical tier within a comprehensive backup and disaster recovery strategy for EKS. While network, compute, and storage layers provide foundational infrastructure durability, protecting the application state ensures meaningful recoverability aligned to end-user experiences. EKS applications build on managed Kubernetes primitives including Deployments, StatefulSets, DaemonSets and PersistentVolumes. Kubernetes storage abstraction allows coupling stateful apps to network volumes or cloud volumes services like Amazon EBS. Data protection scopes integrate persistent storage snapshots with higher-level application aware semantics.

AWS offers an App2Container model for lifting legacy apps into container format while preserving data stores. This expands data protection integration capabilities allowing legacy databases like Oracle/SQL Server to snapshot via native tooling. Purpose-built applications on EKS optimize protection by persisting state via managed AWS data stores featuring backup capabilities and point-in-time recovery. Third party tools like Kasten K10 extend deeper into application topology awareness, automating policy-based actions that trigger downstream protection workflows encompassing data, configurations, and app interdependencies. Indexing backups with catalogs aids rapid search and restoration granularity down to keyspace or document-level detail.

Some key AWS CLI commands are:

*   Take RDS DB snapshot: 
    
    aws rds create-db-snapshot
    
*   List all snapshots for DB:
    
    aws rds describe-db-snapshots
    
*   Restore from DB snapshot:
    
    aws rds restore-db-instance-from-db-snapshot
    

Application data traverses beyond storage to include configurations, logs, communications, and operational analytics that constitute a holistic state. Adopting layered data protection spanning storage, data stores, and app-centric tools prevents fragmented visibility that hampers rapid, coherent restoration when urgency strikes. Thinking beyond infrastructure to incorporate state management reconciles RTO objectives with application service quality experienced by end users that depend on the resilient operations of systems running on Amazon EKS. The blend of application portability, infrastructure immutability, and loosely coupled persistence models unique to containerized environments furnishes reliable building blocks for next-generation data protection. However, minding organizational governance, compliance, and security requirements remains imperative as protection toolchains expand in capability. Fortifying disaster preparedness procedures without compromising oversight carries equal weight for sustainable operations at scale.

[Infrastructure and cluster backup practices](#contents.xhtml#sc2_409a)

Robust cluster protection relies on the foundations of core infrastructure resilience. Compute, database, networking, and security layers constitute interdependent pillars that underpin the reliable functioning of Amazon EKS. Employing battle-tested services fortified by mature continuity capabilities prepares for uncertainties ahead. Amazon EBS persistence upholds EC2 worker node resilience via snapshot-based volume backups. Retention policies govern backup cycles, while snapshot automation aids instance recovery workflows. For on-demand capacity, ASG worker node groups also integrate with EBS, providing durable scaling. S3 is for durable object storage, and CloudFront is for content edge networking, which also carries native continuity.

RDS database services simplify data protection by building in automated backups with user-defined retention periods. Multi-AZ deployments prevent regional database failures through synchronous replica updates across AZ. Point-in-time restore fulfils granular restore use cases. Network security calls for NACL/security group backup plus identity components such as IAM roles, policies, and federated access configurations that constitute access provisioning. DNS and load balancing stack recovery ensures traffic continuity post-recovery. Infrastructure interdependency mandates structured impact analysis when failures unfold. Tracing upstream and downstream influence across integrated systems throughout recovery illuminates systemic risks that add delays. Modern architectures weave complex yet agile resource graphs via services and autoscaling capabilities that demand thoughtful orchestration tactics when restoring large-scale disruptions.

Learning from past executed recoveries and continuously rehearsing updated playbooks keeps restoration workflows evergreen. Chaos experiments that simulate component or dependency failures unearth latent assumptions before outages surface them. Integrating learnings into enhanced recovery processes, aided by preventative security plus foundational SLAs across critical services, furnishes reliable infrastructure that empowers Amazon EKS to deliver applications matched to business demands.

[AWS Fault Injection Simulator](#contents.xhtml#sc2_410a)

The AWS Fault Injection Simulator provides a managed service to stress test AWS workloads through controlled experiments. By surfacing failure scenarios in pre-production environments, teams gain confidence in operational resiliency ahead of critical phases. The Fault Injection Simulator introduces faults across a breadth of downstream dependency layers encompassing EC2, EBS, EKS, RDS, and more. Testing the blast radius of primary component disruptions exposes potential downstream cascading risks. Experiments are executed within isolated sandboxes to eliminate the risks of interfering with production workloads.

Predefined templates jumpstart testing key scenarios like instance retirements, disk space exhaustion, or clustered container service disruptions. Customization through resource targeting, fault selection, and experiment duration flexibility accommodates advanced use cases. Control groups contrast outcomes against unimpaired baselines. Post-experiment reporting furnishes crucial insights, including step-by-step fault visibility and breakdown of recovery workflows, both automated and manual invoked in response. This auditable evidence trail aids identification of RTO improvements while demonstrating due diligence around resiliency testing governed through internal or external compliance mandates. Once you create an EKS cluster and deploy a sample micro service, call as app1, and try to patch as below. By using the Kubernetes topology-spread, you can ask the provisioner to have pods spread across AZs to limit the blast radius of an outage. Patch the deployment with topologySpreadConstraint as follows:

cat <<EOF > patch-file.yaml

spec:

template:

spec:

topologySpreadConstraints:

\- maxSkew: 1

topologyKey: "topology.kubernetes.io/zone"

whenUnsatisfiable: DoNotSchedule

labelSelector:

matchLabels:

app: app1

EOF

kubectl patch deployment app1 --patch-file patch-file.yaml

After this, create the necessary IAM roles as below:

cat > fis-trust-policy.json << EOF

{

"Version": "2012-10-17",

"Statement": \[

{

"Effect": "Allow",

"Principal": {

"Service": \[

"fis.amazonaws.com"

\]

},

"Action": "sts:AssumeRole"

}

\]

}

EOF

aws iam create-role --role-name my-fis-role --assume-role-policy-document file://permissons/fis-trust-policy.json

The following figure shows the Fault Injection Simulator screen showing the action screen to target the subnets:

![](images/Figure_20.1.png)

Figure 20.1: AWS Fault Injection Simulator Actions screen

Then, create an AWS Fault Injection Simulator (FIS) experiment as above. FIS has a lot of action types, including disrupting network connectivity, as above. With this setup, we are targeting a particular subnet to be down for 32 minutes. This way, you can test the resiliency of the workload using FIS.

Reflecting on testing outcomes steers more informed architecture decisions and disaster recovery planning cycles. Comparing experiment observations against established SLA commitments helps validate ITO/RPO suitability or trigger policy revisions where gaps emerge. Ongoing testing cadences aligned to deployment rhythms and cycles of learning infusion sustain resilient operations as complexity scales over time.

Expanding executive support for proactive resiliency testing converts previously manual procedures into automated pipelines. This shifts testing left through progressive integration from development into pre-production environments. As exclusions narrow, experiments run more representative risks revealing vulnerabilities at proportionate pace alongside feature evolution. Prioritizing these investments balances preventative rigor against pace of innovation, both vital for competitive edge.

Gaining executive support for proactive resiliency testing is crucial for transforming manual procedures into automated, scalable solutions. Strategies for securing executive buy-in include presenting clear ROI calculations for investing in automated resiliency testing, highlighting potential costs and risks of inadequate backup and recovery processes, and demonstrating how proactive testing aligns with business continuity objectives. Implementing a culture of resiliency involves promoting a shift-left mentality, integrating testing earlier in the development cycle, gradually narrowing testing exclusions to create more representative risk scenarios, and balancing rigorous testing with the pace of innovation to maintain competitive edge.

[Disaster recovery models with Amazon EKS](#contents.xhtml#sc2_411a)

Amazon EKS allows teams to architect disaster recovery systems that are aligned to application criticality through flexible recovery models. Choosing suitable data replication techniques with infrastructure across Regions or accounts aids business continuity planning. The backup and restore model offers a baseline approach focused on backing up application data and cluster configurations while relying on native AWS redundancy within a Region. Recovery prioritizes restoration speed, leveraging snapshots, images, and backups to rebuild in-Region resources after isolated or zonal failures.

The pilot light model prepares for recovery via a minimal replica environment with critical core components ready. This might encompass running a replica Kubernetes control plane across Regions with small database pilot instances but keeping main application stacks cold. The goal is quick re-provisioning of the remaining infrastructure. The pilot light model balances limited additional overhead for partial hot standby against the need to rebuild certain stacks after disaster events.

A warm standby setup expands on the pilot light model, keeping the replica environment pre-provisioned. Full technology stacks are deployed in the secondary region but without production traffic. Occasional switching to perform sync data updates avoids growing data gaps. Warm standby pays higher operating costs for fuller standby availability and lower RTO relative to cold setup still requiring app deployment. This suits applications with changing data and configurations incompatible with cold spares.

Exercising switchover processes for pilot light and warm standby remains vital to validate RTO expectations. Traffic redirection, quorum transitions, and DNS propagation all carry nuances only visible at full simulation scale. Adjusting architecture based on test observations allows optimizing for target recovery objectives. Factoring exercise costs when choosing the level of hot standby avoids over or under engineering continuity infrastructure. Active-passive multi-Region deployments extend resilience via an online production environment mirrored by a secondary warm standby. Cross-Region snapshots or replication ensures continuity data protection even during a regional outage. The tradeoff warrants weighing additional overhead against the risk tolerance.

An active-active model utilizes multi-master data replication to attain the highest availability, deploying full-fledged infrastructure across Regions. Production traffic alternates seamlessly via DNS routing or load-balanced failover. This suits extremely low RTO/RPO thresholds but incurs maximum complexity. Understanding application architectures aids decisioning on suitable infrastructure recovery models. Stateful and stateless tier separation provides options for selective replication, minimizing overhead. Leader-follower data topologies allow focusing on real-time duplication only for databases, leaving stateless compute recovery to revert to backups.

Testing switchover execution remains imperative regardless of the chosen model to vet assumptions on RTO and synchronization preconditions. Traffic redirection, quorum transitions, and access roles/credentials validation all face real-world testing shortfalls relative to staged simulations. Revisiting recovery procedures post-test hardens capabilities, converting documented plans into reliable, resilient operations.

[Validating and testing backup DR strategies](#contents.xhtml#sc2_412a)

Rigorously testing implemented backup and disaster recovery capabilities creates confidence in operational resilience. Schedule formal rehearsals outlining scope, procedures, stakeholders, and success criteria. Execute recovery procedures encompassing isolation of simulated failure events, restoration workflow kickoff, monitoring, and cutover verification against performance benchmarks. Test nuanced scenarios like partial data loss, corrupted data stores, selective component failures or Region-wide service disruptions based on risk assessments. For advanced use cases, simulate cyber-attacks, credential compromises, or insider threats that can inflict infrastructure harm that is difficult to inoculate upfront.

Documenting the testing journey from failed dependencies and blast radius through orchestrated restart procedures provides audit history showcasing due diligence while clarifying pathways requiring optimization. Gathering compliant evidentiary proves implementation effectiveness for internal leadership or external governing authorities. Testing frequently exercises actual recovery toolchains before dire scenarios render them non-functional from bit rot accumulation. Critical to disaster preparedness strategies is overcoming a false sense of security from untested documentation alone. Rigorous testing unlocks tangible confidence in capacities to uphold infrastructure support for applications running on Amazon EKS when stability assumes paramount importance within chaotic conditions.

[Monitoring backup and DR operations](#contents.xhtml#sc2_413a)

Preserving visibility into backup and disaster recovery processes ensures teams can verify operational health and compliance. Monitoring consolidates status across varied capabilities, providing consolidated dashboards detailing completion, frequency, retention, and historical success.

AWS Config delivers configuration history and changes for resources, applications, and infrastructure to enable compliance audits. Change tracking aids review of control plane modifications while storing evidence like EKS Kubernetes API calls to etcd. Compliance packs furnish predefined rules for standards like HIPAA. Robust monitoring centrally aggregates metrics across recovery tools into CloudWatch Dashboards, providing temporal visualizations of job success rates, backup age, and frequency. Building rule-based alarm alerts on thresholds achieves proactive notifications when anomalies threaten SLA attainments.

Going beyond reactive monitoring to proactively simulate failures tests resilience while creating observable events to validate response workflows. Using tools like AWS Fault Injection Simulator induces controlled experiments across downstream dependencies, exercising recovery capabilities. Integrating resulting event and performance data enriches a holistic understanding of backup and disaster recovery operations.

Stepping back, comprehensive monitoring reconciles capacities, compliance and costs, three crucial elements for sustainable continuity planning. Architecting durable systems calls for data-driven diligence validating that recovery infrastructure not only functions reliably today but stays evergreen for tomorrow's uncertainties.

[Conclusion](#contents.xhtml#sc2_414a)

In the pursuit of resilient Amazon EKS deployments, a meticulous blend of comprehensive planning and meticulous execution is imperative. This chapter served as a foundational cornerstone, providing readers with both theoretical insights and practical knowledge essential for crafting robust backup and disaster recovery strategies. It addresses the nuanced intricacies of application architectures and organizational needs, laying the groundwork for meeting ambitious availability goals.

Armed with a layered approach to data protection encompassing infrastructure, cluster, and application data, teams gain the capability to proactively combat disruptions, ranging from minor outages to large-scale disasters. This adept handling of data protection ensures that as organizations entrust their mission-critical workloads to Amazon EKS, the ability to recover within predefined RTO and RPO objectives remains paramount.

By internalizing the concepts embedded in this chapter, IT teams are poised to confidently construct durable systems aligned with organizational goals of availability, reliability, and long-term data preservation. The knowledge imparted here not only addresses immediate challenges but also equips teams to navigate the evolving landscape of cloud-native deployments, fostering an environment where resilience becomes synonymous with success in the realm of Amazon EKS.

[Questions](#contents.xhtml#sc2_415a)

1.  What is the difference between backup and disaster recovery?
    
2.  What factors determine the choice between EKS native tools vs. external tools for backup/restore?
    
3.  Where should application data be backed up to support disaster recovery?
    
4.  What is the primary benefit of testing disaster recovery systems periodically?
    
5.  How can you ensure backup jobs and restore jobs are visible for auditing?
    

[Exercises](#contents.xhtml#sc2_416a)

1.  Install Velero on an Amazon EKS cluster and back up a WordPress deployment's persistent volumes.
    
2.  Simulate an availability zone failure to test the disaster recovery plan and measure the RTO/RPO.
    
3.  Create an Amazon CloudWatch dashboard to monitor key backup and restore metrics for an EKS cluster.
    

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 21Amazon EKS Optimization and Best Practices](#contents.xhtml#ch21a)

[Introduction](#contents.xhtml#sc2_417a)

Managing Amazon Elastic Kubernetes Service (EKS) entails navigating a diverse and dynamic landscape of considerations, each playing a crucial role in the overall success of your EKS clusters. This chapter acts as a guiding compass, distilling best practices into key areas essential for the effective deployment and maintenance of EKS clusters. From fortifying security practices to optimizing costs, the goal is to empower practitioners with invaluable insights and proven strategies. By focusing on critical aspects such as security, reliability, scalability, and operational efficiency, this chapter provides a roadmap for practitioners to confidently navigate the complexities of EKS management and make informed decisions throughout their EKS journey.

As practitioners explore EKS, they will find actionable recommendations and practical insights that address real-world challenges. The chapter is designed to evolve alongside the dynamic EKS ecosystem, ensuring that practitioners stay abreast of the latest best practices and emerging trends in Kubernetes orchestration on the AWS cloud. With a commitment to providing a holistic perspective, this chapter becomes an indispensable companion for those seeking to master the art of EKS management, fostering a resilient and efficient Kubernetes environment on AWS.

[Structure](#contents.xhtml#sc2_418a)

This chapter discusses the various touchpoints including the below:

*   Cost optimization
*   Cluster upgrades
*   Scalability considerations
*   Networking
*   Reliability
*   Cluster Autoscaling
*   Security best practices

[Objectives](#contents.xhtml#sc2_419a)

In this chapter, we aim to offer readers a straightforward and accessible understanding of Amazon EKS best practices across key operational domains. We recognize the importance of breaking down complex concepts to provide practical insights that can be easily grasped. The chapter delves into the intricacies of securing clusters effectively, ensuring that readers gain valuable knowledge on bolstering the safety of their EKS environments. Simultaneously, we explore the optimization of resources, guiding practitioners on how to make their clusters reliable and scalable to meet dynamic demands.

Furthermore, the chapter places a strong emphasis on cost-efficient practices, recognizing the significance of budget-conscious approaches in the ever-evolving landscape of cloud computing. By the end of this chapter, we will comprehend the theoretical aspects and be confidently equipped to architect, deploy, and maintain EKS clusters. The intention is to empower readers with a skill set grounded in industry-leading practices, fostering an environment where EKS implementation aligns seamlessly with operational excellence. This practical approach aims to demystify the complexities associated with Amazon EKS, making it an accessible and manageable undertaking for professionals in the field.

[Cost optimization](#contents.xhtml#sc2_420a)

A critical first step is to define a tagging strategy for workloads to allocate costs and monitor usage. Tools like Kubecost should be used to gain visibility into EKS usage and costs. Dashboards should also be enabled to visualize and estimate costs. Cloud costs should be allocated to applications, teams, and revenue streams. Recommended optimization best practices include identifying and eliminating waste, architecting solutions for cost efficiency, choosing the most cost-efficient purchasing options, and continuously adapting as services evolve to account for changes in efficient use. The main Kubernetes and EKS cost drivers, like compute, networking, and storage, should be optimized. Once observability and optimizations are implemented, planning and forecasting best practices include budgeting and forecasting cloud and EKS costs dynamically, quantifying the business value delivered by EKS, and integrating EKS cost management practices with overall IT financial planning. Cost optimization should be treated as a continuous process, securing executive sponsorship to integrate optimizations into organizational processes. Tooling, automation, and activities should continue to evolve with the organization's changing needs.

The key themes are getting visibility into EKS costs, optimizing for efficiency, adapting approaches over time, and making cost optimization a critical capability integrated into IT financial processes. Continually adjust resource requirements for applications rather than trying to get them perfectly right the first time to avoid increasing costs and worsening performance over time. Right-sizing workloads, reducing unused capacity, and optimizing compute types like Spot and GPUs are top priorities for lowering cluster costs. The bulk of EKS cluster costs come from EC2 instances, so accurately setting workload resource requests and limits is essential for rightsizing. Tools like Horizontal Pod Autoscaler, Vertical Pod Autoscaler, Karpenter, and Cluster Autoscaler help continually adjust resource allocations and node counts based on real usage. Strategies like bin packing, scheduling scale downs, using Spot instances, committing to Savings Plans, and switching to Graviton chips or GPUs optimize the type and amount of compute provisioned. Isolating noisy neighbor workloads, configuring multi-tenant resource quotas, and tuning Cluster Autoscaling parameters balance utilization, availability, and cost in shared clusters.

Using topology aware routing, endpoint slices, and hints, the endpoint slice controller allocates pod endpoints across zones and sets hints for keeping traffic within zones that the kube-proxy on each node uses to restrict cross-zone traffic. Provisioning worker nodes or scheduling pods restricted to a single availability zone (AZ) prevents cross-zone pod traffic by default but sacrifices high availability and resilience to zone outages. Node selectors and pod affinity can alternatively schedule pods onto nodes in the same AZ without compromising the full distribution of nodes across zones, but adds management overhead compared to relying on default zone diversity. Balancing even distribution of endpoints with completely eliminating cross-zone traffic, topology aware routing reduces but does not fully remove traffic across zones, so some high availability is still compromised compared to default behaviors.

The right balance between cost optimization from limiting cross-zone traffic and availability from distributing across zones depends on the specific reliability requirements and traffic patterns of the workload. Monitoring actual cross-zone traffic levels before and after changes is important to quantify the cost-availability tradeoffs. There are cases where restricting traffic at a zonal level is not sufficient, and you may need to reduce network latency between certain applications that have frequent inter-communication. To achieve optimal network performance and reduce costs, you can restrict traffic to a specific node using the Service internal traffic policy in Kubernetes. The Service internal traffic policy dictates the exclusive use of node-local endpoints, reducing network traffic-related costs and latency. To avoid unexpected behavior, you should run enough replicas for each communicating Pod, have an even spread of Pods using topology spread constraints, and use pod-affinity rules for co-location. When using load balancers, you can reduce data transfer charges by utilizing the IP traffic mode instead of the instance mode. To reduce data transfer costs from container registries, you can use Elastic Container Registry’s (ECR) built-in image replication feature, interface VPC endpoints, and pre-cached container images. To minimize data transfer costs when communicating with AWS services and the internet, you can use VPC endpoints and NAT gateways in each AZ.

For communication between VPCs, you can use VPC peering or Transit Gateways to reduce data transfer costs. Service meshes like Istio offer networking capabilities, such as locality weighted distribution, to restrict traffic to AZs and reduce cross-zone data transfer charges. There are scenarios where applications need to preserve data, either for short or long term, and volumes can be mounted by Pods to tap into different storage mechanisms in Kubernetes. For ephemeral storage, Kubernetes supports various types of volumes like emptyDir, configMap, and hostPath, which are backed by locally-attached devices or RAM. For host root volumes, it is recommended to start with gp3 Amazon EBS volumes, which are cost-efficient and offer lower prices compared to gp2 volumes. Amazon EC2 instance stores provide temporary block-level storage without additional fees, making them cost-efficient for ephemeral storage, but data is lost when the instance is terminated. For persistent storage, Kubernetes supports different options like Amazon EBS, Amazon EFS, Amazon FSx for Lustre, and Amazon FSx for NetApp ONTAP. Amazon EBS volumes can be consumed as Kubernetes persistent volumes, suitable for databases and throughput-intensive applications, with the Amazon EBS Container Storage Interface (CSI) driver managing the lifecycle of these volumes.

For high-performance requirements, io2 block express volumes are suggested. Monitoring and optimizing storage utilization over time is important, and you can use tools like AWS Trusted Advisor, and AWS Compute Optimizer for recommendations. Implementing a backup retention policy using Amazon Data Lifecycle Manager or Velero can help manage snapshot costs. Amazon EFS, a serverless file system, is suitable for sharing file data across containers and AZs, with different storage classes and lifecycle management options available. Amazon FSx for Lustre, a high-performance parallel file system, is recommended for workloads requiring high throughput and low latency, with options for scratch or persistent deployments, SSD or HDD storage, and data compression. Amazon FSx for NetApp ONTAP provides feature-rich, shared file storage with primary and capacity pool tiers, enabling data compression and deduplication to reduce storage costs. Additionally, minimizing container image size through techniques like multi-stage builds and using slim base images can help reduce storage requirements on the host.

For the EKS control plane, you can optimize costs by selectively enabling log types based on your environment (production or non-production) and streaming control plane logs to Amazon S3 via CloudWatch Logs subscriptions for more cost-efficient long-term storage. Regarding the EKS data plane, you can customize the log retention period in CloudWatch based on your workload requirements, ranging from 1 day to 10 years, to save on storage costs while maintaining critical logs. Another cost optimization strategy is to leverage different AWS S3 storage tiers for log storage, such as forwarding less critical logs directly to S3 instead of CloudWatch, which can significantly reduce storage costs. Additionally, you can use log filtering to narrow down the types of log messages that are stored, further optimizing storage costs.

[Cluster upgrades](#contents.xhtml#sc2_421a)

Before initiating an upgrade, we recommend understanding Kubernetes deprecation policies, reviewing the Kubernetes change log, assessing cluster add-ons compatibility, enabling control plane logging, and testing upgrades in a non-production environment. It also suggests leveraging tools like eksctl for cluster management, using managed node groups or EKS on Fargate to streamline worker node upgrades, and employing the kubectl convert plugin to ensure compatibility with the new Kubernetes version. Staying current with Kubernetes updates is highlighted as crucial for maintaining a secure and efficient EKS environment. Proactive upgrading is encouraged at least once a year to align with technological advancements, ensuring optimal efficiency and security in the EKS environment.

The sequence of actions for upgrading a cluster is documented in the public forums, including reviewing release notes, taking backups, identifying deprecated API usage, and ensuring compatibility of managed node groups. A checklist creation process using EKS Documentation is recommended for each upgrade. Next, administrators are guided to verify the EKS IAM role, ensuring it has the correct assume role policy. The use of CLI commands to check and validate the IAM role's policy chapter is demonstrated. Configuring PodDisruptionBudgets and topologySpreadConstraints to ensure workload availability during data plane upgrades and introduces the AWS Resilience Hub for tracking application resilience.

In preparation for upgrading Amazon EKS clusters, several key considerations and steps should be addressed. Firstly, for Karpenter-managed nodes, the utilization of the Node Expiry feature is recommended. By setting the ttlSecondsUntilExpired parameter in the provisioner, node expiry is activated, facilitating the safe replacement of nodes with upgraded instances. Additionally, Karpenter's Drift feature can be employed to automatically upgrade provisioned nodes, ensuring synchronization with the EKS control plane. This feature, however, requires enabling through a feature gate. For self-managed node groups, which are EC2 instances attached to the cluster outside the EKS service, tools like eksctl can be utilized for tasks such as deleting and draining self-managed nodes. Prior to any upgrades, it is imperative to back up the cluster, and Velero, an open-source tool, is suggested for this purpose. Keep in mind that downgrading after an upgrade is not supported.

In the case of Fargate deployments, a restart of deployments is necessary after upgrading the control plane. Identification of Fargate nodes can be achieved by listing pods and redeploying as needed. Alternative upgrade strategies, such as blue/green clusters, should be considered. While this strategy offers benefits like version changes and the ability to revert to the old cluster, it involves downsides such as API and OIDC changes, requiring parallel cluster running during migration. Admins should stay informed about major changes in Kubernetes versions beyond the next release.

[Scalability considerations](#contents.xhtml#sc2_422a)

EKS automatically scales the Kubernetes control plane to ensure high availability. The data plane scales based on the number of nodes in node groups. Node groups can autoscale to match workload demands and optimize costs. Karpenter and Cluster Autoscaler help scale node groups. Services like load balancers and databases should be scaled independently to match traffic and workload demands on the cluster.

[Control plane scaling](#contents.xhtml#sc3_423a)

Scaling nodes and pods down safely is crucial for maintaining a healthy Amazon EKS cluster. One strategy is to regularly replace long-running instances to prevent configuration drift and address issues that may arise after extended uptime, such as slow memory leaks. Automated replacement, facilitated by Karpenter's time-to-live (TTL) settings, ensures efficient node upgrades and security patching. For self-managed node groups, the max-instance-lifetime setting can be used to cycle nodes automatically, while managed node groups lack this feature currently. Efficiently managing node resources involves removing underutilized nodes. In Kubernetes Cluster Autoscaler, the scale-down-utilization-threshold parameter can be employed, or in Karpenter, the ttlSecondsAfterEmpty provisioner setting. To safeguard workload availability during node removal, the use of pod disruption budgets and safe node shutdown practices is recommended.

When interacting with the Kubernetes API, optimizing the use of kubectl is vital. Utilizing the client-side cache in kubectl reduces unnecessary API calls and minimizes load on the Kubernetes API Server. Conversely, disabling kubectl compression in the kubeconfig file can reduce API and client CPU usage. For large clusters exceeding 1000 nodes, scaling the Kubernetes Cluster Autoscaler in shard mode is advisable. This involves configuring multiple instances of the Cluster Autoscaler, each responsible for scaling a set of node groups. The API Priority and Fairness (APF) mechanism in the API Server ensures it does not get overloaded during increased request periods. This includes configuring inflight requests division using PriorityLevelConfigurations and FlowSchemas. Metrics monitoring and prevention techniques, such as workload adjustments or altering APF settings cautiously, are essential to avoid dropped requests.

Efficiently retrieving resources from the API server is crucial, especially as the cluster scales. Shared informers and using watch instead of list for API calls, limiting calls to necessary resources, and optimizing listing options help manage API server load. Filtering based on labels and namespaces, along with using resourceVersions, are additional strategies for efficient API usage, preventing unnecessary load on both the API server and etcd.

[Data plane scaling](#contents.xhtml#sc3_424a)

The Kubernetes Data Plane encompasses various components, such as EC2 instances, load balancers, and storage, forming the infrastructure for the Kubernetes Control Plane. To enhance organization, cluster services are grouped separately, and load balancer scaling is discussed in the workloads chapter, with this chapter focusing on scaling compute resources. Choosing appropriate EC2 instance types for clusters with diverse workloads can be challenging. The use of automatic node autoscaling, especially through managed node groups and Karpenter, is recommended for large-scale clusters. Managed node groups provide flexibility with benefits like managed upgrades, while Karpenter is an open-source node autoscaler offering workload-native scaling without managing node groups.

To prevent errors due to instance type limitations, various EC2 instance types should be used. Karpenter, by default, utilizes a broad set of compatible instance types, avoiding limitations. The Kubernetes Cluster Autoscaler requires node groups to be similarly sized for consistent scaling, suggesting the creation of multiple groups based on CPU and memory size. Preferably, larger nodes can reduce API server load, but careful consideration is needed to ensure full utilization. Workloads should define resource requirements and availability goals via taints, tolerations, and PodTopologySpread, emphasizing the largest fully utilized nodes. Scheduler and autoscaling tools aim to optimize workload placement across AZs.

Efficient use of compute resources, including EC2 instances and AZs, is crucial for scalability, availability, and cost reduction. Karpenter facilitates on-demand instance provisioning based on workload needs. Regular updates, especially of the Amazon Machine Image (AMI), are essential for security. EBS volumes should be used judiciously, considering I/O quotas and workload storage. Furthermore, instances with low EBS attach limits should be avoided, and unnecessary logging to disk should be disabled. For rapid OS updates, in-place patching can be considered, but it is essential to thoroughly test updates. AWS Systems Manager Patch Manager is recommended for automating patching nodes.

[Services scaling](#contents.xhtml#sc3_425a)

Cluster services in an EKS cluster, distinct from user workloads, play a crucial role in automating and operating the cluster. Typically running in the kube-system namespace, these services, often implemented as DaemonSets, ensure high uptime, which is critical for troubleshooting and outage prevention. For robustness, it is recommended to run cluster services on dedicated compute instances, such as a separate node group or AWS Fargate, shielding them from impacts caused by scaling user workloads. Scaling CoreDNS involves optimizing external queries and increasing replicas. Lowering the ndots setting in CoreDNS configuration reduces unnecessary DNS queries, enhancing efficiency. Additionally, scaling CoreDNS horizontally is achieved by adding replicas using NodeLocal DNS or the cluster proportional autoscaler. The latter scales are based on the cluster's size, offering flexibility.

For the Kubernetes Metrics Server, both horizontal and vertical scaling are supported. Vertical scaling is essential as the cluster grows, requiring adjustments based on the added nodes and metrics. Vertical Pod Autoscaler or Addon Resizer can be employed to scale the Metrics Server efficiently. Addressing CoreDNS propagation delays during scaling, setting a lameduck duration minimizes DNS lookup failures. This ensures CoreDNS continues responding to requests during the shutdown process, allowing nodes time to update iptables rules. Employing /ready instead of /health for CoreDNS's readiness probe aligns with a recommended lameduck duration of 30 seconds, ensuring readiness for DNS requests.

Effective management of logging and monitoring agents is crucial for optimizing cluster control plane performance. Agents querying the API server for metadata can be resource-intensive. Strategies include disabling integrations, implementing sampling and filtering to reduce metrics and logs collected, and buffering data during outages using solutions like Amazon Kinesis Data Firehose with fluentbit for CloudWatch.

[Workloads scaling](#contents.xhtml#sc3_426a)

The scalability of a Kubernetes cluster is heavily influenced by the nature of its workloads. Workloads utilizing Kubernetes APIs extensively can constrain the total number of workloads in a cluster, but adjustments in defaults can alleviate the load. It is recommended to disable unnecessary features like Secrets and ServiceAccounts if not essential, enhancing security and reducing dependence on the control plane. Implementing IPv6 for pod networking can mitigate common scaling issues related to IP address exhaustion and improve per-node performance. It provides an alternative to IPv4 prefix mode, which requires careful management of available IP addresses. Controlling the number of services per namespace, ideally below 500, is advised to enhance performance, manage IP tables rules, and avoid network latency, especially considering the growth in IP tables rules with kube-proxy.

Understanding Elastic Load Balancer (ELB) quotas is crucial when creating services. ALB and NLB quotas differ, requiring adjustments based on service requirements. Considering alternatives like ingress controllers and utilizing Route 53, Global Accelerator, or CloudFront to expose multiple load balancers as a single endpoint provides flexibility and optimizes traffic management. EndpointSlices are recommended over Endpoints for discovering pods matching service labels. AWS Load Balancer Controller users should ensure EndpointSlices are enabled. For secrets, employing immutable and external options, along with monitoring and alerts, helps manage the watch impact on the API server. Limiting deployment history and disabling enableServiceLinks by default can reduce the tracking load on the Kubernetes Controller Manager.

Careful consideration of dynamic admission webhooks, including availability, failure policies, and avoiding unnecessary calls, is essential. Mutating webhooks, if frequent, may lead to resource version storage issues in etcd, emphasizing the importance of minimizing large resource modifications. These strategies collectively contribute to the efficient management and scaling of Kubernetes clusters. Understanding Kubernetes scalability goes beyond merely counting nodes within a cluster. While node count is a factor, the rate of change in workloads over time is a more critical metric for assessing scalability. Metrics such as queries per second (QPS) become crucial, as Kubernetes components have mechanisms, often QPS-based, to prevent overwhelming subsequent components. The QPS settings should be handled with care, considering downstream effects and inter-component relationships.

Distinguishing between AWS-managed components and customer-configurable components in a managed service like EKS helps monitor and address bottlenecks effectively. Examining metrics bidirectionally, both upstream and downstream, is vital for identifying potential issues. Workload complexity may impact the number of pods a node can handle, emphasizing the need to ensure that the Kubelet keeps pace with the container runtime. Metrics-driven optimization is advocated, focusing on finding bottlenecks rather than fixating on specific workload numbers. Considering downstream components when making changes is crucial, and unnecessary errors, though handled well by Kubernetes controllers, incur a cost in terms of increased pressure on components like the Kube Controller Manager.

For large-scale clusters, a holistic approach using functions like top-k in PromQL allows identifying and addressing bottlenecks cluster-wide. Metrics data analysis begins with the API server, providing insights into client applications or control plane issues. The emphasis is on systematic changes backed by data to enhance overall system optimization and avoid unnecessary errors that could impact scalability and performance. Efficiency in managing Kubernetes workloads and nodes is essential for reducing complexity, cost, and enhancing performance and scalability. The choice of node sizes impacts the available space for running pods, with larger nodes providing more usable space. However, extreme packing of nodes with many pods can lead to errors or saturation, requiring vigilant monitoring of node saturation.

Node selection is not a one-size-fits-all decision; workloads with different churn rates may benefit from different node sizes. Consideration of factors like CPU pinning for applications using full cores and understanding the Linux CFS rules post-Kubernetes scheduling is crucial. The concept of sweet spot in application right-sizing emphasizes finding the optimal point before saturation for efficient scaling. Pod sprawl, resulting from incorrect sweet spot settings, can lead to unnecessary pod creation, escalating infrastructure needs. Utilizing metrics that reflect true application saturation rather than relying solely on CPU utilization is vital. HPAv2 provides flexibility in scaling based on multiple criteria, including custom and external metrics.

Saturation metrics, not just utilization, are crucial for scaling nodes and applications efficiently. Node saturation, especially regarding pressure stall information metrics, helps avoid over-saturating nodes and ensures optimal scaling. The importance of smooth scaling, using appropriate saturation metrics, is demonstrated, highlighting the correlation between application and node performance. CPU limits, often misunderstood, require careful consideration and metrics analysis.

[Networking](#contents.xhtml#sc2_427a)

Operating an Amazon Elastic Kubernetes Service (EKS) cluster involves understanding both AWS VPC networking and Kubernetes networking. Before designing the VPC or deploying clusters, it is crucial to grasp EKS control plane communication mechanisms. This includes considerations like Cluster VPC design and Amazon EKS security group configurations. The EKS cluster architecture comprises an AWS-managed VPC for the Kubernetes control plane (not visible in the customer account) and a customer-managed VPC for Kubernetes nodes and associated AWS infrastructure. Nodes connect to the EKS control plane either through a public endpoint or Cross-Account elastic network interfaces (X-ENIs). The communication path is determined by the cluster's API endpoint configuration: public, private, or both.

The cluster networking involves the execution of the EKS bootstrap script on nodes, launching container runtime agents, Kubelet, and Kubernetes node agents. Node registration occurs as Kubelet establishes a connection with the Kubernetes cluster endpoint. EKS provides flexibility in controlling access to the cluster endpoint. This can be achieved through public, private, or both public and private endpoints. The choice impacts how nodes communicate with the control plane, either via the internet or within the VPC using X-ENIs.

Amazon VPC supports both IPv4 and IPv6 addressing, while EKS clusters support both as well. EKS recommends using at least two subnets in different AZs during cluster creation. Deployment scenarios include configurations with public, private, or both public and private subnets. For IPv6 clusters, dual-stack VPCs and subnets are required. Communication across VPCs is facilitated by Amazon VPC Lattice, offering secure connectivity between services across multiple VPCs without additional services like VPC peering. Overlapping IP ranges can be addressed using Private NAT Gateway or VPC CNI in custom networking mode.

Shared Amazon VPCs are employed for network administration efficiency across multiple AWS Accounts. AWS Resource Access Manager (RAM) is utilized to securely share resources among accounts, with considerations for IAM roles and security groups. Security groups, Multi-AZ deployment, and careful consideration of security configurations are emphasized. Recommendations include deploying nodes to private subnets for increased control, using private and public modes for the cluster endpoint, and configuring security groups thoughtfully.

When an EC2 instance is created, a primary ENI is associated with a subnet, and Pods in hostNetwork mode share the primary IP address. The CNI manages additional ENIs with warm pools of IP addresses for scalability. The warm pool includes unused IPs, and the CNI pre-allocates ENIs for faster Pod startup. As Pods are added, the CNI dynamically attaches more ENIs based on node capacity. Each instance type has limits on ENIs and IP addresses, influencing Pod density. HostNetwork Pods are excluded from these calculations. The default Secondary IP mode allocates secondary private IP addresses to Pods. The CNI maintains warm ENIs and IPs, and when depleted, attaches more ENIs dynamically. Configuration settings like WARM\_ENI\_TARGET, WARM\_IP\_TARGET, and MINIMUM\_IP\_TARGET control the warm pool behavior.

When a Pod is added, the CNI binary queries ipamd for an available IP address, wiring up the host and Pod network. Pods share security groups with the primary ENI by default. IP addresses are returned to the warm pool after Pod deletion, following a cool-down period. The maximum number of Pods depends on ENI and IP address limits for each instance type. A formula calculates this, considering host networking Pods like kube-proxy and VPC CNI. Recommendations include deploying VPC CNI as a managed add-on, migrating to managed add-ons, backing up CNI settings, understanding security contexts, using a separate IAM role for CNI, handling probe failures, configuring IPTables, and routinely upgrading the CNI version. As containerized environments experience rapid growth due to application modernization, managing IP addresses in Amazon EKS becomes crucial. The VPC CNI plugin assigns IPs from the VPC's CIDR(s) to Pods, offering visibility but potentially consuming many addresses. Optimizing IP consumption is vital at both VPC and node levels.

Prefix delegation in Amazon VPC allows assigning IPv4 or IPv6 prefixes to EC2 instances, increasing IP addresses per ENI, enhancing pod density, and improving compute efficiency. This feature is compatible with custom networking. To mitigate IP exhaustion, sizing VPCs and subnets with growth in mind is crucial. IPv6 adoption is recommended for its extensive address space, supporting both IPv4 and IPv6 communication within a cluster. Custom networking, using non-routable secondary CIDRs, is another approach to conserve IPv4 addresses.

For IPv4 clusters, planning for growth is essential, with recommended net-masks and considerations for elements beyond pods and nodes, like load balancers. Utilizing the EKS Subnet Calculator helps in network planning. Custom networking allows scheduling Pods in dedicated subnets, conserving routable IPs. Optimizing the warm pool of IPs involves adjusting VPC CNI configuration variables like WARM\_IP\_TARGET, MINIMUM\_IP\_TARGET, and WARM\_ENI\_TARGET. It is crucial to avoid throttling API requests while setting these values. Monitoring IP address inventory using CNI Metrics Helper and CloudWatch alarms provides visibility into subnet IP utilization.

Considerations beyond Amazon EKS include optimizing communication across VPCs, sharing a VPC across multiple accounts, and leveraging architectural patterns to address IP exhaustion challenges. Enabling IPv6 mode in Amazon EKS addresses the challenge of IPv4 exhaustion, especially in large-scale clusters, and aims to resolve the limitations of the IPv4 address space. This support focuses on mitigating concerns raised by customers, distinct from Kubernetes' IPv4/IPv6 dual-stack feature. EKS/IPv6 minimizes CIDR overlap issues by interconnecting network boundaries using IPv6 CIDRs, solving both in-cluster and cross-cluster problems. Once deployed in IPv6 mode, the action is irreversible, lasting the entire cluster's lifetime.

In an IPv6 EKS cluster, Pods and Services receive IPv6 addresses while maintaining compatibility with legacy IPv4 endpoints. The VPC leverages native IPv6 capabilities, creating dual-stack VPCs with dual-stack subnets. IPv4 features like Route Tables and NACLs function similarly in an IPv6-enabled VPC. Each VPC is allocated an IPv4 and a unique /56 IPv6 prefix. Nodes and Pods in an IPv6 EKS cluster receive public IPv6 addresses. IPv6 addresses for services are based on Unique Local IPv6 Unicast Addresses. IPv6 prefix assignment occurs during worker-node bootstrap, mitigating delays caused by high Pod churn. Worker-nodes receive both IPv4 and IPv6 addresses, with IPv4 addressing utilizing a non-routable range (169.254.172.0/22). IPv6 Pods communicate over IPv6, and Kubernetes services receive only IPv6 addresses.

EKS recommends running worker nodes and Pods in private subnets, utilizing public load balancers in public subnets for traffic balancing. The control-plane communication involves Cross-Account ENIs in dual-stack mode, supporting both IPv4 and IPv6. However, EKS APIs remain accessible by IPv4 only, requiring network support for IPv6 transition mechanisms. Considerations include scheduling based on compute resources, evaluating the need for existing custom networking, and recognizing that Fargate Pods in EKS/IPv6 clusters consume IPv6 and VPC routable private IPv4 addresses. Deploying the AWS Load Balancer Controller is recommended for handling IPv6 in the load balancing of services, with considerations for AWS Network Load Balancer limitations with dual-stack UDP protocol address types. Enabling Amazon VPC CNI in default mode assigns Pods IP addresses from the primary subnet, typically the node's subnet. In cases where the primary subnet is too small, leading to a lack of secondary IP addresses, common in EKS IPv4 clusters, custom networking provides a solution. Custom networking addresses IP exhaustion by assigning node and Pod IPs from secondary VPC address spaces using ENIConfig custom resources, creating secondary ENIs, and assigning Pods IP addresses from CIDR ranges defined in ENIConfig.

Custom networking lowers the maximum Pods per node since the primary ENI is not used. Configuration involves specifying alternate subnet CIDR ranges in ENIConfig. The recommended CIDRs are from the CG-NAT space, like 100.64.0.0/10 or 198.19.0.0/16, less likely to be used in corporate settings. A diagram illustrates the primary ENI using the primary VPC CIDR, while secondary ENIs use the secondary VPC CIDR. Custom networking is recommended for addressing IPv4 exhaustion challenges when deploying multiple EKS clusters. However, it involves operational overhead and requires considerations for security groups, subnet configurations, and drain procedures for existing nodes.

It is recommended to use custom networking when dealing with IPv4 exhaustion and unable to use IPv6. Custom networking can also be useful for security requirements where Pods need to run on a different network with different security group settings. It is highlighted as an ideal option for connecting EKS clusters to on-premise datacenter services. Conversely, custom networking should be avoided if IPv6 implementation is imminent. In such cases, it is recommended to deploy IPv6 clusters instead. Additionally, if CIDRs from the CG-NAT space are exhausted or cannot be linked with the cluster VPC, alternative solutions, like private NAT gateways, should be explored. The blog post provides insights into overcoming communication challenges for EKS workloads due to overlapping CIDRs, emphasizing considerations for custom networking.

Automated configuration with AZ labels is suggested, utilizing the AZ as the ENI config name. Custom networking is a disruptive action, and it is crucial to replace Pods when configuring secondary networking. Calculating the maximum Pods per node involves considerations for prefix assignment, and recommendations for setting max-pods are provided based on instance types. Identifying existing usage of CG-NAT space is essential when considering custom networking, as it may not address all challenges. In such cases, exploring alternate CNIs, moving to IPv6 clusters, or considering private NAT gateways is recommended. Amazon VPC CNI introduces prefix assignment to enhance IP address availability and pod density on nodes. This feature, available in version 1.9.0 and later, allows the assignment of IPv4 and IPv6 CIDRs, replacing individual secondary IP addresses. Prefix mode is enabled by default on IPv6 clusters, assigning a /80 IPv6 prefix to ENIs.

In prefix assignment mode, Amazon VPC CNI can be configured to assign /28 (16 IP addresses) IPv4 address prefixes, offering flexibility for pod scaling. The number of IP addresses per network interface depends on the instance type, with each prefix counting as one IP address. During worker node initialization, VPC CNI assigns prefixes to the primary ENI, maintaining a warm pool for faster pod startup. Environment variables like WARM\_PREFIX\_TARGET control the number of held prefixes. As more pods are scheduled, additional prefixes are requested, and the CNI attempts to allocate them to existing ENIs or attaches new ENIs to the node.

Recommendations for using prefix mode include enabling it for improved pod density on worker nodes. Care should be taken to avoid subnet fragmentation when migrating to prefix mode. To maximize node utilization, similar instance types are recommended in a node group, and setting WARM\_PREFIX\_TARGET is advised for IPv4 address conservation. Avoiding prefix mode is recommended if the subnet is heavily fragmented or has insufficient available IP addresses for /28 prefixes. In prefix mode, the security group assigned to worker nodes is shared by pods, making it essential to consider Security groups for Pods in scenarios requiring varying network security.

For efficient node group management, it is suggested to use similar instance types and configure WARM\_PREFIX\_TARGET. Allocating new prefixes is preferred over attaching new ENIs for faster performance. Subnet reservations help prevent subnet fragmentation, and the downgrading of VPC CNI version post-prefix mode activation must be avoided. Transitioning to prefix delegation is recommended by creating new node groups and replacing all nodes instead of rolling replacements for increased IP addresses, with a cautionary note on safely deleting old nodes and node groups.

Amazon VPC CNI provides a virtual firewall through AWS security groups for EC2 instances, controlling inbound and outbound traffic. By default, it associates security groups with the primary ENI on nodes, causing all Pods on a node to share the same security groups as the node itself. This broad application of security groups may lead to inefficiencies. Introducing Security Groups for Pods allows for improved compute efficiency by enabling applications with diverse security requirements to run on shared compute resources. It offers network segmentation, essential for a defense-in-depth strategy, as it permits defining multiple security rules for Pods in one place using EC2 security groups. This is particularly beneficial for scenarios such as Pod-to-Pod and Pod-to-External AWS services, as illustrated in the provided images. Enabling security groups for Pods involves setting ENABLE\_POD\_ENI=true for VPC CNI. This triggers the creation of trunk and branch interfaces, with trunk acting as a standard network interface attached to the instance. Branch interfaces facilitate associating security groups with Pods, allowing the scheduling of Pods requiring specific security groups on additional network interfaces.

The capacity of branch interfaces adds to the instance type limits for secondary IP addresses. However, Pods using security groups are not considered in the max-pods formula, necessitating adjustment of max-pods values based on the specific use case. Several recommendations accompany the usage of security groups for Pods. These include disabling TCP Early Demux for Liveness Probe, leveraging existing AWS configuration investments, configuring Pod Security Group Enforcing Mode based on specific requirements, identifying incompatibilities with certain instance types, and efficiently controlling traffic to AWS services. The enforcing mode, whether strict or standard, is crucial in determining which security groups apply to Pods and whether source NAT is enabled. Recommendations emphasize using strict mode for isolating pod and node traffic and standard mode for scenarios like client source IP visibility, deploying NodeLocal DNSCache, and supporting Kubernetes Network Policy.

Incompatibility issues are highlighted for Windows-based and non-nitro instances, which do not support security groups for Pods. Network policies are suggested as an alternative in such cases. Security groups for Pods prove beneficial when applications within an EKS cluster need to communicate with AWS services within a VPC, providing an optimized choice compared to CIDR-based policies. Additional configuration tips include tagging a single security group for use with the AWS Loadbalancer Controller, configuring NAT for outbound traffic, deploying Pods with security groups to private subnets, and verifying terminationGracePeriodSeconds in the Pod specification file.

Several recommendations are provided to address these challenges: to enhance the efficiency and reliability of Kubernetes deployments, several best practices are recommended. Firstly, the utilization of IP Target-Type Load Balancers is advised to streamline the traffic path from the Load Balancer to the target Pods. This facilitates the direct registration of Pod IP/Port tuples, simplifying the overall architecture. Additionally, incorporating Pod Readiness Gates is crucial for preventing Kubernetes from advancing too swiftly during deployments. This mechanism ensures that new pods are thoroughly checked for health before the deployment proceeds, maintaining stability in the system. Another vital consideration is to ensure Pods are deregistered from Load Balancers before termination. This involves implementing a preStop lifecycle hook and extending the terminationGracePeriodSeconds to manage the graceful shutdown of applications, guaranteeing deregistration from Load Balancers prior to termination.

Furthermore, it is recommended to incorporate Readiness Probes in the Pod spec. This practice ensures that applications are only marked as in-service when they are fully ready to handle requests, preventing premature traffic and potential issues. To maintain control over disruptions, configuring a Pod Disruption Budget (PDB) is advised. This budget limits the number of Pods of a replicated application that can be down simultaneously from voluntary disruptions, safeguarding against actions like node draining or application deployments. Lastly, gracefully handling termination signals is highlighted as a critical aspect. This involves effective management of termination signals to enable applications to shut down gracefully. The suggested approach includes the use of lifecycle hooks and extending termination grace periods to facilitate a smooth termination process. By adhering to these best practices, Kubernetes deployments can achieve enhanced stability and performance. Additionally, there is a caution about the deregistration delay in Elastic Load Balancing and considerations regarding in-flight requests during the deregistration process.

[Reliability](#contents.xhtml#sc2_428a)

The importance of maintaining the availability, scalability, and resilience of applications is paramount to meet customer expectations. A scalable and resilient architecture ensures that applications run smoothly, even during changes or traffic spikes. Kubernetes, with its declarative management, plays a crucial role in achieving high availability and resilience. To optimize the deployment and operation of applications on Kubernetes, a comprehensive set of best practices is recommended. Firstly, it is advised to steer clear of Singleton Pods, opting instead for deployments to ensure continuous availability by creating new Pods in case of failures, thus minimizing vulnerability.

Running multiple replicas of an application through Deployments is crucial for achieving high availability. Leveraging the Horizontal Pod Autoscaler facilitates automatic adjustments to the number of replicas based on workload demand, enhancing scalability. To avoid single points of failure, distributing replicas across different nodes is essential. This can be achieved through the use of pod anti-affinity, and Pod topology spread constraints, promoting better fault tolerance and availability.

Implementing Pod Anti-affinity Rules is recommended to favor the placement of pods on separate nodes and AZs, contributing to enhanced reliability. Similarly, employing Pod Topology Spread Constraints ensures the distribution of application replicas across different topology domains, further strengthening fault tolerance. To aid in scaling applications, it is essential to install the Kubernetes metrics server, as autoscaler add-ons such as HPA and VPA rely on metrics to make informed scaling decisions.

Horizontal Pod Autoscaler (HPA) is a valuable tool for automatically scaling applications based on demand. It retrieves metrics from various APIs, including resource metrics, custom metrics, and external metrics. Scaling applications based on custom or external metrics beyond CPU or memory utilization is recommended for more granular control. Additionally, Vertical Pod Autoscaler (VPA) is suggested for automatically adjusting CPU and memory reservations for Pods, ensuring optimal resource allocation. When updating applications, incorporating mechanisms such as rollbacks, blue/green deployments, and canary deployments is vital for smooth and reversible updates. Testing deployments in lower environments before updating the production cluster and utilizing CI/CD pipelines for automated and reversible deployments are crucial steps.

For health checks and self-healing capabilities, leveraging Kubernetes' health-check features, including liveness, startup, and readiness probes, is recommended to automatically replace unhealthy instances. Implementing Pod Disruption Budgets (PDB) is essential to control the eviction process during upgrades and prevent service disruptions. Furthermore, embracing chaos engineering is advised to experiment on the system, identify weaknesses, and build confidence in the system's resilience. Employing a service mesh enhances service-to-service communication, observability, and resilience. Lastly, observability is emphasized through monitoring applications with cluster-wide tools like Prometheus, exposing custom metrics, centrally collecting and persisting logs, and implementing distributed tracing to identify bottlenecks effectively.

By adhering to these recommendations, organizations can ensure their applications remain available, scalable, and resilient, meeting the expectations of their users even during changes or challenging conditions. Amazon EKS simplifies Kubernetes deployment on AWS, removing the need for users to install, operate, and maintain their own control plane or worker nodes. EKS is a certified Kubernetes conformant, ensuring compatibility with upstream Kubernetes. Applications running on upstream Kubernetes seamlessly integrate with EKS. The service autonomously manages the availability and scalability of Kubernetes control plane nodes, promptly replacing unhealthy nodes.

The architecture of EKS focuses on eliminating single points of failure in the Kubernetes control plane, ensuring robustness. The EKS-managed VPC hosts the control plane, consisting of Kubernetes API server nodes and an etcd cluster. API server nodes, including components like the API server, scheduler, and kube-controller-manager, operate in an auto-scaling group across distinct AZs. A similar setup is employed for etcd server nodes to enhance durability. EKS employs a NAT Gateway in each AZ, placing API servers and etcd servers in a private subnet, safeguarding the cluster's availability in case of an AZ-specific event.

Upon creating a cluster, EKS establishes a highly-available endpoint for the managed Kubernetes API server. This endpoint, utilizing Network Load Balancer (NLB), balances the load across Kubernetes API servers. EKS also provisions Elastic Network Interfaces (ENIs) in different AZs, facilitating communication with worker nodes. Users can configure the Kubernetes cluster's API server accessibility, choosing between a public endpoint, EKS-managed ENIs, or both, ensuring redundant connection paths. Monitoring control plane metrics is crucial for identifying and addressing issues that may impact workload availability. Kubernetes API metrics, such as request counts and latency, can be monitored using tools like Prometheus or CloudWatch. CloudWatch Container Insights added support for Prometheus metrics, enabling seamless integration. Essential metrics to monitor include API server metrics, like request duration and admission controller latency, and etcd metrics, such as request duration and database size.

EKS supports two authentication methods: bearer/service account tokens and IAM authentication. Management of cluster access involves editing the aws-auth configmap. In case of misconfiguration, access recovery can be achieved using the cluster creator's user or role. Alternatively, a super-admin account with full cluster access can be created, providing a failsafe mechanism. Admission webhooks, both validating and mutating, extend the Kubernetes API. Poorly configured webhooks may disrupt the control plane. It is advised to avoid catch-all webhooks or implement a fail-open policy with a timeout shorter than 30 seconds. Blocking pods with unsafe sysctls, which modify kernel parameters, can be achieved using tools like OPA Gatekeeper or Kyverno. Handling cluster upgrades involves staying informed about the Kubernetes release cycle changes and ensuring compatibility between control plane and worker node versions.

For running large clusters, EKS actively monitors and scales control plane instances for optimal performance. However, users should consider potential performance issues and AWS service quotas. Clusters exceeding 1000 services may face network latency, and switching kube-proxy to ipvs mode is recommended. EC2 API request throttling may occur for large clusters, and mitigations involve caching IP addresses and using larger EC2 instance types to reduce scaling events. To ensure the high availability and resilience of applications, a robust data plane is essential in Kubernetes. An elastic and resilient data plane, consisting of two or more worker nodes that can dynamically scale and recover from failures, is crucial for the automatic scaling and healing of applications. Scaling EC2 worker nodes is efficiently achieved using tools like Kubernetes Cluster Autoscaler, EC2 Auto Scaling groups, or community projects like Atlassian’s Escalator. Best practices recommend using EC2 Auto Scaling Groups to create worker nodes, ensuring automatic replacement of terminated or failed nodes.

Kubernetes Cluster Autoscaler is recommended for dynamically adjusting the data plane size when there's insufficient capacity, ensuring efficient pod scheduling. It reacts to pending pods due to resource shortages by adding EC2 instances to the cluster. Configuring over-provisioning with Cluster Autoscaler can mitigate delays in scaling by adding more replicas than required. To spread worker nodes and workloads across multiple AZs, it is advised to use Kubernetes 1.18+ Topology Spread Constraints for Pods. For older Kubernetes versions, pod anti-affinity rules can be employed to schedule pods across multiple AZs. Ensuring capacity in each AZ is crucial when using EBS volumes, as volumes are only available within a single AZ.

Resource reservations for system and Kubernetes daemons enhance node stability, and implementing Quality of Service (QoS) with resource requests and limits for containers is recommended for critical applications. Resource quotas for namespaces and LimitRanges can be used to enforce resource usage policies, preventing containers from impinging on resources used by other tenants. Monitoring CoreDNS metrics, employing NodeLocal DNSCache, and configuring cluster-proportional-scaler for CoreDNS are recommended practices to ensure optimal DNS performance in an EKS cluster. Choosing the right AMI for the node group is crucial, and it is advised not to use deprecated AMIs to ensure security and reliability.

[Cluster Autoscaling](#contents.xhtml#sc2_429a)

Karpenter automatically launches node groups based on pending pod capacity to improve cluster utilization. Cluster Autoscaler automatically resizes node groups based on utilization to optimize costs. Karpenter focuses on launching spot instances to reduce costs, while Cluster Autoscaler handles general node group resizing.

[Karpenter](#contents.xhtml#sc3_430a)

Karpenter is an open-source Cluster Autoscaler designed to enhance the capabilities of Kubernetes clusters by automatically provisioning new nodes in response to unschedulable pods. It evaluates the collective resource requirements of pending pods and selects the optimal instance type to run them, automatically scaling in or terminating instances without non-daemonset pods to reduce waste. Additionally, Karpenter supports a consolidation feature that actively relocates pods and deletes or replaces nodes with cost-effective alternatives, thereby reducing overall cluster costs.

Prior to Karpenter's introduction, Kubernetes users often relied on Amazon EC2 Auto Scaling groups and the Kubernetes Cluster Autoscaler. However, Karpenter offers greater flexibility without the need for numerous node groups, making it less dependent on specific Kubernetes versions and avoiding frequent switches between AWS and Kubernetes APIs. Karpenter consolidates instance orchestration tasks within a single system, providing a more stable and cluster-aware solution than the Cluster Autoscaler. It addresses challenges related to workload provisioning, diverse node configurations, and efficient pod scheduling at scale. For more information and documentation on using Karpenter, users can refer to the karpenter.sh site.

Karpenter simplifies workload scaling, bringing management closer to Kubernetes native APIs compared to alternatives like Autoscaling Groups and Managed Node Groups. It is ideal for clusters with dynamic capacity needs or diverse compute requirements. Users can leverage a mix of dynamically and statically managed nodes based on specific workload demands.

Best practices for Karpenter include many options. For optimal deployment and management of Kubernetes clusters using Karpenter, several key practices are recommended. Firstly, for the Karpenter controller deployment, it is advised to run it on EKS Fargate or a worker node, ensuring that it does not manage the node on which it runs. To enhance flexibility and compatibility, it is recommended to avoid custom launch templates, as they may limit multi-architecture support, automatic node upgrades, and security group discovery. For more granular control over the cluster's resources, exclude specific instance types not needed by the cluster's workloads using the \`node.kubernetes.io/instance-type\` key. When utilizing Spot instances, enabling interruption handling is crucial to gracefully manage upcoming interruption events and maintain the stability of the cluster.

In scenarios where Karpenter is used in a private EKS cluster without internet access, it is important to set up necessary VPC endpoints for essential services such as EC2, ECR, S3, STS, and others to ensure seamless operation. To accommodate different teams sharing a cluster with varying requirements or operating system preferences, creating multiple provisioners is recommended, allowing for better customization and resource allocation.

For efficient resource management, utilizing timers (TTL) is suggested to automatically delete nodes that are either devoid of workload pods or have reached a specified expiration time. Additionally, when specifying instance type constraints, it is advised to avoid overly restrictive configurations, especially when using Spot instances, to optimize resource utilization and flexibility within the cluster. These practices contribute to the effective deployment and management of Kubernetes clusters using Karpenter.

Provisioner best practices include optimizing node provisioning in Kubernetes clusters with diverse requirements, it is advisable to adopt several best practices. Firstly, when catering to different teams with varying needs, creating multiple provisioners allows for the customization of node configurations, ensuring a more tailored approach to resource allocation.

For consistent scheduling behavior, it is important to make provisioners either mutually exclusive or weighted appropriately. This ensures that nodes are allocated based on predefined criteria, maintaining predictability and alignment with specific team requirements.

Utilizing timers, particularly TTL mechanisms, on provisioned nodes proves beneficial for automatic deletion. This feature aids in the seamless management of node upgrades and retirement, contributing to the overall efficiency and maintenance of the cluster. Caution is advised when specifying instance type constraints, especially in the context of Spot instances. Overly constraining instance types can impact availability adversely. Therefore, it is essential to strike a balance, avoiding excessive restrictions to promote better flexibility and availability within the cluster. These practices collectively contribute to a well-managed and adaptable Kubernetes environment that accommodates diverse team needs and ensures optimal resource utilization.

To ensure a robust and well-managed Kubernetes environment with Karpenter, it is essential to adhere to key best practices. Firstly, prioritize high availability by following EKS best practices, which involve spreading pods across nodes and AZs while utilizing Disruption Budgets to control potential disruptions and maintain system stability. For complex provisioning and scheduling scenarios, leverage layered constraints to optimize pod placement effectively. This strategic approach enhances resource allocation and improves overall cluster efficiency.

To maintain cost control and monitor compute spend, establish billing alarms and set resource limits within the Karpenter configuration. This proactive measure ensures better financial oversight and prevents unexpected resource utilization. To safeguard critical nodes from deprovisioning, utilize the \`karpenter.sh/do-not-evict\` annotation on pods. This annotation acts as a preventive measure, ensuring the retention of essential nodes and avoiding potential disruptions.

Lastly, configure accurate resource requests for all workloads, as this is crucial for Karpenter's consolidation feature. By providing precise resource specifications, Karpenter can optimize resource utilization and enhance the overall performance of the Kubernetes cluster. Adhering to these best practices ensures a resilient, cost-effective, and well-optimized Kubernetes environment with Karpenter.

[Cluster Autoscaler](#contents.xhtml#sc3_431a)

The Kubernetes Cluster Autoscaler, maintained by SIG Autoscaling, plays a crucial role in optimizing resource utilization within a Kubernetes cluster. It ensures that the cluster has an adequate number of nodes to accommodate scheduled pods efficiently, preventing both underutilization and resource wastage. The AWS Cloud Provider implementation of the Cluster Autoscaler manages the .DesiredReplicas field in your EC2 Auto Scaling Groups. Configuring the Cluster Autoscaler involves making decisions that align with your organization's specific requirements.

Operating the Cluster Autoscaler involves understanding its deployment as a Deployment in the cluster, utilizing leader election for high availability. It highlights considerations such as version compatibility and the importance of enabling Auto Discovery unless specific advanced use cases dictate otherwise. Configuring Node Groups correctly is foundational for effective autoscaling. Guidelines include ensuring uniform scheduling properties for nodes within a group, addressing considerations for MixedInstancePolicies, and preferring Node Groups with more nodes over having many Node Groups with fewer nodes for enhanced scalability.

To optimize for performance and scalability, we dive into the autoscaling algorithm's runtime complexity and provide insights into tuning factors. Vertical Autoscaling, reducing the number of Node Groups, and adjusting the scan interval are discussed as strategies for achieving optimal performance in large clusters. Advanced use cases such as handling EBS Volumes, co-scheduling for machine learning jobs, and dealing with accelerators are presented. The section also covers the capability of scaling Node Groups to and from zero, with considerations for additional resources and configurations.

[Security best practices](#contents.xhtml#sc2_432a)

Identity and Access Management (IAM) within AWS serves the critical functions of Authentication and Authorization. Authentication verifies identity, and Authorization dictates the actions AWS resources, whether services or IAM principals like Users or Roles, can perform. These rules are expressed through IAM policies. For Amazon EKS, various strategies, including Bearer Tokens, X.509 certificates, and OIDC, authenticate requests to the kube-apiserver service. EKS supports webhook token authentication, service account tokens, and OIDC authentication, allowing users to manually or programmatically generate tokens for secure communication.

[Role-based access control](#contents.xhtml#sc3_433a)

Once a user's identity is authenticated by AWS IAM, the kube-apiserver associates the user with Kubernetes RBAC groups by reading the aws-auth ConfigMap. This ConfigMap, automatically created during EKS provisioning, maps IAM principals to Kubernetes RBAC groups, defining permissible actions on resources. Cluster Access Manager simplifies IAM and Kubernetes RBAC identity mapping in EKS. It introduces Access Entries linked to IAM principals and Access Policies for authorization. With three authentication modes: CONFIG\_MAP, API\_AND\_CONFIG\_MAP, and API, it streamlines access management and reduces operational overhead.

To ensure secure EKS cluster access, best practices include configuring the cluster endpoint to be private, avoiding long-lived service account tokens, and employing least privileged access to AWS resources. Regularly auditing access and utilizing IAM Roles for multiple users are recommended. Alternative approaches, such as OIDC authentication with GitHub or AWS SSO, provide flexibility in authentication methods.

Applications running within a Kubernetes cluster often require permission to access the Kubernetes API. For instance, the AWS Load Balancer Controller needs rights to list Service Endpoints and invoke AWS APIs for provisioning an ALB.

[IAM roles for service accounts](#contents.xhtml#sc3_434a)

Kubernetes service accounts play a crucial role, allowing the assignment of Kubernetes RBAC roles to pods. Default service accounts are automatically created for each Namespace, and when a pod does not specify a service account, the default one gets assigned. Service account tokens, decoded from the mounted volume, contain metadata and permissions for Kubernetes API access. IAM roles for service accounts (IRSA) introduces a way to associate IAM roles with Kubernetes service accounts. Leveraging Service Account Token Volume Projection, the Kubernetes API server signs an OIDC token, granting temporary AWS credentials. AWS SDKs validate the token, allowing pods to call AWS APIs. Recommendations include updating the aws-node daemonset to use IRSA, restricting access to instance profiles, and scoping IAM Role trust policies.

Additional recommendations cover securing applications by running them as non-root users, using dedicated service accounts, and implementing least privileged access. These practices collectively enhance security, ensuring granular control over permissions and minimizing potential vulnerabilities in Kubernetes clusters. The pod specification in Kubernetes involves various attributes affecting overall security, with a primary focus on preventing processes from escaping container isolation. Processes within containers typically run as the root user, constrained by Linux capabilities. Default capabilities can pose security risks, especially for EC2 and Fargate pods, which have specific default capabilities that can only be dropped from Fargate pods. Privileged pods inherit all Linux capabilities associated with the host's root, emphasizing the need to avoid such configurations.

Node Authorization in Kubernetes worker nodes grants permissions for read, write, and auth-related operations. While EKS employs the node restriction admission controller, limiting node modifications, an attacker with host access could still gather sensitive information from the Kubernetes API, enabling lateral movement within the cluster. Pod Security Solutions are crucial for enhancing security. Pod Security Policy (PSP), though deprecated, was used to specify pod creation requirements. As of Kubernetes v1.25, alternatives like Policy-as-Code (PAC) solutions and Kubernetes Pod Security Standards (PSS) should replace PSP. PAC solutions like OPA/Gatekeeper, Kyverno, and Kubewarden provide automated controls, while PSS defines three security policies, Privileged, Baseline, and Restricted, controlling pod execution. Pod Security Admission (PSA) enforces, audits, or warns based on these policies and operates at the namespace level, allowing granular security configurations. Exemptions in PSA provide flexibility by excluding certain pods based on usernames, runtime class names, or namespaces.

The Validating Webhook implementation in Kubernetes allows configuring exemptions through a ConfigMap resource. The provided YAML example sets cluster-wide default Pod Security Standards (PSS) levels for audit, enforce, and warn modes, with exemptions specified for certain namespaces. The exemptions, such as usernames, runtime class names, and namespaces, are defined in the ConfigMap. Additionally, exemptions are applied to the ValidatingWebhookConfiguration to avoid circular dependencies.

While PSS provides a built-in Kubernetes solution, PAC solutions offer more flexibility and granularity. Pros and cons for both approaches are outlined, aiding in making an informed decision based on the specific security needs and preferences. It also addresses issues related to privileged escalation, ServiceAccount token mounts, and service discovery. Finally, configuring images with a read-only root file system is recommended to prevent unauthorized overwrites, and the use of PAC and PSS for enforcement is highlighted. In multi-tenancy, the aim is often to shield users or applications from each other within a shared infrastructure. Kubernetes, as a single tenant orchestrator, employs constructs like Namespaces, Role-based access control (RBAC), Quotas, and Limit Ranges to simulate multi-tenancy. While these offer logical isolation, the cluster itself remains a robust security boundary.

The concept of soft multi-tenancy utilizes native Kubernetes elements such as Namespaces, roles, and network policies for logical separation. Tools like Kiosk and Loft enhance this approach, providing features like self-service namespace provisioning and multi-cluster access. Use cases for soft multi-tenancy include enterprise settings, Kubernetes as a Service (KaaS), and Software as a Service (SaaS). Key constructs like Namespaces, network policies, RBAC, Quotas, and Pod priority are pivotal in isolating tenants. However, to bolster security, controls like sandboxed execution environments, Open Policy Agent (OPA) with Gatekeeper, and Kyverno are recommended. For more stringent isolation in soft multi-tenancy, techniques like node affinity, taints, and tolerations are employed. Policy-based management tools ensure correct application of these techniques. However, certain scenarios, especially in highly-regulated industries, may necessitate the adoption of hard multi-tenancy, where separate clusters are provisioned for each tenant, ensuring stronger isolation but at the cost of increased complexity and resource usage.

[Hierarchical Namespace Controller](#contents.xhtml#sc3_435a)

The Kubernetes community is actively addressing the challenges of multi-tenancy through projects like Hierarchical Namespace Controller (HNC) and virtual cluster, aiming to enhance soft multi-tenancy and explore new directions in the field. The Multi-Tenancy Special Interest Group (SIG) provides guidelines for sharing clusters and validates conformance through tools like kubectl-mtb. The provided text discusses the importance of collecting and analyzing audit logs in a Kubernetes environment, specifically focusing on Amazon EKS. The audit logs are crucial for root cause analysis, attribution of changes to users, and detecting anomalous behaviors. The audit policy for EKS is outlined, specifying rules for logging various activities such as configmap changes, user actions, and authorization decisions.

Network security in the context of Amazon EKS involves multiple facets, each addressing different aspects of securing network traffic. The first aspect pertains to controlling the flow of network traffic between services, achieved through the application of rules. Network policies, security groups, and encryption mechanisms are employed for this purpose. The second facet focuses on encrypting traffic while it is in transit. Various tools such as service mesh, Container Network Interfaces (CNIs), ingress controllers, load balancers, Nitro instances, and ACM Private CA with cert-manager are utilized to implement encryption. In the realm of network policies, Kubernetes employs mechanisms like network policies, security groups, and ingress controllers to manage the flow of traffic. Kubernetes network policies, operating at layers 3 and 4 of the OSI model, enable the restriction of communication between pods and external services, offering a secure framework for East/West traffic. Recommendations for establishing secure network policies include creating a default deny policy and incrementally adding rules to selectively allow traffic between namespaces or pods.

[Open Policy Agent](#contents.xhtml#sc3_436a)

Monitoring and enforcing network policies are crucial for maintaining security. Network policy editor, audit logs, automated testing, and regular monitoring of metrics are suggested practices. The use of Open Policy Agent (OPA) can ensure that network policies exist before onboarding application pods. Troubleshooting network policy enforcement involves monitoring VPC CNI controller logs, enabling control plane controller manager logs, and leveraging VPC Flow Logs. Security groups play a vital role in controlling traffic within an EKS cluster, and recommendations include following the principle of least privilege, segmenting applications, and using a combination of security groups and Kubernetes network policies for layered security. Encryption in transit is essential for applications adhering to regulations like PCI and HIPAA. TLS is the preferred choice for encrypting traffic, and different methods are available, including Nitro instances, CNIs, service mesh, and ingress controllers. AWS Elastic Load Balancers, ACM Private CA with cert-manager, and Istio are highlighted for implementing encryption in various scenarios.

[Mutual TLS](#contents.xhtml#sc3_437a)

ACM Private CA with cert-manager is particularly emphasized for securing EKS application workloads. The use of short-lived CA mode is recommended for mutual TLS (mTLS) between workloads. Instructions for setting up ACM Private CA with cert-manager, including IAM permissions and creating issuers, are provided. AppArmor and SELinux, categorized as mandatory access control systems, are compared to seccomp, with their integration into Kubernetes noted. Recommendations include using Amazon GuardDuty for runtime monitoring in EKS environments offering threat detection through AWS CloudTrail and VPC flow logs. Third-party solutions for runtime monitoring and leveraging ML for threat detection are suggested as alternatives. Considerations for capabilities, PSPs, and using third-party solutions before delving into manual security configurations are also presented.

The importance of periodically running kube-bench, an open-source tool, to verify compliance with CIS benchmarks for Kubernetes is highlighted. Additional recommendations include deploying workers onto private subnets to minimize exposure to the internet, leveraging Amazon Inspector to assess hosts for vulnerabilities, and considering alternatives like running SELinux for an additional layer of container isolation.

Firstly, creating minimal images is advised by removing extraneous binaries and avoiding unnecessary utilities, enhancing security by reducing the attack surface of the image. Multi-stage builds are recommended for automation, allowing developers to receive immediate feedback during the continuous integration cycle and resulting in smaller final images. Additionally, generating a Software Bill of Materials (SBOM) for container images is crucial for software security and supply chain risk management, offering visibility, provenance verification, trustworthiness, and dependency trust verification. Regularly scanning container images for vulnerabilities is emphasized, and tools like Amazon Inspector, Syft, and others are suggested for generating and scanning SBOMs.

Additional recommendations include creating IAM policies for ECR repositories to manage access, using ECR private endpoints for secure access within a VPC, implementing endpoint policies for ECR to control access, setting lifecycle policies to manage image expiration, and curating a set of vetted images to enhance security. Further practices involve adding the USER directive to Dockerfiles, linting Dockerfiles to ensure adherence to guidelines, building images from scratch for minimalism, using immutable tags for versioning, and signing images, SBOMs, pipeline runs, and vulnerability reports for integrity verification.

In the centralized EKS cluster approach, the EKS cluster is deployed in a single AWS account known as the cluster account. This account contains the VPC, subnets, EKS cluster, compute resources, and networking configurations needed for the EKS cluster. Workloads are organized into separate AWS accounts called workload accounts, and AWS Resource Access Manager (RAM) is used to share subnets from the cluster account into workload accounts. IAM roles for service accounts (IRSA) or EKS Pod Identities are employed to deliver temporary AWS credentials to pods, allowing them to access resources in workload accounts.

The de-centralized EKS clusters approach involves deploying EKS clusters in respective workload AWS accounts, alongside other AWS resources. Each workload account is independent and operated by respective business unit/application teams. This model allows for reusable blueprints for different cluster capabilities, and GitOps is employed for managing application and infrastructure deployments. IAM roles for service accounts or EKS Pod Identities are utilized for secure AWS resource access, with no cross-account access required.

[Conclusion](#contents.xhtml#sc2_438a)

In this chapter, you gained a comprehensive understanding of the multifaceted facets of Amazon EKS best practices. The integration of security fortifications ensures a resilient defense against potential threats, while the implementation of efficient autoscaling mechanisms guarantees adaptability to varying workloads. Deliberate considerations for reliability, coupled with adept networking configurations, create a foundation that safeguards against failures and facilitates secure communication within clusters. Furthermore, scalability strategies, upgrade methodologies, and prudent cost optimization techniques collectively contribute to a robust framework for deploying and maintaining EKS clusters.

As you conclude this chapter in your EKS journey, it is essential to recognize that mastery is an ongoing pursuit. The cloud landscape evolves, introducing new technologies and practices. We encourage you to remain proactive, staying abreast of emerging trends and continually refining your expertise. Embrace the dynamic nature of the cloud, as doing so will empower you to harness the full potential of Amazon EKS and navigate future challenges with confidence and agility.

[Questions](#contents.xhtml#sc2_439a)

1.  How can IAM roles be leveraged to enhance security within an Amazon EKS cluster?
2.  Describe the key components and considerations when implementing Cluster Autoscaler for EKS.
3.  What are the critical aspects to address for ensuring reliability in an EKS environment, especially in terms of fault tolerance?
4.  Discuss the networking considerations and configurations that contribute to a secure and efficient EKS cluster.
5.  In the context of cost optimization for EKS, elaborate on the strategies to make resource usage more efficient.

[Exercises](#contents.xhtml#sc2_440a)

1.  Implement IAM roles for service accounts to enhance security within an EKS cluster. Associate these roles with specific pods and verify their access permissions.
2.  Set up and configure Cluster Autoscaler for an EKS cluster. Simulate workload changes and observe how the cluster dynamically adjusts its resources.
3.  Create and apply network policies to control pod communication within an EKS cluster. Test the policies by deploying sample applications with distinct networking requirements.

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [CHAPTER 22Data Workloads on Amazon EKS](#contents.xhtml#ch22a)

[Introduction](#contents.xhtml#sc2_441a)

In the rapidly evolving field of cloud computing, Amazon Elastic Kubernetes Service (EKS) stands out as a robust platform for orchestrating containerized applications. This chapter takes a deep dive into data workloads on Amazon EKS, offering insights into various methods and strategies to seamlessly run diverse data-centric applications. From large-scale data processing with Apache Spark to interactive data analysis using Jupyter Notebooks, and leveraging the distributed querying capabilities of Trino, this chapter comprehensively covers a spectrum of data workloads on Amazon EKS.

Apache Spark, Jupyter Notebooks, Apache Trino, and Apache Superset are transformative tools reshaping data processing, analysis, and visualization in the cloud. The integration of these powerful platforms with Amazon EKS introduces new dimensions of scalability, efficiency, and containerized deployment. This comprehensive chapter intricately explores the setup of EKS clusters tailored for each of these tools, detailing their configuration and deployment within the Kubernetes environment, and unleashing their full potential within a cloud-native architecture.

[Structure](#contents.xhtml#sc2_442a)

In this chapter, we will cover the following topics:

*   Apache Spark on EKS
*   Jupyter Notebooks on EKS
*   Apache Trino on EKS
*   Apache Superset on EKS

[Objectives](#contents.xhtml#sc2_443a)

In pursuit of its main goal, this chapter strives to provide readers with the knowledge and hands-on proficiency necessary to fully utilize Apache Spark, Jupyter Notebooks, Apache Trino, and Apache Superset within the Amazon EKS ecosystem. The step-by-step instructions and best practices detailed throughout the chapter are structured to empower readers, ensuring they not only comprehend the theoretical aspects but also develop the practical skills to create and manage scalable, containerized environments. Readers will discover the capacity to handle diverse data tasks, including processing, interactive analysis, distributed querying, and data visualization within the context of Amazon EKS.

Moreover, the chapter places a strong emphasis on equipping readers with expertise beyond the basics. By offering insights into optimization, security measures, and seamless integration with AWS services, the chapter aims to go beyond foundational knowledge. Readers are guided through the intricacies of optimizing these tools for performance, ensuring secure data workflows, and integrating them seamlessly with AWS services. This holistic approach aims to empower readers to navigate the complexities of data processing on Amazon EKS with a comprehensive skill set, fostering a robust and streamlined data workflow in a cloud-native environment.

[Apache Spark on EKS](#contents.xhtml#sc2_444a)

Apache Spark, renowned for its distributed data processing capabilities, seamlessly integrates with Amazon EKS, providing a scalable and efficient environment for executing Spark applications. Let us explore the process of setting up an Amazon EKS cluster optimized for Spark workloads using eksctl, configuring Spark on EKS with the Spark Operator, and submitting a sample Spark job. Start by ensuring the prerequisites are met on your local machine, including the installation of the AWS CLI, eksctl, and kubectl. With these tools in place, you can initiate the creation of an EKS cluster using eksctl. Define the desired configurations, such as the region, node group specifications, and instance types. This step lays the foundation for hosting Spark applications within the EKS cluster, i.e., you could create a new EKS cluster using the following eksctl command:

eksctl create cluster \\

 --name my-spark-cluster \\

 --version 1.28 \\

 --nodegroup-name spark-workers \\

 --node-type m5.xlarge \\

 --nodes 3 \\

 --nodes-min 3 \\

 --nodes-max 6 \\

 --region us-west-2

The following figure shows the architecture diagram of running a Spark job on EKS:

![](images/Figure_22.1.png)

Figure 22.1: Spark on EKS - Flow diagram

Upon successful cluster creation, update your local kubeconfig file using kubectl to enable seamless communication with the EKS cluster. This step ensures that subsequent commands and configurations are applied to the correct EKS environment. The following command adds the cluster to detail the ./kube/config to access it:

aws eks update-kubeconfig --name my-spark-cluster --region us-west-2

Replace my-spark-cluster and us-west-2 with your cluster name and region, respectively. With the EKS cluster set up, the next phase involves deploying Spark on EKS. Leverage the Spark Operator, a Kubernetes-native application that simplifies Spark application management. Utilize custom resources like SparkApplications to define properties and resource requirements. This approach streamlines the deployment and maintenance of Spark applications within the EKS environment. Apply the Spark Operator to your EKS cluster using the following command:

kubectl apply -f https://raw.githubusercontent.com/GoogleCloudPlatform/spark-on-k8s-operator/master/manifest/spark-operator.yaml

Create a spark-app.yaml file with the following YAML file:

apiVersion: spark.apache.org/v1beta2

kind: SparkApplication

metadata:

 name: spark-pi

 namespace: default

spec:

 type: Scala

 mode: cluster

 image: gcr.io/spark-operator/spark:v3.1.2

 imagePullPolicy: Always

 mainApplicationFile: local:///opt/spark/examples/jars/spark-examples.jar

 mainClass: org.apache.spark.examples.SparkPi

 driver:

 cores: 1

 coreLimit: "1200m"

 memory: "512m"

 labels:

 version: 3.1.2

 serviceAccount: spark

 executor:

 cores: 1

 instances: 2

 memory: "512m"

 labels:

 version: 3.1.2

This file defines a SparkApplication resource that runs the SparkPi example job using the Spark 3.1.2 image. Apply the SparkApplication resource to your EKS cluster with the following command:

kubectl apply -f spark-app.yaml

Watch the progress of the Spark job by monitoring the logs:

kubectl logs spark-pi-driver -f

You can also access the Spark UI by forwarding the port:

kubectl port-forward spark-pi-driver 4040:4040

Then, open your web browser and navigate to [http://localhost:4040](http://localhost:4040) to access the Spark UI. To submit a sample Spark job, package your Spark application into a JAR file, including all necessary dependencies. Use kubectl to submit the Spark job to the EKS cluster, specifying parameters such as the JAR file, main class, and any additional requirements. This triggers the execution of the Spark job within the containerized environment on EKS.

Monitoring the progress and performance of Spark applications on EKS is crucial for effective management. Leverage tools such as the Spark UI and Kubernetes Dashboard to gain insights into tasks, stages, and resource utilization. These interfaces facilitate real-time monitoring and troubleshooting, ensuring optimal performance. Optimizing Spark configurations for EKS involves adjusting parameters to align with the resources available in the cluster. Experiment with executor memory, cores, and parallelism to achieve an optimal balance between performance and resource utilization. Fine-tune these configurations based on the specific requirements of your Spark applications.

Dynamic scaling of Spark applications on EKS is simplified using Kubernetes capabilities. Utilize kubectl commands to adjust the number of Spark executor instances dynamically, responding to changing workload demands. This elasticity ensures efficient resource utilization and responsiveness to varying data processing requirements. Scaling considerations extend beyond dynamic adjustments; plan for scaling Spark applications horizontally by distributing tasks across multiple nodes within the EKS cluster. This approach capitalizes on the distributed nature of Spark, enhancing parallel processing and overall performance.

The security of Spark applications on EKS is paramount. Implement best practices, such as utilizing Kubernetes role-based access control (RBAC) to restrict access to resources, encrypting communication channels, and securing sensitive data within the EKS environment. To streamline the deployment pipeline, consider incorporating tools like Helm charts for managing Spark configurations and dependencies. Helm simplifies the packaging and deployment of complex applications on EKS, promoting consistency and repeatability in Spark application deployments.

Maintaining an efficient and cost-effective EKS environment involves regular monitoring of resource utilization. Utilize AWS Cost Explorer and CloudWatch to gain insights into the costs associated with the EKS cluster, helping optimize resource allocation and control expenses. Explore integrations with AWS services such as Amazon S3 for efficient data storage and retrieval within Spark applications. Leverage the scalability and durability of S3 for handling large datasets, enhancing the overall performance of Spark jobs on EKS.

Implementing high availability strategies is crucial for ensuring the resilience of Spark applications on EKS. Explore options like deploying Spark across multiple availability zones and utilizing Kubernetes features for pod rescheduling in the event of node failures. Regularly update Spark and EKS components to benefit from the latest features, security patches, and optimizations. Follow best practices for managing version compatibility between Spark and Kubernetes to ensure a stable and up-to-date environment. Collaboration and knowledge sharing are essential aspects of optimizing Spark on EKS. Engage with the community through forums, documentation, and events to stay informed about best practices, emerging trends, and potential challenges in Spark application development and deployment on EKS.

In conclusion, running Apache Spark on Amazon EKS involves a comprehensive journey, encompassing cluster creation, deployment with the Spark Operator, submission of Spark jobs, monitoring, optimization, and scaling considerations. This integration harnesses the strengths of both Spark and EKS, providing a robust foundation for scalable and efficient data processing in the cloud.

[Jupyter Notebooks on EKS](#contents.xhtml#sc2_445a)

Running Jupyter Notebooks on Amazon EKS opens the door to interactive and collaborative data analysis in a scalable, containerized environment. Let us explore the detailed steps, from creating an EKS cluster optimized for Jupyter workloads using eksctl to configuring and deploying Jupyter Notebooks on EKS. The following diagram shows the architecture for running Jupyter Notebook on EKS:

![](images/Figure_22.2.png)

Figure 22.2: Jupyter Notebooks on EKS - Architecture diagram

Begin by ensuring your local machine has the necessary prerequisites, including the AWS CLI, eksctl, and kubectl. These tools will be instrumental in creating and interacting with the EKS cluster. Use eksctl to initiate the creation of the EKS cluster, specifying parameters such as the region, node group configurations, and instance types, tailored for optimal Jupyter Notebook processing. Create the cluster using the following command:

eksctl create cluster \\

 --name my-jupyter—cluster \\

 --version 1.28 \\

 --nodegroup-name jupyter-node-group \\

 --node-type m5.xlarge \\

 --nodes 3 \\

 --nodes-min 3 \\

 --nodes-max 6 \\

 --region us-west-2

Upon successful cluster creation, update your local kubeconfig file using kubectl to establish seamless communication with the EKS cluster. This ensures that subsequent configurations and deployments are targeted to the correct EKS environment. The following command adds the cluster to detail the ./kube/config to access it:

aws eks update-kubeconfig --name my-jupyter-cluster --region us-west-2

With the EKS cluster ready, proceed to configure and deploy Jupyter Notebooks. Utilize Helm, a package manager for Kubernetes, to simplify the installation of JupyterHub, a multi-user Jupyter Notebook server. Customize the Helm chart to specify configurations such as authentication mechanisms, user storage, and resource allocation. Create a namespace for Jupyter Notebook. The following command creates a namespace for the Jupyter Notebook:

kubectl create namespace jupyter-notebook

Create a jupyter-notebook.yaml file with the following YAML:

apiVersion: apps/v1

kind: Deployment

metadata:

 name: jupyter-notebook

 namespace: jupyter-notebook

spec:

 replicas: 1

 selector:

 matchLabels:

 app: jupyter-notebook

 template:

 metadata:

 labels:

 app: jupyter-notebook

 spec:

 containers:

 - name: jupyter-notebook

 image: jupyter/scipy-notebook:latest

 ports:

 - containerPort: 8888

 volumeMounts:

 - name: data

 mountPath: /home/jovyan

 volumes:

 - name: data

 emptyDir: {}

Apply the deployment:

kubectl apply -f jupyter-notebook.yaml -n jupyter-notebook

Create a jupyter-notebook-service.yaml file with the following YAML:

apiVersion: v1

kind: Service

metadata:

 name: jupyter-notebook

 namespace: jupyter-notebook

spec:

 type: LoadBalancer

 selector:

 app: jupyter-notebook

 ports:

 - port: 80

 targetPort: 8888

Apply the service with the following command:

kubectl apply -f jupyter-notebook-service.yaml -n jupyter-notebook

Get the external IP address. Wait for the LoadBalancer service to get an external IP address, by using the following command:

kubectl get service jupyter-notebook -n jupyter-notebook –watch

Once the EXTERNAL-IP column is populated, you can access the Jupyter Notebook using that IP address in your web browser at http://<external-ip>. Connect to Spark from Jupyter Notebook. In the Jupyter Notebook, create a new Python notebook and add the following code to connect to Spark on EKS:

import os

import pyspark

\# Configure Spark

master\_url = "k8s://https://" + os.environ\["KUBERNETES\_SERVICE\_HOST"\] + ":" + os.environ\["KUBERNETES\_SERVICE\_PORT\_HTTPS"\]

spark = pyspark.sql.SparkSession.builder \\

 .master(master\_url) \\

 .appName("jupyter-spark") \\

 .getOrCreate()

\# Example usage

data = spark.range(100).toDF("value")

data.show()

This code creates a SparkSession connected to the Kubernetes cluster, allowing you to run Spark jobs from within the Jupyter Notebook. Once JupyterHub is deployed, users can access the Jupyter Notebook interface, creating individual notebooks for interactive data analysis. Leverage the Jupyter ecosystem by installing additional libraries and extensions and tailoring the environment to specific data processing requirements.

Optimizing Jupyter Notebooks on EKS involves tuning resource allocations to match the demands of interactive data analysis. Adjust parameters such as CPU and memory limits for JupyterHub pods to ensure a responsive and performant user experience. For enhanced security, implement measures such as utilizing HTTPS for secure communication with Jupyter Notebooks, configuring authentication mechanisms, and restricting access through Kubernetes RBAC. These practices safeguard sensitive data and promote secure collaboration within the Jupyter environment on EKS.

Scaling Jupyter Notebooks on EKS can be achieved by dynamically adjusting the number of replicas for JupyterHub pods based on user demand. Utilize kubectl commands to scale the deployment horizontally, ensuring efficient resource utilization during peak usage periods. Integrate Jupyter Notebooks with data stored in Amazon S3 or other AWS services to streamline data access and enhance collaboration. Leverage the flexibility and scalability of cloud storage to handle diverse datasets within the Jupyter environment on EKS.

Regularly monitor the usage and performance of Jupyter Notebooks on EKS using tools like Prometheus and Grafana. These monitoring solutions provide insights into resource utilization, user activity, and potential issues, enabling proactive management and optimization. To enhance collaboration and knowledge sharing, explore options for persistent storage of Jupyter Notebooks. Utilize storage solutions such as Amazon EBS or Amazon EFS to ensure data persistence across pod restarts or scaling events.

Consider implementing version control for Jupyter Notebooks using tools like Git. This facilitates collaboration, enables tracking of changes, and provides a structured approach to managing code and data within the Jupyter environment on EKS. Explore advanced features of Jupyter Notebooks, such as interactive widgets, custom visualizations, and integrations with ML frameworks. Harness the extensibility of Jupyter to create rich and interactive data analysis experiences within the EKS environment.

Regularly update JupyterHub, Helm charts, and other dependencies to benefit from the latest features, security patches, and optimizations. Follow best practices for managing version compatibility between Jupyter components and Kubernetes to ensure a stable and up-to-date environment. Engage with the Jupyter and Kubernetes communities through forums, documentation, and events to stay informed about best practices, emerging trends, and potential challenges in running Jupyter Notebooks on EKS.

In conclusion, running Jupyter Notebooks on Amazon EKS involves a detailed journey encompassing cluster creation, deployment with Helm and JupyterHub, customization, optimization, security considerations, scaling, integration with AWS services, monitoring, and continuous improvement. This integration offers a robust foundation for collaborative and scalable data analysis within a containerized environment.

[Apache Trino on EKS](#contents.xhtml#sc2_446a)

Integrating Apache Trino, formerly known as PrestoSQL, with Amazon EKS opens the door to powerful distributed querying capabilities in a containerized environment. Let us explore the detailed steps, from creating an EKS cluster optimized for Trino workloads using eksctl to deploying Trino clusters on EKS and connecting them to data sources. Start by ensuring your local machine is equipped with the necessary tools, including the AWS CLI, eksctl, and kubectl. These tools will play a crucial role in creating and interacting with the EKS cluster. Utilize eksctl to initiate the creation of the EKS cluster, specifying parameters such as the region, node group configurations, and instance types optimized for efficient Trino processing. You could create a new EKS cluster using the following eksctl command:

eksctl create cluster \\

 --name my-trino-cluster \\

 --version 1.28 \\

 --nodegroup-name trino-workers-ng \\

 --node-type m5.xlarge \\

 --nodes 3 \\

 --nodes-min 3 \\

 --nodes-max 6 \\

 --region us-west-2

Upon successful cluster creation, update your local kubeconfig file using kubectl to establish seamless communication with the EKS cluster. This ensures that subsequent configurations and deployments are directed to the correct EKS environment. The following command adds the cluster to detail the ./kube/config to access it:

aws eks update-kubeconfig --name my-spark-cluster --region us-west-2

With the EKS cluster ready, proceed to deploy Trino clusters on EKS. Leverage Helm, a package manager for Kubernetes, to simplify the installation of Trino coordinator and worker nodes. Customize the Helm chart to define configurations such as connector settings, memory allocations, and resource constraints based on the anticipated workloads. Once the Trino clusters are deployed, configure them to connect to relevant data sources. Utilize Trino connectors to establish connections with databases, data lakes, or other storage systems. Customize the Trino configuration files to specify details such as connection strings, authentication mechanisms, and query optimization settings. Create a Namespace for Trino with the following command:

kubectl create namespace trino

Deploy the Trino coordinator. Create a trino-coordinator.yaml file with the following YAML:

apiVersion: apps/v1

kind: Deployment

metadata:

 name: trino-coordinator

 namespace: trino

spec:

 replicas: 1

 selector:

 matchLabels:

 app: trino-coordinator

 template:

 metadata:

 labels:

 app: trino-coordinator

 spec:

 containers:

 - name: trino-coordinator

 image: trinodb/trino:latest

 command: \["bin/launcher", "run"\]

 ports:

 - containerPort: 8080

 volumeMounts:

 - name: config

 mountPath: /docker/cluster

 volumes:

 - name: config

 emptyDir: {}

Apply the deployment by using the following kubectl command, which creates the Trino deployment:

kubectl apply -f trino-coordinator.yaml -n trino

Create a Service for Trino coordinator by creating a trino-coordinator-service.yaml file with the following YAML:

apiVersion: v1

kind: Service

metadata:

 name: trino-coordinator

 namespace: trino

spec:

 selector:

 app: trino-coordinator

 ports:

 - port: 8080

 targetPort: 8080

Apply the service:

kubectl apply -f trino-coordinator-service.yaml -n trino

Deploy the Trino workers by creating a trino-workers.yaml file with the following content:

apiVersion: apps/v1

kind: Deployment

metadata:

 name: trino-workers

 namespace: trino

spec:

 replicas: 2

 selector:

 matchLabels:

 app: trino-workers

 template:

 metadata:

 labels:

 app: trino-workers

 spec:

 containers:

 - name: trino-worker

 image: trinodb/trino:latest

 command: \["bin/launcher", "run"\]

 env:

 - name: TRINO\_COORDINATOR

 value: trino-coordinator

Apply the deployment:

kubectl apply -f trino-workers.yaml -n trino

Access Trino Web UI by getting the cluster IP of the Trino Coordinator Service:

kubectl get service trino-coordinator -n trino

You can access the Trino Web UI using the cluster IP at [http://cluster-ip:8080](http://cluster-ip:8080). To connect to Trino from a client, you need to expose the Trino coordinator service as a LoadBalancer or NodePort service. Modify the trino-coordinator-service.yaml file to change the service type:

apiVersion: v1

kind: Service

metadata:

 name: trino-coordinator

 namespace: trino

spec:

 type: LoadBalancer # or NodePort

 selector:

 app: trino-coordinator

 ports:

 - port: 8080

 targetPort: 8080

Apply the updated service:

kubectl apply -f trino-coordinator-service.yaml -n trino

Get the external IP (for LoadBalancer) or node IP and port (for NodePort):

kubectl get service trino-coordinator -n trino

You can then connect to Trino using a client like the Trino CLI or a SQL client, specifying the external IP or node IP and port. To optimize Trino for performance on EKS, fine-tune configurations such as memory allocations, concurrency limits, and resource utilization. Experiment with different settings to achieve the desired balance between query performance and resource efficiency in the containerized environment.

For security considerations, implement encryption for communication between Trino nodes and data sources. Leverage network policies within Kubernetes to control communication between Trino clusters and other pods within the EKS environment, ensuring secure data querying and transmission. Scaling Trino clusters on EKS is facilitated by the dynamic scalability of Kubernetes. Utilize kubectl commands to adjust the number of Trino worker nodes based on query loads, providing flexibility to handle varying workloads efficiently.

Monitor the performance of Trino clusters on EKS using tools like Prometheus and Grafana. These monitoring solutions offer insights into query execution times, resource utilization, and potential bottlenecks, enabling proactive management and optimization. Integrate Trino clusters with data stored in Amazon S3 or other AWS services to leverage the scalability and flexibility of cloud storage. Customize Trino connectors to efficiently query and analyze data across different storage systems within the EKS environment. Regularly update Trino, Helm charts, and other dependencies to stay abreast of the latest features, security patches, and optimizations. Follow best practices for managing version compatibility between Trino components and Kubernetes to ensure a stable and up-to-date environment.

Engage with the Trino and Kubernetes communities through forums, documentation, and events to stay informed about best practices, emerging trends, and potential challenges in running Trino clusters on EKS. In conclusion, running Apache Trino on Amazon EKS involves a detailed journey encompassing cluster creation, deployment with Helm, configuration, optimization, security considerations, scaling, integration with AWS services, monitoring, and continuous improvement. This integration offers a robust foundation for distributed querying within a containerized environment, unlocking the full potential of Trino on EKS.

[Apache Superset on EKS](#contents.xhtml#sc2_447a)

Exploring the integration of Apache Superset with Amazon EKS provides a scalable and containerized environment for interactive data visualization and exploration. Let us dive into the detailed steps, from creating an EKS cluster optimized for Apache Superset workloads using eksctl to deploying and configuring Apache Superset on EKS.

Ensure your local machine is equipped with essential tools, including the AWS CLI, eksctl, and kubectl. These tools play a crucial role in creating and interacting with the EKS cluster. Initiate the creation of the EKS cluster using eksctl, specifying parameters such as the region, node group configurations, and instance types tailored for optimal Apache Superset processing. You could create a new EKS cluster using the following eksctl command:

eksctl create cluster \\

 --name my-superset-cluster \\

 --version 1.28 \\

 --nodegroup-name superset-ng \\

 --node-type m5.xlarge \\

 --nodes 3 \\

 --nodes-min 3 \\

 --nodes-max 6 \\

 --region us-west-2

Upon successful cluster creation, update your local kubeconfig file using kubectl to establish seamless communication with the EKS cluster. This ensures that subsequent configurations and deployments are directed to the correct EKS environment. The following command adds the cluster to detail the ./kube/config to access it:

aws eks update-kubeconfig --name my-spark-cluster --region us-west-2

With the EKS cluster prepared, proceed to deploy Apache Superset on EKS. Leverage Helm, a package manager for Kubernetes, to simplify the installation of Apache Superset. Customize the Helm chart to specify configurations such as database connections, authentication mechanisms, and resource allocations based on anticipated workloads. Create a Namespace for Superset with the following command:

kubectl create namespace superset

Deploy Superset by creating a superset.yaml file with the following content:

apiVersion: apps/v1

kind: Deployment

metadata:

 name: superset

 namespace: superset

spec:

 replicas: 1

 selector:

 matchLabels:

 app: superset

 template:

 metadata:

 labels:

 app: superset

 spec:

 containers:

 - name: superset

 image: apache/superset:latest

 ports:

 - containerPort: 8088

 env:

 - name: MAPBOX\_API\_KEY

 valueFrom:

 secretKeyRef:

 name: superset-secrets

 key: mapbox-api-key

 volumeMounts:

 - name: superset-data

 mountPath: /app/superset\_home

 volumes:

 - name: superset-data

 emptyDir: {}

This deployment assumes you have a secret named superset-secrets with a mapbox-api-key key. If you do not need Mapbox integration, you can remove the environment variable section. Apply the deployment:

kubectl apply -f superset.yaml -n superset

Create a Service for Superset by creating a superset-service.yaml file with the following YAML snippet:

apiVersion: v1

kind: Service

metadata:

 name: superset

 namespace: superset

spec:

 type: LoadBalancer

 selector:

 app: superset

 ports:

 - port: 80

 targetPort: 8088

Apply the service:

kubectl apply -f superset-service.yaml -n superset

Get the external IP address. Wait for the LoadBalancer service to get an external IP address:

kubectl get service superset -n superset --watch

Once the EXTERNAL-IP column is populated, you can access Superset using that IP address in your web browser at http://<external-ip>. After accessing Superset for the first time, you will be prompted to create an admin user account. Follow the instructions to set up the initial admin user. The following screen shows the typical login screen to log into a superset:

![](images/Figure_22.3.png)

Figure 22.3: Superset login screen

In the Superset UI, navigate to Sources | Databases and add a new database connection. You can connect Superset to various databases like PostgreSQL, MySQL, or Amazon Athena. The following screen shows the different dashboard and charts sections once logged in:

![](images/Figure_22.4.png)

Figure 22.4: Superset dashboard screen

Configure Apache Superset to connect to relevant data sources by setting up database connections within the Superset interface. Customize connection details, credentials, and other parameters to establish seamless communication with databases, data lakes, or other storage systems.

Optimize Apache Superset for performance on EKS by fine-tuning configurations such as worker counts, caching settings, and resource utilization. Experiment with different settings to achieve the desired balance between interactive visualization responsiveness and resource efficiency in the containerized environment. Consider security measures such as enabling HTTPS for secure communication with Apache Superset, configuring authentication mechanisms, and implementing RBAC within Kubernetes. These practices safeguard sensitive data and ensure secure exploration within the Apache Superset environment on EKS.

Scaling Apache Superset on EKS is facilitated by the dynamic scalability of Kubernetes. Utilize kubectl commands to adjust the number of Apache Superset pods or replicas based on user demand, providing flexibility to handle varying workloads efficiently. Monitor the performance of Apache Superset on EKS using tools like Prometheus and Grafana. These monitoring solutions offer insights into user activity, query performance, and resource utilization, enabling proactive management and optimization.

Integrate Apache Superset with data stored in Amazon S3 or other AWS services to leverage the scalability and flexibility of cloud storage. Customize Superset connections to efficiently visualize and explore data across different storage systems within the EKS environment. Regularly update Apache Superset, Helm charts, and other dependencies to stay current with the latest features, security patches, and optimizations. Follow best practices for managing version compatibility between Apache Superset components and Kubernetes to ensure a stable and up-to-date environment.

Engage with the Apache Superset and Kubernetes communities through forums, documentation, and events to stay informed about best practices, emerging trends, and potential challenges in running Apache Superset on EKS. To summarize, running Apache Superset on Amazon EKS involves a comprehensive journey encompassing cluster creation, deployment with Helm, configuration, optimization, security considerations, scaling, integration with AWS services, monitoring, and continuous improvement. This integration provides a robust foundation for interactive data visualization and exploration within a containerized environment, unlocking the full potential of Apache Superset on EKS.

[Conclusion](#contents.xhtml#sc2_448a)

Running Apache Spark, Jupyter Notebooks, Apache Trino, and Apache Superset on Amazon EKS represents a paradigm shift in data processing and analytics. By embracing the principles of containerization and leveraging the scalability and flexibility of Kubernetes, organizations can unlock new levels of efficiency, collaboration, and insights. This comprehensive chapter serves as a valuable resource for data engineers, analysts, and professionals seeking to embark on a journey of modern, cloud-native data processing and visualization. Through detailed explanations, practical examples, and best practices, readers will gain the confidence and expertise to navigate the intricate landscape of these powerful tools within the EKS environment. In the next chapter, we will review the Gene AI infrastructure and how to deploy it in EKS.

[Questions](#contents.xhtml#sc2_449a)

1.  What are the prerequisites for creating an EKS cluster using eksctl, and why are they important in terms of running data workloads on EKS?
2.  Explain the role of the Spark Operator in deploying and managing Spark applications on EKS.
3.  How does Kubernetes facilitate the scaling of Jupyter Notebooks and Apache Superset on EKS?
4.  What security considerations should be taken into account when running Apache Trino on EKS?
5.  Discuss the benefits of integrating Apache Spark, Jupyter Notebooks, Apache Trino, and Apache Superset with AWS services like Amazon S3.

[Exercises](#contents.xhtml#sc2_450a)

1.  Create an EKS cluster using eksctl, and deploy a sample Spark application using the Spark Operator. Monitor the Spark job's progress through the Spark UI and Kubernetes Dashboard.
2.  Set up a Jupyter Notebook environment on EKS, and connect it to a Spark cluster. Explore interactive data analysis and visualization using Jupyter Notebooks and Apache Spark.
3.  Deploy an Apache Trino cluster on EKS, and configure it to connect to a database or data lake. Execute distributed queries and explore the performance characteristics of Trino on Kubernetes.

# [CHAPTER 23Generative Artificial Intelligence on Amazon EKS](#contents.xhtml#ch23a)

[Introduction](#contents.xhtml#sc2_451a)

Venturing into generative artificial intelligence (GenAI) on Amazon Elastic Kubernetes Service (EKS) for machine learning workloads unveils a landscape rich with possibilities for AI innovation. Establishing a resilient infrastructure is paramount, and Amazon's EKS service serves as a reliable cornerstone. This combination integrates data storage, collaborative development environments, GPU-accelerated training, and real-time inference capabilities, fostering a comprehensive ecosystem for unlocking profound AI insights. This chapter serves as a guide to harnessing GenAI on Amazon EKS, guiding readers through the process of provisioning foundational elements and optimizing model performance. The aim is to provide a holistic understanding of both the potential and the practical implementation of this potent combination.

As we dive into this exploration, we will navigate through the various stages, starting from the provisioning of essential components, progressing towards the deployment of collaborative development environments, and culminating in the optimization of model performance. Readers will gain insights into how this powerful amalgamation can be effectively utilized, paving the way for groundbreaking advancements in Gen AI on Amazon EKS.

[Structure](#contents.xhtml#sc2_452a)

In this chapter, we will cover the following topics:

*   Overview
*   Setup
*   Model training
*   Model inference
*   Monitoring

[Objectives](#contents.xhtml#sc2_453a)

This chapter aims to deliver an in-depth exploration of GenAI's utilization on Amazon EKS specifically tailored for ML workloads. It breaks down the crucial components involved, spanning from the provisioning of raw materials to the intricacies of monitoring and optimization. Furthermore, it provides practical insights and step-by-step guidance, enabling readers to adeptly implement GenAI within the Amazon EKS environment.

[Overview](#contents.xhtml#sc2_454a)

Setting up a robust ML environment on Amazon EKS involves several key steps, beginning with the creation of an EKS cluster using eksctl. This is achieved by defining a comprehensive eksctl command, which includes specifications for availability zones, node groups, and instance types. By seamlessly executing the eksctl create cluster command with the configured YAML file, the EKS cluster is instantiated, laying the foundation for subsequent machine learning tasks. Following the cluster setup, the next step involves creating a node group tailored for GPU instances, a pivotal component for accelerating ML workloads. This entails using the eksctl create nodegroup command with specified parameters, such as the desired GPU instance type. To ensure optimal resource utilization, the NVIDIA Device Plugin is installed using Helm, enabling GPU access within the Kubernetes environment. Additionally, the EBS CSI driver is deployed to facilitate persistent storage for EBS volumes, crucial for storing large datasets and model checkpoints.

The deployment continues with the installation of essential components for load balancing. This includes configuring the load balancer controller, allowing for seamless traffic distribution across the cluster. The KubeRay operator, a key player in enabling distributed training and model inference, is then installed via Helm, providing operators with a simplified way to manage complex ML workflows on Kubernetes.

To facilitate collaborative model development, JupyterHub is integrated into the environment using Helm and configured with a custom values.yaml file. This allows for specifying authentication settings, resource allocations, and other parameters crucial for collaborative data science work. Following the successful deployment of JupyterHub, the platform is ready for use. The final steps of this focus on training a model and deploying an inference service. Leveraging JupyterHub's scalable GPU resources, the provided instructions guide users through training a model using Hugging Face's diffusers, a pre-trained diffusion model. The process involves executing specific commands within a Jupyter Notebook to clone the necessary repositories, install required dependencies, and launch the training process.

Concluding the deployment, the chapter details how to deploy an inference service for the trained model using the KubeRay operator. This involves deploying the NGINX Ingress Controller for exposing the inference service, configuring the RayService CRD, and ultimately exposing the service using an Ingress resource. The result is a fully operational ML environment on Amazon EKS, capable of collaborative model development, efficient model training, and scalable inference services.

[Setup](#contents.xhtml#sc2_455a)

Let us start setting up and running the Generative AI workload on EKS. After this, we will add the various modules required like adding nodegroup and the various helm components. We will start with creating the EKS cluster using eksctl as shown:

eksctl create cluster \\

 --name genai-eks \\

 --version 1.28 \\

 --nodegroup-name nodegroup-genai \\

 --node-type m5.xlarge \\

 --nodes 3 \\

 --nodes-min 3 \\

 --nodes-max 6 \\

 --region us-west-2

Upon successful cluster creation, update your local kubeconfig file using kubectl to establish seamless communication with the EKS cluster. This ensures that subsequent configurations and deployments are directed to the correct EKS environment. The following command is used to update the local Kubernetes configuration file (kubeconfig) with the details of an Amazon EKS cluster:

aws eks update-kubeconfig --name <cluster-name> --region <region>

This command ensures that your local Kubernetes client (kubectl) can communicate with the specified EKS cluster. You need to replace <cluster-name> with the name of your EKS cluster, and <region> with the AWS region where the cluster is located.

After running this command, you should be able to interact with the EKS cluster using kubectl commands without any further configuration

Creating a dedicated node group for GPU instances is a crucial step in optimizing the machine learning environment within the Amazon EKS cluster. This involves utilizing the eksctl create nodegroup command, specifying parameters such as the desired GPU instance type, minimum and maximum node capacities, and associating it with the existing EKS cluster. By tailoring a node group specifically for GPU workloads, users can harness the computational power of GPUs to accelerate model training and inference tasks. The following commands are used to create a new node group with GPU instances in an Amazon EKS cluster using eksctl, and then taint the GPU node to ensure GPU workloads are scheduled on it:

eksctl create nodegroup -n gpu-ng -t g5.12xlarge --nodes 1 --enable-ssm --managed --cluster genai-eks

NODE\_NAME=\`kubectl get nodes --show-labels |grep -i g5type | awk '{print $1}'\`

kubectl taint node $NODE\_NAME nvidia.com/gpu:NoSchedule

Facilitating GPU access within the Amazon EKS cluster involves the installation of the NVIDIA device plugin, a critical component that seamlessly integrates GPUs into the Kubernetes environment. This is achieved through the utilization of Helm, a package manager for Kubernetes, and upgrading or installing the plugin with specific version details. The commands helm repo add and helm upgrade -i are employed to incorporate the NVIDIA device plugin, ensuring compatibility with the Kubernetes cluster. The namespace and create-namespace flags aid in organizing resources and establishing a dedicated namespace, respectively. By executing these commands, the NVIDIA device plugin is effectively deployed, enabling the Kubernetes cluster to efficiently manage and allocate GPU resources for accelerated ML workloads. NVIDIA GPU Operator also can be considered, which can be a good choice for managing the lifecycle of NVIDIA GPUs in Kubernetes environments including EKS. This integration is a pivotal step in enhancing the computational capabilities of the EKS cluster, empowering users to harness the full potential of GPUs for intricate model training and inference tasks. The following snippet deploys the NVIDA device plugin:

helm repo add nvdp-helm https://nvidia.github.io/k8s-device-plugin

helm upgrade -i nvdp-helm nvdp/nvidia-device-plugin --namespace nvidia-device-plugin --create-namespace --version 0.14.1

Install the EBS CSI driver for EBS persistent volumes on an Amazon EKS cluster by executing three essential commands. First, associate the IAM OIDC provider in the specified Region and cluster. Then, create an IAM service account with the necessary policy and role for the EBS CSI driver. Finally, add the AWS EBS CSI driver addon to the cluster, ensuring seamless integration for managing EBS persistent volumes. The following set of commands is used to set up the Amazon Elastic Block Store (EBS) Container Storage Interface (CSI) driver in an Amazon EKS cluster:

eksctl utils associate-iam-oidc-provider --region us-west-2 --cluster genai-eks --approve

eksctl create iamserviceaccount --name ebs-csi-controller-sa \--namespace kube-system --cluster genai-eks --attach-policy-arn arn:aws:iam::aws:policy/service-role/AmazonEBSCSIDriverPolicy --approve --role-only --role-name AmazonEKS\_EBS\_CSI\_DriverRole

eksctl create addon --name aws-ebs-csi-driver --cluster genai-eks --service-account-role-arn arn:aws:iam::{AWS\_ACCOUNT\_ID}:role/AmazonEKS\_EBS\_CSI\_DriverRole --force

To install the Load Balancer Controller on an EKS cluster, set it up by first creating an IAM service account with the required policy and role permissions. Then, use Helm to install the controller, specifying the cluster name and referencing the previously created service account. This streamlined process ensures proper integration and configuration of the AWS Load Balancer Controller for effective load balancing on the EKS cluster. The following set of commands is used to install and configure the AWS Load Balancer Controller in an Amazon EKS cluster:

eksctl create iamserviceaccount --cluster genai-eks --namespace=kube-system --name=aws-load-balancer-controller --attach-policy-arn=arn:aws:iam::${AWS\_ACCOUNT\_ID}:policy/AWSLoadBalancerControllerIAMPolicy --approve

helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=genai-eks --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller

Let us install the KubeRay operator. For this start by adding the Helm repository and updating it for the latest information. Confirm the existence of the repository and then proceed to install both Custom Resource Definitions (CRDs) and the KubeRay operator, specifying version 1.0.0-rc.0 for accurate deployment on the Kubernetes cluster. The following sequence of commands ensures the successful setup of the Kuberay operator on the specified version:

\# Add the Helm repo

helm repo add kuberay https://ray-project.github.io/kuberay-helm/

helm repo update

\# Confirm the repo exists

helm search repo kuberay --devel

\# Install both CRDs and KubeRay operator v0.6.0.

helm install kuberay-operator kuberay/kuberay-operator --version 1.0.0-rc.0

Once deployed, verify using the kubectl get pods command.

[Model training](#contents.xhtml#sc2_456a)

JupyterHub is a versatile platform that offers a multi-user hosted notebook environment, making it particularly well-suited for model learning and AI research. The integration of JupyterHub with Kubernetes allows us to capitalize on scalable GPU resources, enabling the training of cutting-edge models efficiently. This comprehensive section is designed to lead you through the process of deploying JupyterHub on a Kubernetes cluster, along with configuring it to facilitate collaborative and distributed training scenarios. The steps include the installation of JupyterHub using Helm, the setup of authentication and user management, GPU allocation, and the initiation of training notebooks. By the end of this tutorial, you will have a fully functional JupyterHub instance tailored to meet the demands of your machine learning workflows. Embarking on this journey, you will gain insights into creating a production-ready JupyterHub environment that aligns seamlessly with your specific requirements. Let us dive into the details and kickstart the process:

1.  To initiate the installation of JupyterHub on our Kubernetes cluster, we will start by adding the official JupyterHub Helm chart repository. This repository houses the pre-packaged JupyterHub, simplifying the deployment process. The subsequent step involves updating the Helm repository to ensure access to the latest version and features. The following command adds Jupyterhub using helm:
    
    helm repo add jupyterhub https://hub.jupyter.org/helm-chart/
    
    helm repo update
    
2.  To tailor JupyterHub to our specific requirements, we will craft a values.yaml file that allows customization of various aspects, including user configuration, authentication settings, resource allocations, and more. The provided example showcases configurations for user authentication, GPU allocation, and load balancer settings. It is crucial to exercise caution and avoid deploying such configurations in production, especially when dealing with sensitive information. This file, named values.yaml, serves as a centralized hub for specifying JupyterHub behaviors, ensuring a seamless and efficient deployment on our Kubernetes cluster. For example, store the below as values.yaml. The various configuration values are as shown:
    
    hub:
    
     config:
    
     Authenticator:
    
     admin\_users:
    
     - admin1
    
     allowed\_users:
    
     - user1
    
     # testing only - do not do this for production
    
     DummyAuthenticator:
    
     password: never-do-this
    
     JupyterHub:
    
     authenticator\_class: dummy
    
    proxy:
    
     service:
    
     annotations:
    
     service.beta.kubernetes.io/aws-load-balancer-nlb-target-type: ip
    
     service.beta.kubernetes.io/aws-load-balancer-scheme: internal-facing # Private Load Balancer can only be accessed within the VPC
    
     service.beta.kubernetes.io/aws-load-balancer-type: internal
    
     service.beta.kubernetes.io/aws-load-balancer-cross-zone-load-balancing-enabled: 'true'
    
     service.beta.kubernetes.io/aws-load-balancer-ip-address-type: ipv4
    
    singleuser:
    
     image:
    
     name: public.ecr.aws/h3o5n2r0/gpu-jupyter
    
     tag: v1.5\_cuda-11.6\_ubuntu-20.04\_python-only
    
     pullPolicy: Always
    
     cmd: null
    
     startTimeout: 600
    
     memory:
    
     guarantee: 24G
    
     extraResource:
    
     limits:
    
     nvidia.com/gpu: "1"
    
     storage:
    
     capacity: 100Gi
    
     extraVolumes:
    
     - name: shm-v
    
     emptyDir:
    
     medium: Memory
    
     extraVolumeMounts:
    
     - name: shm-volume
    
     mountPath: /dev/shm
    
     extraTolerations:
    
     - key: nvidia.com/gpu
    
     operator: Exists
    
     effect: NoSchedule
    
    scheduling:
    
     userScheduler:
    
     enabled: false
    
3.  To deploy JupyterHub on our Kubernetes cluster with custom configurations, we utilize Helm by executing the following command:
    
    helm upgrade --cleanup-on-fail --install jupyterhub jupyterhub/jupyterhub --namespace jupyterhub --create-namespace --version=3.1.0 --values values.yaml
    
4.  Upon deploying JupyterHub with our specified configurations in the Kubernetes cluster, we can access the service by opening the external IP once the deployment is complete. Logging in with the admin credentials set in values.yaml allows us to launch notebooks and initiate GPU-enabled model training. In this case, we will be employing Hugging Face's Diffusers, a well-pretrained diffusion model. To access the UI exposed via the proxy, use the kubectl get svc proxy-public -n jupyterhub command to obtain the LoadBalancer URL. Paste this URL into your browser, log in with the provided credentials, and begin your AI experimentation and model training. The following figure shows the login screen for Jupyterhub:
    
    ![](images/Figure_23.1.png)
    
    Figure 23.1: Sign in screen for JupyterHub
    

Once logged in, create a Python3 (ipykernel) and run each step, as shown:

![](images/Figure_23.2.png)

Figure 23.2: JupyterHub home screen

Follow the steps in the JupyterHub Notebook from here on, as shown:

1.  Verify NVIDIA GPU is visible:
    
    !nvidia-smi
    
    import os
    
    os.chdir(“/home/user1")
    
2.  Clone the diffusers repo:
    
    !git clone https://github.com/huggingface/diffusers
    
3.  Change the directory:
    
    os.chdir(“diffusers")
    
    \# Install requirements
    
    ! pip install -e .
    
    ! pip install xformers==0.0.16 diffusers\[torch\]
    
    ! wget https://raw.githubusercontent.com/TimDettmers/bitsandbytes/main/cuda\_install.sh
    
    ! bash cuda\_install.sh 117 ~/local 1
    
4.  Install bitsandbytes for optimizations:
    
    ! pip install bitsandbytes==0.41.0
    
5.  Use the newly installed CUDA version for bitsandbytes:
    
    os.environ\["BNB\_CUDA\_VERSION"\] = "117"
    
    os.environ\["LD\_LIBRARY\_PATH"\] = os.getenv("LD\_LIBRARY\_PATH") + “:/home/user1/local/cuda-11.7"
    
6.  Validate successful installation of bitsandbytes:
    
    ! python -m bitsandbytes
    
7.  Install requirements for dreambooth:
    
    os.chdir("examples/dreambooth")
    
    ! pip install -r requirements.txt
    
8.  Setup default configuration for accelerate:
    
    ! accelerate config default
    
9.  Login to huggingface associated with your account (please create one if it does not exist):
    
    ! huggingface-cli login --token $HUGGING\_FACE\_HUB\_TOKEN
    
10.  Download sample dataset of the subject:
     
     from huggingface\_hub import snapshot\_download
     
     local\_dir = "./dog"
     
     snapshot\_download(
     
      "diffusers/dog-example",
     
      local\_dir=local\_dir, repo\_type="dataset",
     
      ignore\_patterns=".gitattributes",
     
     )
     
11.  Export environment variables:
     
     os.environ\[“MODEL\_NAME”\] = “stabilityai/stable-diffusion-2-1”
     
     os.environ\["INSTANCE\_DIR"\] = "dog"
     
     os.environ\["OUTPUT\_DIR"\] = "dogbooth"
     
     os.environ\["RESOLUTION"\] = "768"
     
     os.environ\["PYTORCH\_CUDA\_ALLOC\_CONF"\] = "garbage\_collection\_threshold:0.6,max\_split\_size\_mb:128"
     
     \# Launch the training and push the output model to huggingface
     
     ! accelerate launch train\_dreambooth.py \\
     
      --pretrained\_model\_name\_or\_path=$MODEL\_NAME \\
     
      --instance\_data\_dir=$INSTANCE\_DIR \\
     
      \--output\_dir=$OUTPUT\_DIR \\
     
      --instance\_prompt="a photo of \[v\]dog" \\
     
      --resolution=768 \\
     
      --train\_batch\_size=1 \\
     
      --gradient\_accumulation\_steps=1 \\
     
      --gradient\_checkpointing \\
     
      --learning\_rate=1e-6 \\
     
      --lr\_scheduler="constant" \\
     
      --enable\_xformers\_memory\_efficient\_attention \\
     
      --use\_8bit\_adam \\
     
      --lr\_warmup\_steps=0 \\
     
      --max\_train\_steps=800 \\
     
      --push\_to\_hub
     

The entire process, including model training and subsequent upload to Hugging Face, is expected to take around 90 minutes. Following the completion of this duration, we can move on to the inference stage, where a sample inference will be executed to assess the model's performance.

[Model inference](#contents.xhtml#sc2_457a)

In this section, we will guide you through the process of establishing an inference service for Dogbooth utilizing the Kuberay operator. This step-by-step explanation will provide insights into deploying and configuring the RayService for optimal performance in the context of Dogbooth:

1.  To facilitate the creation of a Network Load Balancer for the Inference service, we will deploy the NGINX Ingress Controller. This involves adding the NGINX Ingress Helm chart repository and updating the Helm repositories accordingly. The NGINX Ingress Controller serves as a crucial component in managing external access to the deployed services within the Kubernetes cluster. The following helm command adds ingress-nginx:
    
    helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
    
    helm repo update
    
2.  We will use the ingress-values.yaml file for deploying the ingress controller. Here we are making the annotations to make sure the endpoint is accessible from a load balancer. Refer to the following code snippet:
    
    controller:
    
     service:
    
     externalTrafficPolicy: "Local"
    
     annotations:
    
     service.beta.kubernetes.io/aws-load-balancer-type: external
    
     service.beta.kubernetes.io/aws-load-balancer-nlb-target-type: ip
    
     service.beta.kubernetes.io/aws-load-balancer-backend-protocol: http
    
     service.beta.kubernetes.io/aws-load-balancer-scheme: internet-facing
    
     targetPorts:
    
     http: http
    
     https: http
    
    Deploy using helm as shown:
    
    helm install nginx-ingress ingress-nginx/ingress-nginx -f ingress-values.yaml --set controller.admissionWebhooks.enabled=false
    
3.  The provided ray-service.yaml is a configuration file for creating the Dogbooth inference service using the Kuberay operator. It defines Kubernetes resources, such as a namespace and a RayService custom resource within that namespace. The ray-service.yaml specifies service and deployment parameters, including the import path, runtime environment, and Ray cluster configuration. The runtime environment sets environment variables, such as the model ID for Dogbooth. The Ray cluster configuration details the version, head node specifications, and worker group specifications, defining the resources and replicas for GPU-enabled containers responsible for serving the model and handling inference requests. This comprehensive configuration file ensures the proper setup and orchestration of the inference service within the Kubernetes environment. The following snippet deploys the ray service:
    
    apiVersion: v1
    
    kind: Namespace
    
    metadata:
    
     name: ns1
    
    \---
    
    apiVersion: ray.io/v1alpha1
    
    kind: RayService
    
    metadata:
    
     name: ns1
    
     namespace: ns1
    
    spec:
    
     serviceUnhealthySecondThreshold: 600
    
     deploymentUnhealthySecondThreshold: 600
    
     serveConfig:
    
     importPath: dogbooth:entrypoint
    
     runtimeEnv: |
    
     env\_vars: {"MODEL\_ID": "sguruvar/dogbooth"}
    
     rayClusterConfig:
    
     rayVersion: '2.6.0'
    
     headGroupSpec:
    
     rayStartParams:
    
     dashboard-host: '0.0.0.0'
    
     template:
    
     spec:
    
     containers:
    
     - name: ray-head
    
     image: public.ecr.aws/h5u5m2y7/dogbooth:0.0.1-gpu
    
     resources:
    
     limits:
    
     cpu: 2
    
     memory: 16Gi
    
     nvidia.com/gpu: 1
    
     requests:
    
     cpu: 2
    
     memory: 16Gi
    
     nvidia.com/gpu: 1
    
     ports:
    
     - containerPort: 6379
    
     name: gcs-server
    
     - containerPort: 8265
    
     name: dashboard
    
     - containerPort: 10001
    
     name: client
    
     - containerPort: 8000
    
     name: serve
    
     workerGroupSpecs:
    
     - replicas: 1
    
     minReplicas: 1
    
     maxReplicas: 5
    
     rayStartParams: {}
    
     groupName: small-group
    
     template:
    
     spec:
    
     containers:
    
     - name: ray-worker
    
     image: public.ecr.aws/h3o5n2r0/dogbooth:0.0.1-gpu
    
     lifecycle:
    
     preStop:
    
     exec:
    
     command: \["/bin/sh","-c","ray stop"\]
    
     resources:
    
     limits:
    
     cpu: "2"
    
     memory: "16Gi"
    
     nvidia.com/gpu: 1
    
     requests:
    
     cpu: “2”
    
     memory: “16Gi”
    
     nvidia.com/gpu: 1
    
4.  The above yaml will create a namespace and a rayservice with the model we trained in the previous section. Let us download the file and run the following commands:
    
    kubectl apply -f ray-svc.yaml
    
5.  To make the Dogbooth service accessible, we will expose it through a Network Load Balancer (NLB) by configuring the ray-ingress.yaml file. This YAML file contains the necessary ingress configuration for provisioning an NLB. It is crucial to replace <DOGBOOTH SVC NAME> with the actual name of the Dogbooth head service. The Ingress rules specify paths for accessing the Ray Dashboard and Ray Serve, mapping them to the appropriate backend services and ports. Once applied, this Ingress configuration will enable external access to the Dogbooth service, allowing users to interact with the Ray Dashboard and initiate inference requests through Ray Serve using the specified NLB. The following snippet deploys the ingress endpoint for the ray service:
    
    apiVersion: networking.k8s.io/v1
    
    kind: Ingress
    
    metadata:
    
     name: ns1
    
     namespace: ns1
    
     annotations:
    
     nginx.ingress.kubernetes.io/rewrite-target: "/$1"
    
    spec:
    
     ingressClassName: nginx
    
     rules:
    
     - http:
    
     paths:
    
     # Ray Dashboard
    
     - path: /(.\*)
    
     pathType: ImplementationSpecific
    
     backend:
    
     service:
    
     name: <DOGBOOTH SVC NAME>
    
     port:
    
     number: 8265
    
     # Ray Serve
    
     - path: /dogbooth/serve/(.\*)
    
     pathType: ImplementationSpecific
    
     backend:
    
     service:
    
     name: <DOGBOOTH SVC NAME>
    
     port:
    
     number: 8000
    
    Let us go ahead and deploy the ingress file with the following command:
    
    kubectl apply -f ray-ingress.yaml
    
6.  Now, let us proceed with a sample inference. Copy the NLB endpoint and paste it into your browser. To obtain the NLB Endpoint, execute the command kubectl get svc -n jupyterhub. For instance, the output may resemble the following. After obtaining the NLB Endpoint, run a sample prompt, such as creating a drawing of dogs playing by the water's side, as shown:
    
    http://NLBENDPOINT//dogbooth/serve/imagine?prompt=a drawing of 2 dogs playing beach side
    
    This should generate an image like the following:
    
    ![](images/Figure_23.3.png)
    
    Figure 23.3: GenAI generated image
    

[Monitoring](#contents.xhtml#sc2_458a)

Monitoring GPUs is essential for teams tasked with managing large-scale GPU clusters dedicated to AI or HPC workloads. The insights derived from GPU metrics play a crucial role in comprehending workload behavior, enabling teams enhance overall data center efficiency. To facilitate GPU monitoring, we will deploy the DCGM exporter, a tool built on the Go APIs to NVIDIA DCGM. This exporter allows users to collect GPU metrics, gaining valuable insights into workload behavior and facilitating efficient GPU cluster monitoring. The DCGM exporter, crafted in Go, exposes GPU metrics through an HTTP endpoint (metrics), making it compatible with monitoring solutions like Prometheus.

Moreover, we will deploy the ADOT collector to scrape metrics from the DCGM exporter and seamlessly ingest them into Prometheus. This integration streamlines the process of gathering and managing GPU metrics, enhancing the overall monitoring capabilities of large-scale GPU clusters. Additionally, we will leverage Amazon Managed Grafana for visualizing the collected GPU metrics, providing a comprehensive and user-friendly interface to monitor and analyze GPU-related data efficiently. Prior to deploying the DCGM exporter, it is essential to set up the ServiceMonitor custom resource definition (CRD), which serves as a prerequisite. This can be achieved by applying the ServiceMonitor CRD using the provided YAML file through the following command:

kubectl apply -f https://raw.githubusercontent.com/helm/charts/master/stable/prometheus-operator/crds/crd-servicemonitor.yaml

Subsequently, the GPU monitoring tools Helm charts repository is added and updated. Following this, the DCGM exporter is deployed using Helm with the following command:

helm repo add gpu-helm-charts https://nvidia.github.io/gpu-monitoring-tools/helm-charts

helm repo update

helm install --generate-name gpu-helm-charts/dcgm-exporter

This sequence of commands ensures that the necessary ServiceMonitor CRD is in place before initiating the deployment of the DCGM exporter, laying the groundwork for effective GPU monitoring in the Kubernetes cluster. Before proceeding with the ingestion setup steps outlined below, it is imperative to establish the IAM role for the service account along with the corresponding trust policy. This role, once created, will be utilized by the ADOT Collector for scraping and exporting metrics.

Following the creation of the IAM role, the trust policy associated with the role needs to be modified. This can be accomplished by accessing the IAM console at [https://console.aws.amazon.com/iam/](https://console.aws.amazon.com/iam/). Navigate to the Roles section in the left navigation pane and locate the amp-iamproxy-ingest-role, previously created. Then proceed to edit the trust relationship. In the JSON representation of the trust policy, replace aws-amp with adot-col and subsequently update the Trust Policy. This adjustment ensures that the trust policy aligns with the requirements for the ADOT Collector's metric-scraping operations. The following snippet shows the trust policy json:

{

 "Version": "2012-10-17",

 "Statement": \[

 {

 "Effect": "Allow",

 "Principal": {

 "Federated": "arn:aws:iam::account-id:oidc-provider/oidc.eks.region.amazonaws.com/id/openid"

 },

 "Action": "sts:AssumeRoleWithWebIdentity",

 "Condition": {

 "StringEquals": {

 "oidc.eks.region.amazonaws.com/id/openid:sub": "system:serviceaccount:adot-col:amp-iamproxy-ingest-service-account"

 }

 }

 }

 \]

}

Choose the Permissions tab and make sure that the following permissions policy is attached to the role, as shown:

{

 "Version": "2012-10-17",

 "Statement": \[

 {

 "Effect": "Allow",

 "Action": \[

 "aps:RemoteWrite",

 "aps:GetSeries",

 "aps:GetLabels",

 "aps:GetMetricMetadata"

 \],

 "Resource": "\*"

 }

 \]

}

We will use Prometheus workspace to ingest the GPU metrics collected by ADOT collector. The following command creates a Prometheus workspace in the us-west-2 region:

aws amp create-workspace --alias genai-workspace --region us-west-2  
WORKSPACE=$(aws amp list-workspaces | jq -r '.workspaces\[\] | select(.alias==“genai-workspace").workspaceId')

REMOTE\_WRITE\_URL=“https://aps-workspaces.us-west-2.amazonaws.com/workspaces/$WORKSPACE/api/v1/remote\_write"

Let us now deploy the ADOT collector with the following code snippet, starting with namespace and configmap:

apiVersion: v1

kind: Namespace

metadata:

 name: adot

 labels:

 name: adot

\---

apiVersion: v1

kind: ConfigMap

metadata:

 name: adot-collector-conf

 namespace: adot

 labels:

 app: aws-adot

 component: adot-collector-conf

data:

 adot-collector-config: |

 receivers:

 prometheus:

 config:

 global:

 scrape\_interval: 15s

 scrape\_timeout: 10s

 scrape\_configs:

 \- job\_name: gpu-metrics

 scrape\_interval: 1s

 metrics\_path: /metrics

 scheme: http

 kubernetes\_sd\_configs:

 - role: endpoints

 namespaces:

 names:

 - default

 relabel\_configs:

 - source\_labels: \[\_\_meta\_kubernetes\_pod\_node\_name\]

 action: replace

 target\_label: kubernetes\_node

 - job\_name: 'kubernetes-service-endpoints'

 kubernetes\_sd\_configs:

 - role: endpoints

 tls\_config:

 ca\_file: /var/run/secrets/kubernetes.io/serviceaccount/ca.crt

 insecure\_skip\_verify: true

 bearer\_token\_file: /var/run/secrets/kubernetes.io/serviceaccount/token

 relabel\_configs:

 - source\_labels: \[\_\_meta\_kubernetes\_service\_annotation\_scrape\]

 action: keep

 regex: true

 exporters:

 prometheusremotewrite:

 # replace this with your endpoint

 endpoint: $REMOTE\_WRITE\_URL

 auth:

 authenticator: sigv4auth

 logging:

 loglevel: debug

 extensions:

 health\_check:

 pprof:

 endpoint: :1888

 zpages:

 endpoint: :55679

 # replace this with your region

 sigv4auth:

 region: us-west-2

 service:

 extensions: \[pprof, zpages, health\_check, sigv4auth\]

 pipelines:

 metrics:

 receivers: \[prometheus\]

 exporters: \[logging, prometheusremotewrite\]

\---

Then let us create the snippets for the service account and role based access control using cluster role and cluster role binding:

apiVersion: v1

kind: ServiceAccount

metadata:

 name: amp-iamproxy-ingest-service-account

 namespace: adot

 annotations:

 eks.amazonaws.com/role-arn: arn:aws:iam::$ACCOUNT\_ID:role/amp-iamproxy-ingest-role-genai

\---

kind: ClusterRole

apiVersion: rbac.authorization.k8s.io/v1

metadata:

 name: adotcol-admin-role

rules:

 - apiGroups: \[""\]

 resources:

 - nodes

 - nodes/proxy

 - services

 - endpoints

 - pods

 verbs: \["get", "list", "watch"\]

 - apiGroups:

 - extensions

 resources:

 - ingresses

 verbs: \["get", "list", "watch"\]

 - nonResourceURLs: \["/metrics"\]

 verbs: \["get"\]

\---

kind: ClusterRoleBinding

apiVersion: rbac.authorization.k8s.io/v1

metadata:

 name: adotcol-admin-role-binding

subjects:

 - kind: ServiceAccount

 name: amp-iamproxy-ingest-service-account

 namespace: adot

roleRef:

 kind: ClusterRole

 name: adotcol-admin-role

 apiGroup: rbac.authorization.k8s.io

\---

Let us look at the following snippet to have the services for adot collector configuration and the daemonsets:

apiVersion: v1

kind: Service

metadata:

 name: adot-collector

 namespace: adot

 labels:

 app: aws-adot

 component: adot-collector

spec:

 ports:

 - name: metrics

 port: 8888

 selector:

 component: adot-collector

 type: NodePort

\---

apiVersion: apps/v1

kind: DaemonSet

metadata:

 name: adot-collector

 namespace: adot

 labels:

 app: aws-adot

 component: adot-collector

spec:

 selector:

 matchLabels:

 app: aws-adot

 component: adot-collector

 minReadySeconds: 5

 template:

 metadata:

 labels:

 app: aws-adot

 component: adot-collector

 spec:

 serviceAccountName: amp-iamproxy-ingest-service-account

 containers:

 - command:

 - "/awscollector"

 - "--config=/conf/adot-collector-config.yaml"

 image: public.ecr.aws/aws-observability/aws-otel-collector:latest

 name: adot-collector

 resources:

 limits:

 cpu: 1

 memory: 2Gi

 requests:

 cpu: 200m

 memory: 400Mi

 ports:

 - containerPort: 8888 

 volumeMounts:

 - name: adot-collector-config-vol

 mountPath: /conf

 livenessProbe:

 httpGet:

 path: /

 port: 13133

 readinessProbe:

 httpGet:

 path: /

 port: 13133 

 volumes:

 - configMap:

 name: adot-collector-conf

 items:

 - key: adot-collector-config

 path: adot-collector-config.yaml

 name: adot-collector-config-vol

Let us deploy the file created above with the following command:

kubectl apply -f adot-daemonset.yaml

To visualize GPU metrics seamlessly, you can configure Amazon Managed Grafana. Subsequently, integrate the Prometheus workspace as a datasource. Once these configurations are in place, initiate a Grafana dashboard for GPU metrics by importing the reference NVIDIA dashboard (ID: 12239). This streamlined process allows you to harness the full potential of Amazon Managed Grafana for insightful visualization and monitoring of GPU-related metrics. The following figure shows the snippet of this Grafana dashboard:

![](images/Figure_23.4.png)

Figure 23.4: Sample Grafana dashboard after applying the changes

[Conclusion](#contents.xhtml#sc2_459a)

In conclusion, we have successfully set up a ML platform on Amazon EKS. We began by creating a stable EKS cluster, configured GPU capabilities, storage, and load balancing. JupyterHub was deployed for collaborative data science, and we scaled up distributed training jobs. To keep an eye on the cluster, we added GPU metrics collection using the DCGM exporter, visualizing performance with Grafana, and enabling cluster autoscaling based on usage.

With the core infrastructure in place, there are various paths the ML platform can take. Options include integrating with SageMaker components, deploying models with SageMaker hosting, and incorporating MLops features such as A/B testing. We can also broaden the workload types, explore Spark or PyTorch jobs, and enhance security measures. This workshop lays a solid foundation for building an enterprise-grade ML platform on EKS, providing flexibility for further advancements. The amalgamation of GenAI and Amazon EKS forms a robust and dynamic environment, poised to propel AI innovation and extract valuable insights.

This chapter has meticulously covered the entire spectrum, starting from the foundational steps of data storage to the integration of cutting-edge technologies such as GPU-powered training and real-time inference. The synergy between GenAI and Amazon EKS not only addresses the multifaceted needs of AI workloads but also lays the groundwork for a resilient and efficient AI ecosystem.

[Questions](#contents.xhtml#sc2_460a)

1.  What is the role of EBS volumes in the machine learning infrastructure on Amazon EKS?
    
2.  How does JupyterHub contribute to collaborative model development within an EKS environment?
    
3.  What is the significance of NVIDIA GPUs integrated with EKS in accelerating model training?
    
4.  How does Apache Ray's distributed computing framework facilitate real-time inferences on EKS?
    
5.  In what ways does GenAI provide visibility into ML workloads on Amazon EKS?
    

[Exercises](#contents.xhtml#sc2_461a)

1.  Create an EKS cluster and provision an EBS volume for data storage.
    
2.  Set up JupyterHub within the EKS cluster and develop a simple ML model collaboratively.
    
3.  Explore GPU-powered training by integrating NVIDIA GPUs with your EKS cluster and observe the impact on training time.
    

Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# Index

A

Amazon EBS, steps [200](#ch14.xhtml#page200), [201](#ch14.xhtml#page201)

Amazon EKS [50](#ch04.xhtml#page50), [51](#ch04.xhtml#page51)

Amazon EKS Application, optimizing [61](#ch04.xhtml#page61)

Amazon EKS Cluster [90](#ch07.xhtml#page90)

Amazon EKS Cluster, administration [60](#ch04.xhtml#page60), [61](#ch04.xhtml#page61)

Amazon EKS Cluster, aspects

AWS CDK [98](#ch07.xhtml#page98)\-[100](#ch07.xhtml#page100)

AWS Console [91](#ch07.xhtml#page91)\-[95](#ch07.xhtml#page95)

eksctl [96](#ch07.xhtml#page96)\-[98](#ch07.xhtml#page98)

Pulumi [103](#ch07.xhtml#page103), [104](#ch07.xhtml#page104)

Terraform [100](#ch07.xhtml#page100)\-[103](#ch07.xhtml#page103)

Amazon EKS, key benefits

control plane [58](#ch04.xhtml#page58)

cost, optimizing [54](#ch04.xhtml#page54)

ease, use [56](#ch04.xhtml#page56), [57](#ch04.xhtml#page57)

flexibility [53](#ch04.xhtml#page53), [54](#ch04.xhtml#page54)

high availability [51](#ch04.xhtml#page51)

infrastructure, managing [51](#ch04.xhtml#page51), [52](#ch04.xhtml#page52)

Kubernetes, innovation [52](#ch04.xhtml#page52), [53](#ch04.xhtml#page53)

Observability [55](#ch04.xhtml#page55), [56](#ch04.xhtml#page56)

security, compliance [57](#ch04.xhtml#page57), [58](#ch04.xhtml#page58)

worker, nodes [59](#ch04.xhtml#page59)

Amazon EKS, log types

API Server [239](#ch16.xhtml#page239)

audit [239](#ch16.xhtml#page239)

authenticator [239](#ch16.xhtml#page239)

controller manager [239](#ch16.xhtml#page239)

scheduler [239](#ch16.xhtml#page239)

Amazon EKS, security

audit, logging [77](#ch05.xhtml#page77)

IAM Roles, policies [76](#ch05.xhtml#page76)

Pod Security, policies [76](#ch05.xhtml#page76)

transport layer [77](#ch05.xhtml#page77)

VPC Network Policies [76](#ch05.xhtml#page76)

Amazon Elastic Block Store (EBS) [199](#ch14.xhtml#page199), [200](#ch14.xhtml#page200)

Amazon FSx Lustre [210](#ch14.xhtml#page210), [211](#ch14.xhtml#page211)

Amazon FSx/NetApp ONTAP [206](#ch14.xhtml#page206)

Amazon GuardDuty [190](#ch13.xhtml#page190), [191](#ch13.xhtml#page191)

Amazon S3 [73](#ch05.xhtml#page73)

Amazon VPC Lattice [179](#ch12.xhtml#page179)\-[181](#ch12.xhtml#page181)

Apache Spark [350](#ch22.xhtml#page350)\-[353](#ch22.xhtml#page353)

Apache Superset [362](#ch22.xhtml#page362)\-[365](#ch22.xhtml#page365)

Apache Trino [358](#ch22.xhtml#page358)\-[361](#ch22.xhtml#page361)

Application Load Balancers (ALB) [71](#ch05.xhtml#page71)

AWS EKS, monitoring [217](#ch15.xhtml#page217)\-[224](#ch15.xhtml#page224)

AWS Lambda [254](#ch17.xhtml#page254)

AWS Lambda, key points

EKS Cluster, setting up [255](#ch17.xhtml#page255)

functions, deploying [255](#ch17.xhtml#page255)

integration points [255](#ch17.xhtml#page255)

AWS Lambda, world scenarios [256](#ch17.xhtml#page256)

AWS, monitoring [217](#ch15.xhtml#page217)

AWS, services

CI/CD Pipelines, deploying [78](#ch05.xhtml#page78)

CloudWatch, insights [78](#ch05.xhtml#page78)

control tower, config [79](#ch05.xhtml#page79)

secrets, manager [79](#ch05.xhtml#page79)

AWS X-Ray, steps [285](#ch18.xhtml#page285)

B

Backup/Disaster Recovery, fundamentals

application data, comprehensing [315](#ch20.xhtml#page315)

AWS Fault Injection Simulator [316](#ch20.xhtml#page316)\-[319](#ch20.xhtml#page319)

cluster, backup [316](#ch20.xhtml#page316)

DR Strategies, validating [320](#ch20.xhtml#page320)

EKS, backup [314](#ch20.xhtml#page314)

operation, monitoring [320](#ch20.xhtml#page320), [321](#ch20.xhtml#page321)

regions, infrastructure [319](#ch20.xhtml#page319)

C

chroot command [3](#ch01.xhtml#page3), [4](#ch01.xhtml#page4)

CI/CD [277](#ch18.xhtml#page277)

CI/CD Deploy, techniques

Blue/Green Deploy [282](#ch18.xhtml#page282)

Canary Deploy [283](#ch18.xhtml#page283)

CI/CD Source Code, managing [278](#ch18.xhtml#page278), [279](#ch18.xhtml#page279)

Classic Load Balancers (CLBs) [72](#ch05.xhtml#page72)

Cloud Development Kit (CDK) [98](#ch07.xhtml#page98), [99](#ch07.xhtml#page99)

Cloud Native Landscape [8](#ch01.xhtml#page8), [9](#ch01.xhtml#page9)

CloudWatch Integration [264](#ch17.xhtml#page264)

CloudWatch Integration, key points

agent, installing [265](#ch17.xhtml#page265)

EKS, setting up [265](#ch17.xhtml#page265)

metrics alarms, optimzing [266](#ch17.xhtml#page266)

metrics, scaling [267](#ch17.xhtml#page267)

proactive, managing [267](#ch17.xhtml#page267)

CloudWatch Integration, use cases [266](#ch17.xhtml#page266)

CloudWatch Log Insights [242](#ch16.xhtml#page242)\-[244](#ch16.xhtml#page244)

Cluster Autoscaler [342](#ch21.xhtml#page342)

Cluster Autoscaler (CA) [74](#ch05.xhtml#page74), [162](#ch11.xhtml#page162), [163](#ch11.xhtml#page163)

CNCF [8](#ch01.xhtml#page8)

Container Insights [225](#ch15.xhtml#page225)\-[229](#ch15.xhtml#page229)

container orchestration [6](#ch01.xhtml#page6), [7](#ch01.xhtml#page7)

Cost Optimization [324](#ch21.xhtml#page324)\-[326](#ch21.xhtml#page326)

D

Docker [5](#ch01.xhtml#page5)

docker build [5](#ch01.xhtml#page5)

Docker, history [6](#ch01.xhtml#page6)

docker push [5](#ch01.xhtml#page5)

docker run [5](#ch01.xhtml#page5)

DynamoDB Accelerator (DAX) [271](#ch17.xhtml#page271)

DynamoDB Integration [268](#ch17.xhtml#page268)

DynamoDB Integration, benefits [268](#ch17.xhtml#page268)

DynamoDB Integration, deploying [269](#ch17.xhtml#page269)

DynamoDB Integration, setting up [268](#ch17.xhtml#page268), [269](#ch17.xhtml#page269)

DynamoDB Integration, use cases [270](#ch17.xhtml#page270), [271](#ch17.xhtml#page271)

E

EBS Container Storage Interface (CSI) [202](#ch14.xhtml#page202), [203](#ch14.xhtml#page203)

ECS, key options

benchmarks, performance [263](#ch17.xhtml#page263)

EKS, configuring [261](#ch17.xhtml#page261)

ECS, practices [263](#ch17.xhtml#page263)

EFS Container Storage Interface (CSI) [204](#ch14.xhtml#page204), [205](#ch14.xhtml#page205)

EKS AutoScaler, types

Cluster Autoscaler (CA) [74](#ch05.xhtml#page74)

Horizontal Pod Autoscaler (HPA) [75](#ch05.xhtml#page75)

Vertical Pod Autoscaler (VPA) [74](#ch05.xhtml#page74)

EKS Cluster, components

cluster plane, controlling [68](#ch05.xhtml#page68)

Kubernetes Plane, controlling [67](#ch05.xhtml#page67), [68](#ch05.xhtml#page68)

worker nodes [68](#ch05.xhtml#page68)

EKS Cluster, key aspects

backup, restore [69](#ch05.xhtml#page69)

elastic scaling [69](#ch05.xhtml#page69)

high availability [69](#ch05.xhtml#page69)

observability [69](#ch05.xhtml#page69)

pod, networking [69](#ch05.xhtml#page69)

security, hardening [69](#ch05.xhtml#page69)

serverless, operation [69](#ch05.xhtml#page69)

version, upgrading [69](#ch05.xhtml#page69)

EKS Deployment, patterns

burstable cluster [80](#ch05.xhtml#page80)

ML, serving [80](#ch05.xhtml#page80)

production cluster [80](#ch05.xhtml#page80)

EKS, factors

access, pattern [212](#ch14.xhtml#page212)

administration, configuring [212](#ch14.xhtml#page212)

application, architectures [213](#ch14.xhtml#page213)

cost, budgets [212](#ch14.xhtml#page212)

curves, learning [212](#ch14.xhtml#page212)

performance, considering [211](#ch14.xhtml#page211)

resiliency [212](#ch14.xhtml#page212)

scalability [211](#ch14.xhtml#page211)

EKS OS, tools

Linux [85](#ch06.xhtml#page85)

macOS [85](#ch06.xhtml#page85)

Windows [84](#ch06.xhtml#page84)

EKS Pod, identifying [194](#ch13.xhtml#page194), [195](#ch13.xhtml#page195)

EKS, setting up

billing integration [87](#ch06.xhtml#page87)

CNI Plugin, access [86](#ch06.xhtml#page86)

IAM Role, optimizing [85](#ch06.xhtml#page85)

internet gateway, setup [86](#ch06.xhtml#page86)

node security, rules [86](#ch06.xhtml#page86)

VPC, networking [85](#ch06.xhtml#page85)

EKS, storage

EBS Volumes [72](#ch05.xhtml#page72)

Elastic File System (EFS) [73](#ch05.xhtml#page73)

S3 Buckets [73](#ch05.xhtml#page73)

EKS, troubleshoot

authentication/authorization [249](#ch16.xhtml#page249)

cluster logs, events [248](#ch16.xhtml#page248)

control plane logs [250](#ch16.xhtml#page250)

network, issues [247](#ch16.xhtml#page247), [248](#ch16.xhtml#page248)

Node/Pod Status, checking [246](#ch16.xhtml#page246)

EKS Worker, nodes

EC2 [70](#ch05.xhtml#page70)

Fargate [69](#ch05.xhtml#page69), [70](#ch05.xhtml#page70)

Elastic Block Store (EBS) [72](#ch05.xhtml#page72)

Elastic Container Service (ECS) [261](#ch17.xhtml#page261)

Elastic File System (EFS) [73](#ch05.xhtml#page73), [203](#ch14.xhtml#page203), [204](#ch14.xhtml#page204)

Elastic Load Balancing (ELB) [71](#ch05.xhtml#page71)

ELB, types

Application Load Balancer (ALB) [71](#ch05.xhtml#page71)

Classic Load Balancer (CLBs) [72](#ch05.xhtml#page72)

Network Load Balancers (NLB) [71](#ch05.xhtml#page71)

F

FSxN CSI [206](#ch14.xhtml#page206)\-[208](#ch14.xhtml#page208)

G

GitOps [296](#ch19.xhtml#page296)

GitOps, aspects [297](#ch19.xhtml#page297)

GitOps, best practices [308](#ch19.xhtml#page308), [309](#ch19.xhtml#page309)

GitOps, foundations [297](#ch19.xhtml#page297)

GitOps Framework, tools [298](#ch19.xhtml#page298), [299](#ch19.xhtml#page299)

GitOps Implement, monitoring [308](#ch19.xhtml#page308)

GitOps Observability, implementing [307](#ch19.xhtml#page307)

GitOps Tooling [299](#ch19.xhtml#page299)

GitOps, tools

Argo CD [299](#ch19.xhtml#page299)

Flux [300](#ch19.xhtml#page300)

GPUs, monitoring [381](#ch23.xhtml#page381)\-[388](#ch23.xhtml#page388)

H

Helm [132](#ch09.xhtml#page132), [133](#ch09.xhtml#page133)

Hierarchical Namespace Controller (HNC) [345](#ch21.xhtml#page345)

Horizontal Pod Autoscaler (HPA) [75](#ch05.xhtml#page75), [159](#ch11.xhtml#page159), [160](#ch11.xhtml#page160)

I

IAM, best practices

Hierarchical Namespace Controller (HNC) [345](#ch21.xhtml#page345)

Mutual TLS [346](#ch21.xhtml#page346)

policy, agent [346](#ch21.xhtml#page346)

role-based access, controlling [343](#ch21.xhtml#page343)

service accounts [343](#ch21.xhtml#page343), [344](#ch21.xhtml#page344)

IAM, roles [287](#ch18.xhtml#page287)

IAM Roles Service Accounts (IRSA) [188](#ch13.xhtml#page188), [189](#ch13.xhtml#page189)

IAM With EKS, integrating [288](#ch18.xhtml#page288)

Identity Access Management (IAM) [287](#ch18.xhtml#page287)

IDP, aspects

Crossplane [303](#ch19.xhtml#page303)

Kubevela [303](#ch19.xhtml#page303)

IDP, concepts

cloud-agnostic, provisioning [304](#ch19.xhtml#page304)

collaboration, enhancing [304](#ch19.xhtml#page304)

infrastructure abstraction [304](#ch19.xhtml#page304)

IDP, impact [305](#ch19.xhtml#page305), [306](#ch19.xhtml#page306)

Ingress Controllers [172](#ch12.xhtml#page172)

Internal Developer Platform (IDP) [302](#ch19.xhtml#page302)

J

JupyterHub [371](#ch23.xhtml#page371)

JupyterHub Model, training [372](#ch23.xhtml#page372)\-[374](#ch23.xhtml#page374)

JupyterHub, steps [375](#ch23.xhtml#page375), [376](#ch23.xhtml#page376)

Jupyter Notebooks [354](#ch22.xhtml#page354)\-[357](#ch22.xhtml#page357)

K

Karpenter [163](#ch11.xhtml#page163), [164](#ch11.xhtml#page164), [340](#ch21.xhtml#page340)

Kubecost [230](#ch15.xhtml#page230)\-[234](#ch15.xhtml#page234)

Kubernetes [4](#ch01.xhtml#page4)

Kubernetes Architecture, components

Namespaces [18](#ch02.xhtml#page18)

Pod [18](#ch02.xhtml#page18)

Service [18](#ch02.xhtml#page18)

Volumes [18](#ch02.xhtml#page18)

Kubernetes Architecture, fundamental

blocks, building [17](#ch02.xhtml#page17)

DaemonSets [23](#ch02.xhtml#page23), [24](#ch02.xhtml#page24)

labels, selectors [19](#ch02.xhtml#page19)

monitoring [27](#ch02.xhtml#page27)

Monolith, microservices [24](#ch02.xhtml#page24), [25](#ch02.xhtml#page25)

reconciliation loop [26](#ch02.xhtml#page26)

reconciliation, model [21](#ch02.xhtml#page21), [22](#ch02.xhtml#page22)

security [27](#ch02.xhtml#page27), [28](#ch02.xhtml#page28)

storage [25](#ch02.xhtml#page25)

under, hood [22](#ch02.xhtml#page22)

Kubernetes, capibilities

GitOps Workflow, automation [11](#ch01.xhtml#page11)

meshes, services [11](#ch01.xhtml#page11)

multi-cluster, federation [11](#ch01.xhtml#page11)

node clusters, scalability [11](#ch01.xhtml#page11)

stateful application, maturity [11](#ch01.xhtml#page11)

window, supporting [11](#ch01.xhtml#page11)

Kubernetes, components

Addons [39](#ch03.xhtml#page39)\-[41](#ch03.xhtml#page41)

cluster-level, logging [42](#ch03.xhtml#page42)

cluster storage [44](#ch03.xhtml#page44)

container resource, monitoring [41](#ch03.xhtml#page41), [42](#ch03.xhtml#page42)

etcd [33](#ch03.xhtml#page33), [34](#ch03.xhtml#page34)

extension mechanisms [45](#ch03.xhtml#page45)

kube-apiserver [32](#ch03.xhtml#page32), [33](#ch03.xhtml#page33)

kube-controller-manager [35](#ch03.xhtml#page35), [36](#ch03.xhtml#page36)

kubelet [36](#ch03.xhtml#page36)\-[38](#ch03.xhtml#page38)

kube-proxy [38](#ch03.xhtml#page38), [39](#ch03.xhtml#page39)

kube-scheduler [34](#ch03.xhtml#page34), [35](#ch03.xhtml#page35)

Kubernetes, concepts

event-driven container, scaling [12](#ch01.xhtml#page12)

GitOps, adoption [13](#ch01.xhtml#page13)

IoT Infrastructure, integrating [12](#ch01.xhtml#page12)

ML Data, frameworks [13](#ch01.xhtml#page13)

multi-cloud, deployments [13](#ch01.xhtml#page13)

Kubernetes, container

Control Groups (cgroups) [4](#ch01.xhtml#page4)

LinuX Containers (LXC) [4](#ch01.xhtml#page4)

Kubernetes, domination [9](#ch01.xhtml#page9)

Kubernetes Event-Driven Autoscaling (KEDA) [164](#ch11.xhtml#page164)\-[166](#ch11.xhtml#page166)

Kubernetes, governance [11](#ch01.xhtml#page11), [12](#ch01.xhtml#page12)

Kubernetes, history [7](#ch01.xhtml#page7), [8](#ch01.xhtml#page8)

Kubernetes, key components

Etcd [17](#ch02.xhtml#page17)

kube-apiserver [17](#ch02.xhtml#page17)

kube-controller-manager [17](#ch02.xhtml#page17)

kube-scheduler [17](#ch02.xhtml#page17)

Kubernetes, lifecycle

Persistent Volume Claims (PVCs) [18](#ch02.xhtml#page18)

Persistent Volumes (PVs) [18](#ch02.xhtml#page18)

volumes [18](#ch02.xhtml#page18)

Kubernetes, methodologies

cloud native innovation [10](#ch01.xhtml#page10)

DevOps/PaaS, aligning [10](#ch01.xhtml#page10)

orchestration consolidation [10](#ch01.xhtml#page10)

Kubernetes, milestones [10](#ch01.xhtml#page10)

Kubernetes, operations

Annotations [19](#ch02.xhtml#page19)

ConfigMaps, secrets [20](#ch02.xhtml#page20)

CronJob [21](#ch02.xhtml#page21)

DaemonSet [20](#ch02.xhtml#page20)

deployments [20](#ch02.xhtml#page20)

Horizontal Pod Autoscaler [20](#ch02.xhtml#page20)

Job [20](#ch02.xhtml#page20)

network, policies [20](#ch02.xhtml#page20)

security, contexts [20](#ch02.xhtml#page20)

StatefulSets [20](#ch02.xhtml#page20)

Kubernetes Policy, managing [193](#ch13.xhtml#page193), [194](#ch13.xhtml#page194)

Kubernetes Scaling, history [158](#ch11.xhtml#page158), [159](#ch11.xhtml#page159)

Kubernetes Worker, key components

Kubelet [17](#ch02.xhtml#page17)

Kube-proxy [17](#ch02.xhtml#page17)

L

Linux Containers [5](#ch01.xhtml#page5)

Load Balancing [172](#ch12.xhtml#page172), [173](#ch12.xhtml#page173)

M

monitor, logging [285](#ch18.xhtml#page285), [286](#ch18.xhtml#page286)

N

Namespaces [126](#ch09.xhtml#page126), [127](#ch09.xhtml#page127)

Namespaces, fundamentals

Helm, leveraging [132](#ch09.xhtml#page132), [133](#ch09.xhtml#page133)

HPA [137](#ch09.xhtml#page137), [138](#ch09.xhtml#page138)

ingress, configuring [130](#ch09.xhtml#page130)\-[132](#ch09.xhtml#page132)

monitor, exploring [138](#ch09.xhtml#page138), [139](#ch09.xhtml#page139)

pods, deploying [128](#ch09.xhtml#page128), [129](#ch09.xhtml#page129)

rollouts, managing [135](#ch09.xhtml#page135), [136](#ch09.xhtml#page136)

service mesh, using [136](#ch09.xhtml#page136), [137](#ch09.xhtml#page137)

services, optimizing [129](#ch09.xhtml#page129), [130](#ch09.xhtml#page130)

storage, integrating [133](#ch09.xhtml#page133), [134](#ch09.xhtml#page134)

Network Load Balancers (NLB) [71](#ch05.xhtml#page71)

P

Pipeline Orchestration [289](#ch18.xhtml#page289)

Pipeline Orchestration, key points

API, integrating [292](#ch18.xhtml#page292), [293](#ch18.xhtml#page293)

AWS CodePipeline, optimizing [289](#ch18.xhtml#page289)\-[292](#ch18.xhtml#page292)

trigger, mechanisms [292](#ch18.xhtml#page292)

Pod Networking [170](#ch12.xhtml#page170), [171](#ch12.xhtml#page171)

Pod Networking, aspects

custom, networking [176](#ch12.xhtml#page176)

network, policies [174](#ch12.xhtml#page174), [175](#ch12.xhtml#page175)

Prefix Delegation [177](#ch12.xhtml#page177), [178](#ch12.xhtml#page178)

security group [173](#ch12.xhtml#page173)

Pod Networking, security [185](#ch13.xhtml#page185)\-[187](#ch13.xhtml#page187)

Pulumi [103](#ch07.xhtml#page103), [104](#ch07.xhtml#page104)

R

RayService [376](#ch23.xhtml#page376)

RayService, steps [376](#ch23.xhtml#page376)\-[380](#ch23.xhtml#page380)

RBAC Authorization [113](#ch08.xhtml#page113), [114](#ch08.xhtml#page114)

RBAC Authorization, key points

ClusterRoles, optimizing [114](#ch08.xhtml#page114)

RoleBindings [115](#ch08.xhtml#page115)

subject [114](#ch08.xhtml#page114), [115](#ch08.xhtml#page115)

RBAC IAM, policies [115](#ch08.xhtml#page115), [116](#ch08.xhtml#page116)

RBAC, key aspects

AWS Console [120](#ch08.xhtml#page120), [121](#ch08.xhtml#page121)

eksctl [122](#ch08.xhtml#page122)

RBAC, key options

add-ons [119](#ch08.xhtml#page119)

IAM, roles [119](#ch08.xhtml#page119)

logging [117](#ch08.xhtml#page117)

networking [118](#ch08.xhtml#page118)

scaling [118](#ch08.xhtml#page118)

secrets, encrypting [117](#ch08.xhtml#page117)

update, recovery [118](#ch08.xhtml#page118)

version, upgrading [117](#ch08.xhtml#page117)

RDS, case studies [261](#ch17.xhtml#page261)

RDS, key points

Amazon, integrating [258](#ch17.xhtml#page258)

application, deploying [258](#ch17.xhtml#page258), [259](#ch17.xhtml#page259)

CLI, configuring [257](#ch17.xhtml#page257)

EKS/RDS, optimizing [257](#ch17.xhtml#page257)

performance, optimizing [260](#ch17.xhtml#page260)

RDS, practices [259](#ch17.xhtml#page259)

RDS Security, considering [260](#ch17.xhtml#page260)

Relational Database Service (RDS) [256](#ch17.xhtml#page256)

robust orchestration [135](#ch09.xhtml#page135)

S

Secrets Management [189](#ch13.xhtml#page189), [190](#ch13.xhtml#page190)

service mesh [136](#ch09.xhtml#page136)

Service Networking [171](#ch12.xhtml#page171), [172](#ch12.xhtml#page172)

Simple Storage Service (S3) [208](#ch14.xhtml#page208)\-[210](#ch14.xhtml#page210)

StatefulSets [143](#ch10.xhtml#page143), [144](#ch10.xhtml#page144)

StatefulSets, aspects

Data Lifecycle, managing [151](#ch10.xhtml#page151)

Higher Application, availability [149](#ch10.xhtml#page149)\-[151](#ch10.xhtml#page151)

PersistentVolumes [145](#ch10.xhtml#page145), [146](#ch10.xhtml#page146)

Snapshots [146](#ch10.xhtml#page146), [147](#ch10.xhtml#page147)

StorageClasses [147](#ch10.xhtml#page147), [148](#ch10.xhtml#page148)

Volume, scaling [149](#ch10.xhtml#page149)

StatefulSets, fundamentals

CSI [154](#ch10.xhtml#page154)

Mobility [154](#ch10.xhtml#page154), [155](#ch10.xhtml#page155)

monitoring [155](#ch10.xhtml#page155), [156](#ch10.xhtml#page156)

security [155](#ch10.xhtml#page155)

StatefulSets Storage, categories

application storage [152](#ch10.xhtml#page152)

archive storage [152](#ch10.xhtml#page152)

user storage [152](#ch10.xhtml#page152)

StatefulSets Storage, services

EBS Volumes [152](#ch10.xhtml#page152)

EFS Filesystems [153](#ch10.xhtml#page153)

S3 Object [153](#ch10.xhtml#page153)

T

Terraform [100](#ch07.xhtml#page100)\-[102](#ch07.xhtml#page102)

Terraform, key aspects

control plane, scaling [328](#ch21.xhtml#page328)

data plane [329](#ch21.xhtml#page329)

service, scaling [329](#ch21.xhtml#page329)

workload, scaling [330](#ch21.xhtml#page330)

V

Validation, testing [284](#ch18.xhtml#page284)

Vertical Pod Autoscaler (VPA) [160](#ch11.xhtml#page160)\-[162](#ch11.xhtml#page162)