
# Autoscaling Amazon SageMaker AI Endpoints

Autoscaling Amazon SageMaker AI endpoints ensures that your deployed ML models can handle varying levels of traffic efficiently by scaling horizontally (scale-in, scale-out) the instances responsible for serving incoming inference requests. Amazon Application Auto Scaling allows you to automatically adjust the number of instance replicas for your Amazon SageMaker AI endpoints based on predefined metrics, such as CPU utilization or request count. This helps in maintaining optimal performance while keeping costs under control. To begin with, you need to configure your endpoint with an autoscaling policy using the `application-autoscaling boto3` client.

## Creating an Autoscaling Policy for a Real-Time Endpoint

First, let’s create an autoscaling policy for a real-time endpoint. To do so, you need to define two components:

*   A **scaling target**: Sets the boundaries for scaling (e.g., minimum 1 instance, maximum 10 instances)
*   A **scaling policy**: Specifies the metric to monitor (e.g., `SageMakerVariantInvocationsPerInstance` or `CPUUtilization`), the target value for this metric, and the conditions under which to scale in or out

Here’s a simple example in Python to illustrate this:

```python
import boto3

client = boto3.client('application-autoscaling')

# Register a scalable target
response = client.register_scalable_target(
    ServiceNamespace='sagemaker',
    ResourceId='endpoint/your-endpoint-name/variant/AllTraffic',
    ScalableDimension='sagemaker:variant:DesiredInstanceCount',
    MinCapacity=1,
    MaxCapacity=10
)

# Create a scaling policy
response = client.put_scaling_policy(
    PolicyName='ScalingPolicy',
    ServiceNamespace='sagemaker',
    ResourceId='endpoint/your-endpoint-name/variant/AllTraffic',
    ScalableDimension='sagemaker:variant:DesiredInstanceCount',
    PolicyType='TargetTrackingScaling',
    TargetTrackingScalingPolicyConfiguration={
        'TargetValue': 70.0,  # Target number of endpoint invocations per instance
        'PredefinedMetricSpecification': {
            'PredefinedMetricType': 'SageMakerVariantInvocationsPerInstance',
        },
        'ScaleInCooldown': 300,
        'ScaleOutCooldown': 300
    }
)
```

In this example, autoscaling is triggered based on the number of invocations (requests) per instance for your Amazon SageMaker AI endpoint. Specifically, the scaling policy is set to maintain an average of 70 invocations per instance. If the average number of invocations per instance goes above 70, the policy will automatically add more instances (scale out) to handle the increased load. Conversely, if the average number of invocations per instance drops below 70, the policy will reduce the number of instances (scale in) to optimize resource usage. This “elastic” behavior ensures that your real-time inference endpoint can dynamically adapt to changing traffic levels, maintaining performance and efficiency.

The `ScaleInCooldown` and `ScaleOutCooldown` parameters define the cool down period in seconds for scaling in and scaling out actions, respectively. In this case, both are set to 300 seconds (5 minutes). When a scaling action is triggered, such as adding more instances (scaling out) or reducing instances (scaling in), the cooldown period ensures that no further scaling actions of the same type can be taken until the cooldown period has elapsed. This helps prevent rapid and excessive scaling actions in response to short-term fluctuations in traffic, ensuring that the system has sufficient time to stabilize before considering another scaling adjustment.

## Scaling Based on CPU Utilization

Let’s look at another example where we scale based on CPU utilization. We can modify the scaling policy to use a custom metric, such as average CPU utilization. Here’s how you can achieve this:

```python
import boto3

client = boto3.client('application-autoscaling')

# Register a scalable target
response = client.register_scalable_target(
    ServiceNamespace='sagemaker',
    ResourceId='endpoint/your-endpoint-name/variant/AllTraffic',
    ScalableDimension='sagemaker:variant:DesiredInstanceCount',
    MinCapacity=1,
    MaxCapacity=10
)

# Create a scaling policy
response = client.put_scaling_policy(
    PolicyName='CPUScalingPolicy',
    ServiceNamespace='sagemaker',
    ResourceId='endpoint/your-endpoint-name/variant/AllTraffic',
    ScalableDimension='sagemaker:variant:DesiredInstanceCount',
    PolicyType='TargetTrackingScaling',
    TargetTrackingScalingPolicyConfiguration={
        'TargetValue': 50.0,  # Target average CPU utilization
        'CustomizedMetricSpecification': {
            'MetricName': 'CPUUtilization',
            'Namespace': 'AWS/SageMaker',
            'Dimensions': [{'Name': 'EndpointName', 'Value': 'your-endpoint-name'}],
            'Statistic': 'Average',
            'Unit': 'Percent'
        },
        'ScaleInCooldown': 300,
        'ScaleOutCooldown': 300
    }
)
```

In this second example, autoscaling is triggered based on the average CPU utilization of the instances running the Amazon SageMaker AI endpoint. The scaling policy is set to maintain an average CPU utilization of 50%. If the average CPU usage across the instances exceeds 50%, the policy will automatically add more instances (scale out) to handle the increased load. Conversely, if the average CPU usage drops below 50%, the policy will reduce the number of instances (scale in) to optimize resource usage. The cooldown periods ensure that these scaling actions are not triggered too frequently, allowing the system to stabilize before making further adjustments.

These two programs demonstrate the use of Amazon Application Auto Scaling—**Target Tracking** autoscaling, specifically—to “elastically” adjust the number of instances for your Amazon SageMaker AI endpoints, ensuring optimal performance, reliability, and cost efficiency.

## Considerations for Multi-Model and Multi-Container Endpoints

Amazon Application Auto Scaling is fully supported by MMEs and MCEs. In the latter use case (MCEs), use caution. If you want to configure automatic scaling for an MCE using the `InvocationsPerInstance` metric, make sure the model in each container exhibits similar CPU utilization and latency on each inference request. This is best practice because if traffic to the MCE shifts from a low-CPU-utilization model to a high-CPU-utilization model, but the overall volume of invocations remains the same, the endpoint will not scale out. This will result in an insufficient number of instances to handle all the requests to the high CPU utilization model.

## Understanding ResourceId and Variants

Notice how both examples denote the real-time inference endpoint with the `ResourceId` variable, whose value is set to `endpoint/your-endpoint-name/variant/AllTraffic`. The term *variant* refers to different versions or configurations of the model deployed to the same Amazon SageMaker endpoint. This concept allows for multiple variants within the same endpoint, each potentially having different instance types, counts, or even different model versions. By specifying the suffix `variant/AllTraffic`, we apply the autoscaling policy to all the traffic directed to the endpoint. You can also define specific named variants (e.g., `variant/VersionA`), enabling you to manage and scale different model versions independently. This flexibility is especially useful for tasks such as Blue/Green deployments, shadow testing, or canary testing when deploying new model updates, which will be discussed in the next section.

# Deployment and Testing Strategies

A key aspect of any deployment strategy is to minimize downtime to the consumers of your models (or applications). To avoid disrupting service for users while updating to a new, or an improved, model, you can take advantage of Amazon SageMaker AI’s **production variants** feature.
