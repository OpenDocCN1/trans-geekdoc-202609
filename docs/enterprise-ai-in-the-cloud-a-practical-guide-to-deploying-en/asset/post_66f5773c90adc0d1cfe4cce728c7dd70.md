

| TASK | TASK OWNER | EVALUATION CRITERIA | DELIVERABLE |
| :--- | :--- | :--- | :--- |
| Evaluate platform ecosystem and community, which are useful for faster development and troubleshooting. | Software engineer | Compare the availability of developer community, vendor support, and the development ecosystem such as APIs, SDKs, and development tools. | Report on platform ecosystem and community |
| Assess security and compliance, in particular for dealing with sensitive data. | Security analyst | Evaluate the cloud providers in terms of their support for encryption access controls, data privacy, and other industry certifications that they may have. | Report on platform support for security and compliance |
| Analyze pricing model and costs, which is important for budget management. | Financial analyst | Evaluate their pricing model and compare their costs for data storage, data processing, data transfer costs, compute costs, and ML service pricing. | Cost comparison report |
| Evaluate vendor support, which is required for smoother implementation and operation. | Project manager | Evaluate their documentation, training, product support, and the available developer and partner ecosystem. | Report on vendor support |
| Make a final recommendation. | Team lead | Make a recommendation based on your evaluations and choose a cloud provider or a combination thereof that suits your company. | Recommendation report |

**TIP** Consider the range of AI/ML services offered by the various cloud providers, including prebuilt models, development tools, and support for the entire ML lifecycle when choosing a cloud provider.

## KEY COMPONENTS OF AN ML AND DL PLATFORM

An ML platform's main components are enabling data ingestion, data preparation, model training, deployment, governance, and monitoring. Many organizations want to deploy their machine learning models in the cloud for the benefits discussed earlier. This is true for companies just beginning to deploy machine learning models and those who are advanced in this journey.

Organizations trying to get value from business applications or using curated data are looking at the underlying machine learning platform and infrastructure as a means to an end. By adopting AI services in the cloud, even developers with little or no skills in machine learning can build, train, and deploy complex models in production.

As you keep trying to adopt ML widely across your organization and as the requirements become increasingly complex, you must adopt a combination of cloud-based services, open-source tools, best-of-breed solutions, and your own proprietary custom solutions to build an enterprise-wide AI platform. This will give you fine-grained control over the entire platform but also take a lot of effort and cost. You can derive unique value from the platform software, infrastructure, and expertise, but you have to decide, based on the cost-benefit analysis, which approaches you want to take.

## KEY COMPONENTS OF AN ENTERPRISE AI/ML HEALTHCARE PLATFORM

This section considers the use case of a healthcare company trying to build an enterprise AI/ML imaging platform. You can use this to guide your own AI/ML platform. The platform must have the following components:

| Component | Description |
| :--- | :--- |
| Data ingestion | Ingest enormous amounts of medical data such as X-rays, CT scans, and MRIs from multiple sources. |
| Preprocessing and data cleaning | Automatically preprocess and clean the data such as reducing noise, adjusting contrast, and carrying out normalization. |
| Labeling | Label a subset of images to create a labeled dataset for subsequent model training. This may involve identifying and annotating abnormalities and identifying new feature sets. |
| Model training | Train the ML models using the labeled data to carry out machine learning tasks, such as anomaly detection, classification and segmentation. |
| Model testing | Test the machine learning models by integrating them into a simulation environment that simulates real-life clinical scenarios. This helps with thorough performance analysis and evaluation of the models before they can be deployed in production. |
| Model deployment | Deploy the models in a production scenario, such as a specific hospital or a diagnostic center, to assist doctors and radiologists in accurately interpreting medical images. |
| Performance monitoring | Continuously monitor the performance of these models by measuring their accuracy, recall, and precision metrics in real time. |
| Alerting, dashboarding, and feedback reports | Generate alerts, dashboards, and feedback reports to assist healthcare professionals so that they can make further improvements to these models, as well as provide better patient care by suggesting alternative diagnoses, identifying better treatments, and providing better care overall. |

> NOTE Handling large amounts of data requires a robust and automated data ingestion and preprocessing pipeline.

Figure 13.13 shows some core platform architecture components, each of which is covered in the following sections.

### DATA SOURCES
- ERP
- CRM
- SCM
- Third-party
- Social media, etc.

### DATA MANAGEMENT
- Data Transformation
- Versioning
- Shared Data Lake
- Processing & Labeling

### ML EXPERIMENT
- Pre-training
- Automate Triggers
- Feature Engineering

### MODEL TRAINING AND EVALUATION
- Model Training and Tuning
- Model Evaluation

### MODEL DEPLOYMENT
- Model Registry and Deployment
- Model Operationalization
- Model Execution
- Model Serving

### MODEL MONITORING & PERFORMANCE
- Model Monitoring
- Performance and Scalability of Models
- Distributed Computing
- Parallel Processing
- GPU Acceleration

### SECURITY AND GOVERNANCE
- Encryption
- Security Controls
- Model Inventory Management
- Audit Trail Management
- Tag Management

### MULTI-CLOUD ARCHITECTURE
- Workload distribution
- Redundancy management
- Disaster recovery
- Data synchronization

## **FIGURE 13.13**: Basic components and their integrations in an AI/ML platform

## Data Management Architecture

The data management components shown in Figure 13.14 are required for storing, ingesting, collecting, cleaning, and preparing data for model training. You also need data orchestration, distribution, governance, and access control tools.

### Shared Data Lake

To use data for machine learning, you must store the data in one central location. It is recommended to set up a data lake for this purpose. Consider factors such as data volumes, data access patterns, and data lifecycle management requirements. You must choose data storage solutions such as Amazon S3, Google Cloud Storage, and Azure Blob Storage based on your specific requirements.

Once you store large datasets in S3, other data processing and ML services can access that data. Storing data in one central location, such as S3, helps you manage data scientists' workflow, facilitates automation, and enables true collaboration and governance.

Creating the following folder structure with proper data classification will help you exercise access control and facilitate machine learning workflows, tracking, traceability, and reproducibility during experiments:

| Folder | Description |
| :--- | :--- |
| Users and project teams folders | Individual data scientists and teams can use these folders to store their training, test, and validation datasets that they use for experimentation purposes. |
| Shared features folders | These folders can contain shared features such as customer data, product data, time series, and location data, which can all be used for model training across teams and models. |
| Training, validation, and test datasets folders | These are used for formal model training, testing, and validation purposes. Managing these folders is essential, as this can help you with the traceability and reproducibility of models. |
| Automated ML pipelines folders | These folders can be accessed only by automated pipelines, such as an AWS CodePipeline for storing artifacts related to the pipeline. |
| Models in production folders | These models should be actively monitored and managed through version control and play a key role in ensuring traceability. |

### Data Sources

Your data can come from one or more sources located in various locations or systems. It helps to treat them as enterprise-level assets rather than department-specific assets. The data sources can include databases, data warehouses, data lakes, external APIs, files, and even streaming data from IoT devices and sensors. These sources provide the raw data for the ML models during the training process.

### Data Ingestion

Data ingestion is the process of loading the data from these data sources into the machine learning platform, which can be an automated or manual process. It includes techniques such as data extraction, integration, and loading.

### Data Catalog

The data catalog acts as the central repository for all metadata about the datasets that are used in the ML system. It contains information related to data sources, dataset description, data quality metrics, schema information, data format, and

