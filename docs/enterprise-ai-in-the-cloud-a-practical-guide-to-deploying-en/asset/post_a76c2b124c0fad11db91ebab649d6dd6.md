
- IBM Watson OpenScale provides a similar functionality.

## Open-Source Libraries

In this category, you have the following options:

- Evidently, Prometheus, with Grafana monitor model performance, data, and fairness.
- Amazon Deequ is a validation library for Apache Spark.
- Tensorboard tracks TensorFlow models.

## Third-Party Tools

A number of third-party tools such as Whylabs, Arize, Datadog, Monte Carlo, Labelbox, and Seldon are worth checking out.

> **TIP** _Choose cloud provider tools for scale, open-source tools for customizability, and third-party tools for an end-to-end integrated solution._

## BUILDING A MODEL MONITORING SYSTEM

You need to consider some things before deploying your model in production from a monitoring standpoint (see Figure 19.4).

### Decide on the Model Metrics

Monitor infrastructure health, endpoint responses, track model versions and data

### Set Up the Thresholds

Establish statistical, business, and adaptive thresholds

### Employ a Monitoring Service

Use monitoring services like Amazon CloudWatch and AWS Cost Profiler to track metrics

### Set Up Alerts

Configure alerts for issue detection

### Conduct Periodic Reviews

Perform regular checks and adjust metrics and thresholds

FIGURE 19.4: Monitoring the health of your endpoints

### Determining the Model Metrics to be Monitored

First, you must decide on the metrics you should monitor for your model endpoint once the model is deployed. You should do the following:

- Monitor metrics to measure the health of the infrastructure hosting the endpoint. The metrics used to measure the health of the underlying compute resources are memory and CPU/GPU usage, ML endpoint invocations, and latency.

> NOTE
> You can use Amazon SageMaker Model Monitor to monitor the quality of the models and send metrics data to CloudWatch.

- Monitor the health of the endpoint responses. The metrics used to monitor the model responses are the accuracy and number of errors in the model response. You can use Amazon SageMaker Clarify to identify bias and feature attribution drift.

- Track and trace these metrics to the model's version or the data used for these predictions.

### Setting Up the Thresholds for Monitoring

Thresholds determine whether a metric is acceptable within a specific range, and alerts are triggered when exceeded.

You can set statistical thresholds for triggering alerts if the average prediction accuracy over time falls below a certain percentage. You can also set business thresholds based on business impact, where the threshold level may vary depending on the criticality of the metric. In other cases, you might have an adaptive threshold, where the threshold varies depending on certain factors, such as the time of day.

Ensure you review the thresholds periodically because the models and data change and the thresholds may have to be changed accordingly.

### Employing a Monitoring Service with Dashboards

You must employ a monitoring service that provides dashboards and reports to track these metrics. For example, you can use Amazon CloudWatch to track the metrics of your SageMaker deployments. You can use Amazon EventBridge to automate event responses and AWS Cost Profiler to keep tabs on expenses.

### Setting Up Alerts

You should also set up alerts to be notified in case of an issue, such as increased memory utilization, a sudden increase in latency, and so on. Integrate them with other notification systems such as emails, SNS, SMS, and even Slack.

> TIP Ensure the alerts also have the necessary information as to what went wrong and possibly the root cause so that you can act on them.

### Conducting Periodic Reviews

Finally, conduct periodic reviews to ensure you have the right metrics and thresholds and make necessary changes as needed.

## MONITORING MODEL ENDPOINTS

Model endpoint best practices such as automating endpoint changes, implementing a recoverable endpoint, and autoscaling endpoints ensure models perform reliably and help identify opportunities to improve predictions, reduce costs, and avoid failures.

### Automating Endpoint Changes Through a Pipeline

Every time you change the model, you must manually deploy that change to the endpoint. It is an error-prone, time-consuming process. A better way to do that is to use a pipeline that does the following:

- Checks out the latest version of the model code
- Builds the model
- Deploys the model to the endpoint

By integrating the endpoint into the change management system, you can track every time a new model is deployed to the endpoint. When you face a problem during a deployment, you can roll back to the older version. This process is not only automatic, but it also reduces downtime. You could use a change control system such as Git and CI/CD pipeline management tools like Jenkins, GitLab, or AWS CodePipeline.

> TIP By automating the model deployment to the endpoint, you can eliminate the errors and reduce the downtime, which will reflect in the improved accuracy of your model, thus helping you achieve your business objectives.

### Implementing a Recoverable Endpoint

It is vital to have a recoverable endpoint and a solid version control strategy if your system goes down because of errors or any other reason. You must ensure all components relevant to the hosting model endpoint are version controlled and the relationships between these components are maintained in a lineage tracker system.

Maintaining all the versions will help you maintain backups of all these components, and maintaining the relationships will help you roll back when the situation demands. Figure 19.5 shows the different steps involved to implement a recoverable endpoint.

Consider how to achieve this using AWS services.

- You can implement **Amazon SageMaker Pipeline** to automate the development, training, and deployment of the models and switch between versions seamlessly.

- Using **SageMaker Projects**, you can enable collaboration between the data scientists and the developers by bringing all the necessary components to build an end-to-end ML solution under one umbrella. These components could include the pipeline executions, the registered models, the ML code, the datasets, and the endpoints.

- At the same time, we can use the **AWS CloudFormation** tool to manage the infrastructure as code to manage different versions of the infrastructure and revert to different versions if necessary. You can store the code in **AWS CodeCommit** repositories.

- You can use **Amazon's ECR** as a container registry to manage different versions of the containers and revert to different versions as needed.

- Finally, you can use **AWS SageMaker Lineage** to track the relationships between all these components and troubleshoot issues quickly.

![](img/1490b3cf638678afadc8c48abc1698d5_539_0.png)

FIGURE 19.5: Implementing a recoverable endpoint

> TIP Plan for scale and prepare for the unexpected and leverage tools to automate pipelines, control versions, centralize components, track lineage, and adopt autoscaling.

### Implementing Autoscaling for the Model Endpoint

As you start taking more and more workload, ensuring that your model endpoint can serve customers with the same quality of service is essential. You can achieve this by implementing autoscaling of your model endpoint.

### Configure Automatic Scaling Using SageMaker Endpoint

SageMaker Endpoint can automatically increase or decrease the number of EC2 instances attached to the model endpoint based on the workload or the number of inference requests. The advantage of this approach is that there is no need for manual intervention.

### Leverage Amazon Elastic Inference

Another thing that you can do is, in addition to configuring the right-sized EC2 instances with the required CPU and memory power, is configure Amazon's Elastic Inference, which helps the system choose the correct number of GPU-powered inference accelerations to serve the load.
