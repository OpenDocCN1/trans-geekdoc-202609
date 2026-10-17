
Figure 8.11: SageMaker hosting architecture

The SageMaker Hosting service offers multiple model inference options for different needs, from real-time inference to batch inference. The following are some options available for data scientists to use for model hosting evaluation and testing:

*   One of the most common model serving use cases is low-latency prediction in real time on a sustained basis. For this use case, you should consider the `real-time inference` option from the SageMaker hosting service. SageMaker real-time inference provides multiple options for model hosting, including single-model hosting, multiple-model hosting in a single container behind one endpoint, and multiple-model hosting using different containers behind one endpoint.

*   Sometimes, you have models that are used for intermittent predictions with idle periods between traffic bursts. For this type of requirement, you can consider the `Serverless` option from the SageMaker hosting service. The key benefit of using Serverless Inference is the removal of infrastructure configuration and management overhead. It is also more cost effective since you don’t need to pay for infrastructure when it is not used, unlike real-time inference, where you need to pay for the infrastructure whether there is inference traffic or not. However, there might be a delay caused by cold-starts with Serverless Inference when the model is invoked for the first time or there is extended idle time between invocations to allow SageMaker Serverless Inference to launch instances.

*   Sometimes, the payload size of an inference can be very large, and it takes a long time to generate the prediction. In this case, a real-time endpoint won’t work due to the large payload size and extended time for the inference. For this type of use case, you can consider `the asynchronous inference` option of SageMaker hosting. Asynchronous inference queues the incoming requests and processes them asynchronously (as the name suggests). When using asynchronous inference, the input data and prediction output are stored in S3 instead of sending the payload and getting the response directly from the endpoint API. When the prediction is complete, you get a notification from the AWS SNS service.

*   Another model inference pattern is `batch inference`. This is when you have a large number of inferences to do, and they don’t need individual predictions to be generated and returned. For example, you might need to run a propensity-to-buy model for a large number of users and store the output in a database for downstream consumption. For this usage pattern, you can consider the SageMaker Batch Transform feature for model inference. Batch inference is also more cost effective as you only need to spin up the infrastructure when running the batch job.

Having discussed the various tasks involved in completing an ML project, ranging from data preparation to model deployment using the different SageMaker features, now let’s briefly talk about the need for automation. Data scientists frequently engage in iterative experimentation and model development, involving different datasets, new features, and various training scripts. Keeping track of configurations and model metrics for each run becomes essential. To streamline and automate these repetitive tasks, automation pipelines can be constructed, supporting various ML processes like data processing, model training, and model testing.

There are several tools available for automation and orchestration, including SageMaker’s Pipelines feature. It allows the creation of a `Directed Acyclic Graph` (`DAG`) to efficiently orchestrate and automate ML workflows. SageMaker Pipelines shares similarities with Airflow, an open-source workflow orchestration tool discussed in `Chapter 7`, `Open-Source ML Platforms`. 

Additionally, AWS Step Functions serves as an alternative option for building automated workflow orchestration, providing flexibility and scalability to accommodate diverse ML tasks. By leveraging these tools, data scientists can enhance efficiency, reproducibility, and organization in their ML workflows.

# Best practices for building a data science environment

Data science environments are meant for data scientists to perform quick experimentations using a wide range of ML frameworks and libraries. The following are some best practices to follow when providing such an environment for your data scientists:

*   `Run large-scale model training using the SageMaker Training service instead of Studio notebooks`: SageMaker Studio notebooks are meant for quick experimentation with small datasets. While it is possible to provision large EC2 instances for certain large model training jobs, it is not cost effective to always keep a large EC2 instance running for a notebook all the time.

*   `Abstract infrastructure configuration details from data scientists`: There are many infrastructure configurations to consider when using SageMaker, such as networking configuration, IAM roles, encryption keys, EC2 instance types, and storage options. To make the lives of data scientists easier, abstract these details away from the data scientists. For example, instead of having the data scientists enter specific networking configurations, have those details stored as environment variables or custom SDK options for data scientists to choose from.

*   `Create self-service provisioning`: To prevent provisioning bottlenecks, consider building a self-service provisioning capability to streamline user onboarding. For example, use AWS Service Catalog to create an ML product for automated user onboarding.

*   `Use Studio notebook local mode for quick model training job testing`: SageMaker has support for local mode, meaning you can mimic running training jobs locally in your Studio notebook. With SageMaker Training jobs, there is an overhead of spinning up separate infrastructure. Running these tests locally can help speed up experimentation.

*   `Set up guardrails`: This helps prevent data scientists from making mistakes such as using the wrong instance types for model training or forgetting to use data encryption keys. You can use AWS service control policies to help with guardrail management.

*   `Clean up unused resources`: Regularly review and clean up unused notebooks, endpoints, and other resources to avoid unnecessary costs.

*   `Use Spot instances`: For cost optimization, consider using Amazon EC2 Spot Instances for training jobs if possible. Spot instances can significantly reduce training costs while maintaining high performance. However, since Spot instances can be taken away unexpectedly, it is important to enable training checkpoints, so training can resume at the last checkpoint instead of restarting training from the beginning.

*   `Use built-in algorithms and managed containers for training`: SageMaker provides a list of built-in algorithms for different ML tasks and managed training containers for different ML frameworks. Taking advantage of these pre-existing resources can substantially reduce the engineering effort required, eliminating the need to build your own algorithms from scratch.

*   `Build automated pipelines for repeatable ML experimentation, model building, and model testing`: Having an automated pipeline can greatly reduce the manual effort and improve the tracking of different experiments. Consider different orchestration technology options based on your technology standards and preferences.

By adhering to these best practices, you can make the most of SageMaker Studio’s capabilities, streamline your ML workflows, and ensure cost-effective and secure usage of the platform.

# Hands-on exercise – building a data science environment using AWS services
