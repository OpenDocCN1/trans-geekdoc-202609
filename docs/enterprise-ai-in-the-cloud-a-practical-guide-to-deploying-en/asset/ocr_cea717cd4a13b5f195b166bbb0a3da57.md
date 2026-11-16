![](bbox=[0.12, 0.08, 0.88, 0.39])

# FIGURE 19.5: Implementing a recoverable endpoint

> TIP Plan for scale and prepare for the unexpected and leverage tools to automate pipelines, control versions, centralize components, track lineage, and adopt autoscaling.

# Implementing Autoscaling for the Model Endpoint

As you start taking more and more workload, ensuring that your model endpoint can serve customers with the same quality of service is essential. You can achieve this by implementing autoscaling of your model endpoint.

# Configure Automatic Scaling Using SageMaker Endpoint

SageMaker Endpoint can automatically increase or decrease the number of EC2 instances attached to the model endpoint based on the workload or the number of inference requests. The advantage of this approach is that there is no need for manual intervention.

# Leverage Amazon Elastic Inference

Another thing that you can do is, in addition to configuring the right-sized EC2 instances with the required CPU and memory power, is