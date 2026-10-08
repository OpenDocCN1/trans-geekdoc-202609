
# Model inventory

The model registry is an essential component in the ML governance framework. It helps provide visibility into the available models and their uses, and it is a key tool for both business operations and risk management to govern the use of ML models. With a model registry, you can keep a catalog of models in different stages, version control them, and associate metadata, such as training metrics, with the models. You can also manage the approval process for deployment and use this as part of MLOps pipeline to track lineage and activities against the model training and deployment life cycle.

There are both open source model registry platforms (such as MLFlow model registry) as well as managed model registry services available for model management. As we mentioned in Chapter 9, Building an Enterprise ML Architecture with AWS ML Services, SageMaker has a managed model registry offering provides the following capabilities to support ML governance activities and processes:

- Model inventory: All the versions of the different models belong to a respective model group in the SageMaker registry. You can view all the model groups and different versions of a model in the registry: Metadata such as model metrics, training job details, hyperparameters used for training, and training data sources are important data points for the model review and model audit processes. Depending on specific business requirements, you can set up a central model registry for a single enterprise view, or even distributed model registries if that can meet your governance and audit requirements.

- Model approval and life cycle tracking: You can track the approval of models and model stages directly inside the SageMaker model registry. This helps the business operations and audits ensure the proper processes are followed.

SageMaker's model registry can be part of an automated MLOps pipeline to help the consistency and repeatability of model management and model updates.

# Model monitoring

Post-deployment model monitoring helps detect model failures so that the appropriate remediation actions can be taken to limit risk exposure. Models need to be monitored for system availability and errors, as well as data drift and prediction failure.

As we mentioned in Chapter 9, Building an Enterprise ML Architecture with AWS ML Services, SageMaker provides a monitoring feature for both data drift and model drift. Specifically, SageMaker Model Monitor supports the following:

- With SageMaker Model Monitor, you can monitor data quality issues and data distribution skews (also known as data drift) in production. To use this, you must create a baseline using a baseline dataset, such as a training dataset, to gather statistics, data types, and suggest constraints for monitoring. SageMaker Model Monitor can capture inference traffic, calculate data statistics, examine data types, and verify them against the constraints and trigger alerts. For example, if a feature's mean and standard deviation changes significantly from the baseline, an alert can be triggered.

- Model performance drift: When you use Model Monitor to detect model performance changes in production. To use this feature, you can create a model performance baseline job using a baseline dataset that contains both the inputs and labels. The baseline job will suggest constraints, which are the metrics thresholds that Model Monitor monitors against the metrics calculated with the ground truth data that was collected in production. These metrics can be optionally sent to CloudWatch for visualization.

- Feature attribution drift: When enabled with SageMaker Clarify, SageMaker Model can report feature attribution drift. Feature attributions are indicators of feature importance for the prediction output. Similar to data and model drift, you can create a SHAP baseline job using baseline data to generate constraint suggestions. The separate monitoring job is then scheduled to model predictions in production against the baseline.

SageMaker Model Monitoring can be integrated with automated alerting and response systems to streamline the remediation of model and data issues.

# Change management control

To ensure model deployment process consistency to reduce operational risk, as well as to support auditing, the appropriate change management control needs to be put in place. This might include documentation about the nature of the change and its impact, change review and approval, change ticketing, access and activity monitoring, and backout procedures.

There are purpose-built change management tools for workflows and ticketing management. The underlying ML infrastructure needs to integrate with the change management workflow to ensure all the data points are collected and auditable.

SageMaker provides features that can support change management control, such as model approval status change tracking, model deployment logging, and fine-grained activity logging, such as for the IAM roles that were used for model deployment.

# Lineage and reproducibility

One of the key requirements in many ML governance frameworks is to establish lineage across data and models so that a model can be reproduced when required. The data is needed to establish lineage includes training data sources, the algorithm that was used, hyperparameter configuration, and the model training script. SageMaker provides several features to establish lineage:

- SageMaker training keeps clean lineage as training data sources, training job containers (contains algorithm and training script), hyperparameter configuration, and model artifact locations. Historical training job data is immutable in the SageMaker environment for retention purposes.

- SageMaker Experiment and ML Lineage can contain additional component details, such as data processing, for more complete lineage tracking.

- SageMaker Hosting provides information on the location of the original model artifact and the inference container to trace the lineage from model to endpoint.

These data points are available by calling the SageMaker API. An external application can call the SageMaker API directly to extract this data for review purposes. Alternatively, a data extraction job can be developed to extract these data points and load them into a purpose-built risk management store for analysis.

# Observability and auditing

Auditing mostly focuses on process verification and artifact collection in support of audit activities. The underlying platform normally serves as an information source for collecting artifacts. For example, if there is a risk management policy that requires approval before a model is deployed into production, then the audit will need to access the system of record to ensure such data is collected and retained.

SageMaker and other related services can be data sources in support of the overall audit process. Specifically, it provides the following information that can be relevant for auditing purposes:

- Activity and access audit trail: SageMaker sends all audit trail data to CloudWatch logs, which can be retained and analyzed for audit purposes.

- Model approval tracking: Model deployment approvals are tracked in SageMaker model registry. This can be provided to an auditor as evidence that the required approval processes have been followed.

- Lineage tracking: SageMaker Experiment and ML Lineage tracking components can track and retain model lineages such as data processing, model training, and model deployment. Lineage tracking information helps the auditor verify that the model can be reproduced using its original data and configuration dependencies.

- Configuration changes: System configuration data is captured in AWS CloudTrail as change events. For example, when a SageMaker endpoint is deleted, there will be an entry in AWS CloudTrail indicating this change.

Similarly, automated jobs can be implemented to extract this information and feed it into purpose-built data stores for risk management. An audit is a complex process that can involve many business functions and technology systems. To support the full audit process, you will need the support of multiple technology platforms and human processes to supply the required data.

# Security and privacy-preserving ML

ML privacy is becoming increasingly important in ML implementation. To ensure compliance with data privacy regulations or even internal data privacy controls, ML systems need to provide foundational infrastructure security features such as data encryption, network isolation, compute isolation, and private connectivity. With a SageMaker-based ML platform, you can enable the following security controls:

- Private networking: As SageMaker is a fully managed service, it runs in AWS-owned account. By default, the resources in your AWS account communicate with SageMaker APIs via the public internet. To enable private connectivity to SageMaker components from your own AWS environment, you can attach them to a subnet in your virtual private cloud (VPC).

- Storage encryption: Data-at-rest encryption can be enabled by providing an encryption key when you create a SageMaker notebook, a training job, a processing job, or a hosting endpoint.

- Disabling internet access: By default, your SageMaker notebook, training job, and hosting service have access to the internet. This internet access can be disabled via configuration.
