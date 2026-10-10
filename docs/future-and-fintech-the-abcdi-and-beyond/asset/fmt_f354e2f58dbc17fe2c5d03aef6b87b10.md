
Some biases are inherited and unavoidable, but most are not; instead, they are just being simply misapplied or manipulated. [Figure 4.2](#chap4.xhtml#fig4-2) shows three common types of biases in a general sense, and we can avoid most of the cognitive and contextual biases if we are cautious.

Fairness in fact is closely related to other factors such as accuracy, privacy, explainability, and security ([Figure 4.3](#chap4.xhtml#fig4-3)). Fairness is usually in the same direction as explainability, but may not be with others in some scenarios; hence, we may need a trade-off in the design stage. For example, it is generally difficult for an AI system to achieve both high degrees of privacy and accuracy. Similarly, more privacy information can make fairness treatment more adjustable. Note that we need to take the application scenarios into consideration, as sometimes accuracy is more important and there are legitimate grounds for privacy and fairness. Sometimes, however, the fairness metrics must be satisfied at the expense of accuracy. Therefore, risk mitigation techniques are necessary for achieving the right balance between different metrics.

In AI and data-driven modeling, we usually use "protected" variables to indicate factors that may cause fairness issues, e.g., gender, age, race, citizenship, disability status, sexual orientation, religion, culture, theology, tradition, social class, resource availability, and ethnicity. The opposite is "unprotected" variables, which refers to public information available in the market.

![](images/p121.jpg)

**Figure 4.3.** Relations between fairness and other factors

Protected variables often implicate personal privacy, and their usage varies by the type of financial products. For example, personal income may be required in the case of credit card applications but not for general bank account openings. These protected variables can be further differentiated into privileged and unprivileged categories. For example, disabled persons and minority races are often considered as unprivileged categories.

AI ethics shall not be considered as a constraint on the FIs' capabilities to increase profits for shareholders. In fact, AI ethical principles can be used as one of the key design criteria for innovative development, with the objective to improve wellbeing, reduce inequities and bias, and help people achieve their goals. For example, not lending to someone who is falsely predicted with a higher risk due to racial reasons is a reputational risk and also a missed opportunity. By removing such biases, FIs may attract more high-net-worth clients.

Therefore, FIs shall build their AI ethical framework. As pointed out by the Personal Data Protection Commission (PDPC) of Singapore^[6](#chap4.xhtml#rfn6), the model framework is intended to be broadly applicable — it shall be agnostic to algorithm, technology, sector, scale, and business model. The design for the fairness treatment in AI shall follow similar rules. Since ML pipeline can be applied in most design and development processes, we choose it as the main stem to discuss AI Fairness. In the next two sections, we will discuss the general ML pipeline first, and then present more details on the Fairness pipeline.

### 4.3 ML Pipeline

The pipeline is a widely accepted concept and methodology in many industries. A product pipeline is a series of components to reduce the delay between completed tasks. It has a certain level of automation and increases the throughput in various stages of the product lifecycle. Pipelines usually contain batch processing, i.e., collecting data, sending it through a network, and processing it to provide pre-calculated results and guidance for next stages.

An ML pipeline is used to create formal and automated ML workflows. It builds the necessary components and steps in the lifecycle of the data and model. For example, a data pipeline enables a sequence of data to be extracted, transformed, filtered, and cleaned before sending to a model for training, testing, and evaluation. A model pipeline also contains model deployment and maintenance. An ML lifecycle usually contains five stages: project design, data processing, model development, model/system deployment, and model maintenance, as shown in [Figure 4.4](#chap4.xhtml#fig4-4).

A common ML lifecycle pipeline is illustrated in [Figure 4.5](#chap4.xhtml#fig4-5). An abstracted concept of ML pipelines within the ML lifecycle is named MLOps, which will be further discussed in [Chapter 14](#chap14.xhtml).

For a completed new project, its problem statement, scope, and objective must be clearly defined first by business stakeholders and SMEs. The development team studies its feasibility and provides potential solutions. Resource and cost shall be estimated before the project starts. Once the project is formally set up, access to various ML-relevant resources (e.g., data, workbench, ML platform, and Cloud) shall be applied for approval. Then the raw data will be ingested from databases or other data sources, pre-processed and analyzed at Stage 1 before feeding into the ML development environment in Stage 2.

![](images/p123.jpg)

**Figure 4.4.** ML lifecycle in five stages

![](images/p124.jpg)

**Figure 4.5.** ML pipeline

ML development is generally an iterative procedure to enhance features and improve models with proper evaluation metrics at Stage 2. The processed data and features can be stored in the `Feature Store`, an ML-specific feature management system. The relevant codes, configurations, and documentation will be stored in `Git` (a file version control and management system, e.g., `Bitbucket` or `Github`), and the model will be registered in the `Model Inventory` (or `Model Registry`) and accessed in `Central Repository`. ML developers may get the required tools and repositories from `Central Repository` (e.g., `Artifactory`, a universal artifact repository manager), and gain access to container images (e.g., packaged ML model and environments). Once all the necessary artifacts are ready, the model, which might be integrated into a system, will be deployed in different environments (e.g., user acceptance testing (UAT) and staging for testing and validation). Non-satisfactory results of ML metrics may lead to an ML model re-train (i.e., go back from Stage 3 to Stage 2).

If all the tests are passed and the model/system is signed off by the right person, the model and system can be promoted into a formal production environment. `Feature Store` can feed live data into the ML model for real-time or batch inference. A proper monitoring and diagnosis configuration must be implemented for potential ML issues (e.g., model performance downgrade, data drift, etc.), which might trigger a re-train event with proper process governance.

Note that it is not necessary that every project must have all five stages or all the components indicated here. Sometimes, even the execution sequences in a pipeline can be different. A proper pipeline design shall depend on actual project requirements, not a fixed structure. More details will be discussed in [Chapter 14](#chap14.xhtml).

### 4.4 Fairness Pipeline

Following the ML pipeline, we can create similar pipelines for fairness. [Figure 4.6](#chap4.xhtml#fig4-6) highlights a few questions to be asked at each stage, and [Table 4.1](#chap4.xhtml#tab4-1) highlights the key considerations for each stage.

A precondition to relieve bias is the proper definition and measurement of fairness during the product and service design phases. For simplicity, we may divide them into three phases: before-, in-, and after-modeling, as shown in [Table 4.2](#chap4.xhtml#tab4-2), where each phase has its emphasis: data, model, and maintenance, respectively.
