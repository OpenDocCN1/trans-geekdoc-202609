
This feature comes really handy if you consider how frequently a ML model gets updated and continuously evaluated for performance. A new version of a model may be created as a result of training on more recent data, hyperparameter tuning (with Amazon SageMaker AI AMT, for example), improving feature selection, or using better instances and inference containers. You can leverage production variants to compare your models and choose the best-performing candidate to respond to inference requests.

With Amazon SageMaker AI multivariant endpoints, you can distribute endpoint invocation requests across multiple production variants by providing the traffic distribution for each variant, or you can invoke a specific variant directly for each request. In this section, we look at these methods for deploying and testing ML models.

## Blue/Green Deployment

Blue/Green deployment is a strategy that reduces the risk and downtime associated with deploying new versions of a model. In Amazon SageMaker AI, this approach can be effectively implemented by leveraging the production variant concept you just learned, which allows seamless traffic shifting between different model versions or configurations. By carefully controlling the traffic flow, you can ensure that users experience minimal disruption while you validate the performance and stability of the new model version.

Before going into more details, let's level set on a few terms you need to know for the exam and constitute the basis of this strategy. In the Blue/Green deployment strategy, the *blue fleet* refers to the compute infrastructure where the existing model version is serving live traffic. The *green fleet*, on the other hand, is the compute infrastructure that hosts the new model version you want to deploy. The goal is to shift traffic from the blue fleet to the green fleet in a controlled manner, ensuring that the new model performs well under real-world conditions before fully replacing the old one. By using this approach, you can minimize downtime and mitigate the risk of introducing issues with the new deployment.

Before fully transitioning to the new model, the new model version undergoes rigorous testing and validation to ensure its performance and reliability. During this interval—referred to as the *baking period*—the new model (deployed on the green fleet) is monitored while serving live traffic. This will ensure that it performs as expected, in accordance to performance metrics you established. Once the green fleet starts receiving live traffic, the baking period begins. To accomplish this, CloudWatch alarms must be properly configured to continuously monitor key performance metrics and the behavior of the new model. The baking period allows you to detect any issues early and address them before directing more traffic to the new model. This additional validation step is essential to maintaining service quality and minimizing the risk of disruptions.

The term *traffic shifting mode* denotes the pattern of ingress traffic you want your Amazon SageMaker AI endpoint to use while distributing inference requests between the blue fleet and the green fleet.

Last, *auto-rollbacks* indicate the Amazon CloudWatch alarms Amazon SageMaker AI uses to monitor how the new version of your model performs on the (containers hosted on the) green fleet.

In the next three sections, the three traffic-shifting modes you need to know for the exam are explained: namely, All At Once, Canary, and Linear.

### All at Once

When implementing *All At Once* traffic shifting, Amazon SageMaker AI directs 100% of the traffic to the new fleet (green fleet). As soon as the green fleet starts serving traffic, the baking period begins. This period is a predetermined interval during which Amazon CloudWatch alarms monitor the green fleet's performance. If no alarms are triggered during this time, Amazon SageMaker AI removes the old fleet (blue fleet). However, if any alarms are activated, an automatic rollback is initiated, redirecting 100% of the traffic back to the blue fleet.

[Figure 6.7](#c006.xhtml#c06-fig-7) illustrates the All At Once traffic-shifting mode.

![FIGURE 6.7 Blue/Green deployment with All At Once traffic-shifting mode.](images/c06f007.png)

[FIGURE 6.7](#c006.xhtml#rc06-fig-7) Blue/Green deployment with All At Once traffic-shifting mode.

In [Figure 6.7,](#c006.xhtml#c06-fig-7) we want to deploy a new version of our model named `Model_v2`. In the beginning the current version of the model, `Model_v1`, is serving live production traffic. Ingress traffic is initiated by an Amazon SageMaker AI client, which uses the `invoke_endpoint` boto3 API to get inferences from `Model_v1` hosted in the blue fleet. To learn more about this API, visit `https://boto3.amazonaws.com/v1/documentation/api/1.35.9/reference/services/sagemaker-runtime/client/invoke_endpoint.html`.

As you can see in [Figure 6.7](#c006.xhtml#c06-fig-7), the endpoint has a configuration that contains two production variants, the first one for `Model_v1` and the second one for `Model_v2`. This is the Blue/Green Create step in the process.

Then we change the traffic pattern by redirecting all live traffic to `Model_v2`. This is when the baking period begins. To implement this step, we use the `update_endpoint` boto3 API with the following snippet:

```
import boto3
client = boto3.client("sagemaker")
    
response = client.update_endpoint(
  EndpointName="<your-endpoint-name>",
  EndpointConfigName="<your-config-name>",
  DeploymentConfig={
      "BlueGreenUpdatePolicy": {
          "TrafficRoutingConfiguration": {
              "Type": "ALL_AT_ONCE"
          },
          "TerminationWaitInSeconds": 600,
          "MaximumExecutionTimeoutInSeconds": 1800
      },
      "AutoRollbackConfiguration": {
          "Alarms": [
              {
                  "AlarmName": "<your-cw-alarm>"
              },
          ]
      }
  }
)
```

In the snippet, the parameter `MaximumExecutionTimeoutInSeconds` sets the maximum amount of time that the deployment can run before it times out (30 minutes in this example). The parameter `TerminationWaitInSeconds` tells Amazon SageMaker AI to wait for the specified amount of time (in seconds) after your green fleet is fully active before terminating the instances in the blue fleet. In this example, Amazon SageMaker AI waits for 10 minutes after the final baking period before terminating the blue fleet.

For a detailed syntax of the `update_endpoint` API call, visit `https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sagemaker/client/update_endpoint.html`.

The effect of the `update_endpoint` API call is the new endpoint configuration shown in the middle of [Figure 6.7](#c006.xhtml#c06-fig-7).

In the best-case scenario, no alarms are triggered during the baking period, resulting in a termination of the blue fleet. Otherwise, an auto-rollback initiates, and 100% of the traffic shifts back to the blue fleet.

### Canary

In a Canary deployment with Amazon SageMaker AI, the traffic shifting is more gradual compared to the All At Once approach. Initially, a small portion of the traffic deemed feasible is directed to the new fleet (green fleet), and the majority continues to be directed to the old fleet (blue fleet). This initial phase is called the "canary test." If the new fleet performs well during the canary test without triggering any Amazon CloudWatch alarms, traffic is gradually increased to the new fleet in additional steps until it reaches 100%. This method allows for closer monitoring of the new version in a production environment and reduces the risk of introducing issues by catching potential problems early with a smaller subset of users.

The approach to implement a Canary deployment programmatically is similar to the All At Once, as shown in the following snippet:
