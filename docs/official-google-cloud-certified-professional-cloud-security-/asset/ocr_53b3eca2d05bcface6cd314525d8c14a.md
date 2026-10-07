# Best practices and design considerations

Cloud Asset Inventory is not part of the exam blueprint, you may see indirect references to assets and policies, and it will benefit you as a Google Cloud Security engineer to have a foundational understanding of how asset management is done on Google Cloud and, more importantly, its relevance to security.

We will next look at some of the best practices and design considerations that you should know about and how they apply to the resources in your project.

# Best practices and design considerations

Some of the design considerations are to understand how the resources will be managed inside the project. Using one project might be a good idea to keep it simple, but the isolation and separation of duties will be needed. On the flip side, if you use too many projects, there will be a lot of overhead to manage the projects, but you will achieve the separation of duties and the isolation required.

Some of the design considerations to follow when breaking down resources and workloads into projects are follows. Bear in mind that all these considerations are related:

+   You don't want a misconfiguration or a compromise in one operating environment to impact the other. A key consideration is to reduce the blast radius.

+   Quotas and limits are applied at the project level. It is undesirable for a dev/test project to consume the quota required by a prod project, or that one app consumes the quota of another.

+   You want to break down cloud resources in a way that will ensure least-privilege access. A key consideration is reducing administrative complexity.

+   It's easier to track billing at the project level.

+   Ensure the separation of duties. For example, you might want to separate central networking projects from app projects to achieve the separation of duties between networking teams and development teams.

+   You want to achieve all the above for different operating environments by separating accordingly (for example, prod, test, dev, staging, and user acceptance testing).

The preceding considerations help us understand how and when to consider breaking down resources and projects. Further to this, some key considerations for managing projects are having one project per application, using data classification as a way to keep sensitive data in separate projects and not mixing different data classifications, and finally, using consistent project ID naming conventions.

The best practice is to use workload- and environment-specific projects, and as project creation is a repetitive task, Infrastructure as Code and automation should be leveraged.