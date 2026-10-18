
It is worth noting that ML solutions architecture does not focus on developing new machine algorithms, a job best suited for applied data scientists or research data scientists. Instead, ML solutions architecture focuses on identifying and applying ML algorithms to address a range of ML problems such as predictive analytics, computer vision, or natural language processing. Also, the goal of any modeling task here is not to build production-quality models but rather to validate the approach for further experimentations by full-time applied data scientists.

## System architecture design and implementation

The most important aspect of the ML solutions architect’s role is the technical architecture design of the ML platform. The platform will need to provide the technical capability to support the different phases of the ML cycle and personas, such as data scientists and operations engineers. Specifically, an ML platform needs to have the following core functions:

*   **Data explorations and experimentation**: Data scientists use ML platforms for data exploration, experimentation, model building, and model evaluation. ML platforms need to provide capabilities such as data science development tools for model authoring and experimentation, data wrangling tools for data exploration and wrangling, source code control for code management, and a package repository for library package management.

*   **Data management and large-scale data processing**: Data scientists or data engineers will need the technical capability to ingest, store, access, and process large amounts of data for cleansing, transformation, and feature engineering.

*   **Model training infrastructure management**: ML platforms will need to provide model training infrastructure for different modeling training using different types of computing resources, storage, and networking configurations. It also needs to support different types of ML libraries or frameworks, such as `scikit-learn`, `TensorFlow`, and `PyTorch`.

*   **Model hosting/serving**: ML platforms will need to provide the technical capability to host and serve the model for prediction generations, for real-time, batch, or both.

*   **Model management**: Trained ML models will need to be managed and tracked for easy access and lookup, with relevant metadata.

*   **Feature management**: Common and reusable features will need to be managed and served for model training and model serving purposes.

## ML platform workflow automation 

A key aspect of ML platform design is `workflow automation` and `continuous integration`/`continuous deployment` (`CI`/`CD`), also known as MLOps. ML is a multi-step workflow – it needs to be automated, which includes data processing, model training, model validation, and model hosting. Infrastructure provisioning automation and self-service is another aspect of automation design. Key components of workflow automation include the following:

*   **Pipeline design and management**: The ability to create different automation pipelines for various tasks, such as model training and model hosting.

*   **Pipeline execution and monitoring**: The ability to run different pipelines and monitor the pipeline execution status for the entire pipeline and each of the steps in the ML cycle such as data processing and model training.

*   **Model monitoring configuration**: The ability to monitor the model in production for various metrics, such as data drift (where the distribution of data used in production deviates from the distribution of data used for model training), model drift (where the performance of the model degrades in the production compared with training results), and bias detection (the ML model replicating or amplifying bias towards certain individuals).

## Security and compliance

Another important aspect of ML solutions architecture is the security and compliance consideration in a sensitive or enterprise setting:

*   **Authentication and authorization**: The ML platform needs to provide authentication and authorization mechanisms to manage access to the platform and different resources and services.

*   **Network security**: The ML platform needs to be configured for different network security controls such as a firewall and an IP address access allowlist to prevent unauthorized access.

*   **Data encryption**: For security-sensitive organizations, data encryption is another important aspect of the design consideration for the ML platform.

*   **Audit and compliance**: Audit and compliance staff need the information to help them understand how decisions are made by the predictive models if required, the lineage of a model from data to model artifacts, and any bias exhibited in the data and model. The ML platform will need to provide model explainability, bias detection, and model traceability across the various datastore and service components, among other capabilities.

Various industry technology providers have established best practices to guide the design and implementation of ML infrastructure, which is part of the ML solutions architect’s practices. Amazon Web Services, for example, created `Machine Learning Lens` to provide architectural best practices across crucial domains like operational excellence, security, reliability, performance, cost optimization, and sustainability. Following these published guidelines can help practitioners implement robust and effective ML solutions.

# Summary

In this chapter, I have shared some of my personal experience as an ML solutions architect and provided an overview of core concepts and components involved in the ML lifecycle. We discussed the key responsibilities of the ML solutions architect role throughout the lifecycle. This chapter aimed to give you an understanding of the technical and business domains required to work effectively as an ML solutions architect. With this foundational knowledge, you should now have an appreciation for the breadth of this role and its integral part in delivering successful ML solutions.

In the upcoming chapter, we will dive into various ML use cases across different industries, such as financial services and media and entertainment, to gain further insights into the practical applications of ML.

# Join our community on Discord

Join our community’s Discord space for discussions with the author and other readers:

[https://packt.link/mlsah](https://packt.link/mlsah)

![](OEBPS/Images/QR_Code70205728346636561.png)

# 2

# Exploring ML Business Use Cases

As an `ML` practitioner, it is essential for me to develop a deep understanding of different businesses to have effective conversations with business and technology leaders. This should not come as a surprise since the ultimate goal of any ML solutions architecture is to solve practical business problems with science and technology solutions. Therefore, one of the main areas of focus for ML solutions architecture is to develop a broad understanding of different business domains, workflows, and relevant data. Without this understanding, it would be challenging to make sense of the data and design and develop practical ML solutions for business problems.
