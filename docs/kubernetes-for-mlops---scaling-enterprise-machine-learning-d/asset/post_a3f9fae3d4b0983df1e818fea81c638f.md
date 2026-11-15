
At Airbnb, for example, after gaining experience with applying machine learning to applications like search ranking, smart pricing, and fraud prevention, the company realized that it would need to dramatically increase the number of models it was putting into production in order to meet its business goals. To enable this, an ML infrastructure team was established. The team's mission is to eliminate what it calls the incidental complexity of machine learning—that is, getting access to data, setting up servers, and scaling model training and inference—as opposed to its intrinsic complexity—such as identifying the right model, selecting the right features, and tuning the model's performance to meet business goals.

Common challenges encountered by ML infrastructure teams include:

## Simplifying and automating data access & management

Because so much of model building involves acquiring and manipulating data, providing a way to simplify and automate data acquisition and data transformation, feature engineering, and ETL pipelines is necessary to increase modeling efficiency and ensure reproducibility.

Data acquisition is greatly facilitated when a centralized data repository or directory is available, such as a data lake, fabric, warehouse, or catalog. These enable efficient data storage, management, and discovery, allowing data that is generated from a variety of disparate systems to be more easily worked with by minimizing the time data scientists spend looking for data or trying to figure out how to access new systems.

Data and feature transformations create new data needed for training and often inference. The data produced by these transformations is not typically saved back to the systems of origin, such as transactional databases or log storage. Rather, it is persisted back to facilities such as those mentioned above. Ideally, transformation and feature engineering pipelines are cataloged for easy sharing across projects and teams.

In addition to the efficiency benefits they offer, feature data repositories can also help eliminate time-consuming and wasteful data replication when architected in a way that meets the latency and throughput requirements of a wide range of machine learning training and inference workloads. Because of the scalability, security, and other technical requirements of feature data repositories, ML infrastructure teams typically work with data engineers and corporate IT to establish them.

## Driving efficient resource use

Today, we have more raw computing power at our disposal than ever before. In addition, innovations such as high-density CPU cores, GPUs, TPUs, FPGAs, and other hardware accelerators are increasingly targeting ML and DL workloads, promising a continued proliferation of computing resources for these applications. Despite declining computing costs, the machine learning process is so bursty and resource-intensive that efficient use of available computing capacity is critical to supporting ML at scale. The following are key requirements for efficiently delivering compute to machine learning teams:

- **Multitenancy.** Establishing dedicated hardware environments for each machine learning team or workload is inefficient. Rather, the focus should be on creating shared environments that can support the training and deployment needs of multiple concurrent projects.

- **Elasticity.** Data preparation, model training, and model inference are all highly variable workloads, with the amount and type of resources they require often varying widely in time. To efficiently meet the needs of a portfolio of machine learning workloads it is best when the resources dedicated to individual tasks can be scaled up when needed, and scaled back down when done.

- **Immediacy.** Data scientists and MLEs should have direct, self-service access to the number and type of computing resources they need for training and testing models without waiting for manual provisioning.

- **Programmability.** The creation, configuration, deployment and scaling of new environments and workloads should be available via APIs to enable automated infrastructure provisioning and to maximize resource utilization.

These are, of course, the characteristics of modern, cloud-based environments. However, this does not mean that we're required to use the third-party “public” cloud services to do machine learning at scale.

While the public cloud's operating characteristics make it a strong choice for running some machine learning workloads, there are often other considerations at play. Performance requirements often demand co-locating training and inference workloads with production applications and data in order to minimize latency.

Economics is an important consideration as well. The cost of renting computing infrastructure in the cloud can be high, as can the cost of inbound and outbound data transfers, leading many organizations to choose local servers instead.

As both cloud and on-premises resources have their place, hybrid cloud deployments that harness resources from both are a worthy consideration for many organizations. Hybrid cloud deployment allows organizations to distribute workloads across cloud and on-premises resources in ways that allow them to quickly and cost-effectively meet fluctuating workload demands and provide increased computational power when needed.

Ultimately, in a world of rapid hardware innovation, dynamic infrastructure economics, and shifting workloads, it is prudent to build flexibility into new tools and platforms, so that they can be efficiently operated in any of these environments.

## Hiding complexity

With the rise of Platform-as-a-Service (PaaS) offerings and DevOps automation tools, software developers gained the ability to operate at a higher level of abstraction, allowing them to focus on the applications they are building and not worry about the underlying infrastructure on which their software runs.

Similarly, in order for the machine learning process to operate at full scale and efficiency, data scientists and MLEs must be able to focus on their models and data products rather than infrastructure.

This is especially important because data products are built on a complex stack of rapidly evolving technologies. These include more established tools like the TensorFlow and PyTorch deep learning frameworks; language-specific libraries like SciPy, NumPy and Pandas; and data processing engines like Spark and MapReduce. In addition, there has been an explosion of specialty tools aiming to address specific pain-points in the machine learning process, many of which we discuss in our accompanying book, _The Definitive Guide to Machine Learning Platforms_, and cover in our online **ML/AI Solutions Guide**.

These high-level tools are supported by a variety of low-level, vendor-provided drivers and libraries, allowing training and inference workloads to take advantage of hardware acceleration capabilities. Some of these driver stacks are notoriously difficult to correctly install and configure, requiring that complex sets of interdependencies be satisfied.

Manually managing rapidly churning software tools and the resulting web of dependencies can be a constant drain on data scientist productivity, and the source of hard-to-debug discrepancies between results seen in training and production.

## Unifying the ML workflow

Ultimately, as an organization’s use of data science and machine learning matures, both business and technical stakeholders alike benefit from a unified ML workflow, with a common framework for working with the organization’s data, experiments, models, and tools.

The benefits of a common platform apply across the ML workflow. A unified view of data, as we’ve previously discussed, helps data scientists find the data they need to build models more quickly. A unified view of experiments helps individual users and teams identify what’s working faster, and helps managers understand how resources are being allocated. A unified view of deployed models helps operations and DevOps teams monitor performance across a wide fleet of services. And a unified view of infrastructure helps data scientists more readily access the resources they need for training.

With a unified approach to the machine learning workflow, it becomes much easier to facilitate and manage cross-team collaboration, promote the reuse of existing resources, and take advantage of shared skills. It also enables individual team members to more quickly become productive when transitioning to new projects, driving increased efficiency and better overall outcomes for data science and ML/AI projects.
