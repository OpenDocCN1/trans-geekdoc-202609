
## Deploy and Monitor Models

**Automate deployment:** You should automate the deployment process and make it repeatable and standardized. This will ensure that the model is deployed consistently across multiple environments.

**Automated performance monitoring:** You need to ensure that the model is performing well over a period of time. The monitoring process needs to be automated so that you can proactively identify and address any issues promptly. You need a robust monitoring system to measure the model's performance metrics, such as accuracy, precision, recall, latency, and throughput.

- Deploy Your Models into Production
- Monitor and Secure Models
- Govern Models for Bias and Ethics

### Objective

Seamlessly transition AI/ML models from development to live environments, ensuring optimal deployment strategies, real-time responsiveness, and consistent configuration for efficient production operations

**FIGURE 18.1: DEPLOY AND MONITOR MODELS:** Deploy your models into production.

**Ethical use and responsibility:** You need to ensure that the model is used responsibly and ethically in a production environment without discriminating against its users. To enforce governance, you must define policies and procedures integrated into your organization's overall governance framework and establish systems to detect bias proactively and address them in real time.

**TIP** Adopt deployment best practices such as automatically deploying through CI/CD pipelines, deployment scripts, version control, continuous performance monitoring, ethical use, proactive bias detection, and establishing a model governance framework.

## Challenges in Model Deployment Monitoring and Governance

There are several challenges when deploying models and ensuring they are implemented ethically and responsibly in production, discussed next.

### Model Deployment Challenges

Consider these deployment challenges:

- **Scalability:** Models may not scale well enough to handle large amounts of data in production.
- **Operational efficiency:** Poor operational efficiency and data silos may result from a lack of integration of the models with backend processes, systems, and data storage systems.
- **Latency:** High latency of the models can render them useless for practical use.
- **Reproducibility:** Over time, reproducing these models for retraining and redeployment becomes impossible because of numerous changes in the underlying hardware, software libraries, and other dependencies.

### Model Monitoring Challenges

Here are some monitoring-related challenges:

- **Dynamic data:** The world is constantly changing, and therefore, the data feeding the models also changes, which can cause issues when monitoring the model performance.
- **Model complexity:** Most of these models are complex, and it becomes difficult to understand how they work because of the black-box nature of the algorithms. It poses a challenge to enforcing governance of the models because of the need for model explainability and interpretability.
- **Talent shortage:** There is not enough talent and resources to focus on model deployment and monitoring.
- **Unified framework:** You may find that the methods adopted to develop and deploy models are not standardized across teams.
- **Data lineage tools:** There is also a lack of transparency in the data quality and lineage.

### Model Governance Challenges

Finally, these are governance challenges:

- **Bias control:** Since these models reinforce existing biases in the data, controlling biases is a challenge.
- **Data privacy and regulation:** Data privacy and security should be carefully protected during training and prediction to comply with legal regulations such as GDPR, CCPA, and HIPAA.
- **Industry regulations:** Navigating regulations in industries such as healthcare or finance can be an issue.
- **Model inventory:** Models tend to increase rapidly across business units in large enterprises, and keeping track of inventories becomes tough.
- **Change logs:** Keeping track of changes in AI models is not easy because you have to track the changes in the code and the changes in data, hyperparameters, and models.
- **Accountability:** The question of who is accountable or responsible when the model fails is also tricky.

> **TIP** Solving these challenges requires a mix of technology initiatives such as MLOps, pipelines, explainability techniques, governance policies, data use policies, regulatory guidelines, and culture.

## DEPLOYING YOUR MODELS

This section dives into the model deployment process. It is often underestimated in the model development lifecycle. However, it is the most crucial step from a user perspective because it makes the model available for user consumption. The following sections review some best practices.

### Pre-deployment Checklist

First, you must ensure the model is fully trained and tested. Second, ensure that you have fully optimized the model using the best practices discussed in the previous chapter. Third, perform dry runs in a staging or sandbox environment to uncover unforeseen issues.

### Deployment Process Checklist

As shown in [Figure 18.2](), the deployment process involves the following:

- **Features**: Retrieve the features from the feature store.
- **Artifacts and dependencies**: Retrieve the model from the model registry and other artifacts required for the model to run.
- **Inference code container**: Retrieve the inference code container, which contains the code required to make the predictions against the model. The inference code container is typically retrieved from the container registry using a docker pull command.
- **Deployment**: Once the features, the artifacts, and the inference code container are retrieved, the model is deployed into the production environment.
- **API access:** Making it available as a Restful API using a web service framework like Flask or deploying it in a cloud platform such as AWS SageMaker, GCP, or Azure Machine Learning.
- **Application integration:** Integrating it with other applications if necessary.
- **Monitoring:** Periodically review the model's output with the actual values to ensure the model performs properly using a manual or an automated governance process.

![](img/1490b3cf638678afadc8c48abc1698d5_502_0.png)

FIGURE 18.2: Model deployment process

### Choosing the Right Deployment Option

As part of your architecture design discussion, you need to decide which one of the model deployment options is the best fit for you. As shown in Figure 18.3, you have four options: cloud deployment, on-premises deployment, edge deployment, and hybrid deployment.

### Cloud Deployment

Here are some considerations for cloud deployment:

- **Scalability:** Cloud is the best option if you have many users to serve and if the load fluctuates. It allows you to process large amounts of data using a large computing capacity, and to store large amounts of data.

![](img/1490b3cf638678afadc8c48abc1698d5_503_0.png)

**FIGURE 18.3:** Model deployment options

- **Service integration:** The cloud providers also provide several services that make deploying and managing your model easy. For example, you can leverage services for computing, storage, and networking.
- **Data security:** The cloud allows you to connect to sensitive data using robust network security protocols offered by the cloud providers.

For these reasons, the cloud option is often the most popular option.

### On-Premises Deployment

Some companies may resort to on-premises deployment of their models using their own servers, storage, and networks in their data centers.

- **Security requirement:** It is preferred when security is a primary requirement, and you want to keep your data in your own locations.
- **Infrastructure control:** It also gives more control over their infrastructure. However, you need to regularly update your hardware and software, have robust backup and disaster recovery, and regularly monitor for bottlenecks.
- **Expensive:** However, it can be more expensive and resource intensive to manage.

### Edge Deployment

Here are some considerations for edge deployment:

- **Model performance and latency:** If your model performance and latency are important, then you would resort to deploying the model at the edge where the data resides and action happens. Your edge devices could be smartphones, IoT sensors, tablets, or industrial machines.
- **Real-time processing:** It allows you to process data in real time, provides greater privacy, and has fewer bandwidth requirements.
- **More complex:** However, this can be the most complex deployment type because managing and updating models across multiple devices can take time and effort.
- **Other considerations:** Remember that you need to implement device management to manage software updates, may encounter issues because of limited computing power, and may need to synchronize data between central servers/cloud and devices.

**NOTE** AWS IoT Greengrass can run models in edge devices using models trained in the cloud.

### Hybrid Deployment

People use a hybrid deployment to get the best of both worlds, namely, cloud and on-prem deployments.
