User behavior can be unpredictable. For instance, suppose a model requires a string value, but the user provides an alphanumeric value. In such scenarios, the model output might not be reliable.

# Security

ML systems are prone to security breaches. They may be forced to deliver false predictions by deliberately providing poisonous data or adding noise to the data. The models perform better when trained on new data. However, a person or a group of people can deliberately pass the poisonous data to the model, intending to change the model predictions.

Data security is at risk as the model keeps training on new data. While training the model, attackers can steal sensitive information.

# MLOps

MLOps combines machine learning processes and best practices of DevOps to deliver consistent output with automated pipelines and management. MLOps has been an emerging space in the industry for the last few years.

The following figure shows the increasing popularity of MLOps over time.

![](bbox=[0.13, 0.53, 0.87, 0.73])

Figure 3.2: The rise of MLOps. Source: Google trends

MLOps bridges the gap between machine learning experiments and model deployment in the production environment. Nowadays, many data scientists are forced to execute the MLOps processes manually.

The MLOps process involves multiple professionals, and data scientists play a critical role. Subject matter experts understand and collect the requirements from the client. Then, data engineers collect the data from multiple sources and execute the ETL jobs. Once this is done, data scientists build the models and the DevOps