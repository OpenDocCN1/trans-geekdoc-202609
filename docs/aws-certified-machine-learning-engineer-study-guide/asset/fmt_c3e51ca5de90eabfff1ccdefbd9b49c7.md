
```
import boto3
client = boto3.client("sagemaker")

response = client.update_endpoint(
    EndpointName="<your-endpoint-name>",
    EndpointConfigName="<your-config-name>",
    DeploymentConfig={
        "BlueGreenUpdatePolicy": {
            "TrafficRoutingConfiguration": {
                "Type": "CANARY",
                "CanarySize": {
                    "Type": "CAPACITY_PERCENT",
                    "Value": 30
                },
                "WaitIntervalInSeconds": 600
            },
            "TerminationWaitInSeconds": 600,
            "MaximumExecutionTimeoutInSeconds": 1800
        },
        "AutoRollbackConfiguration": {
            "Alarms": [
                {
                    "AlarmName": "<your-cw-alarm>"
                }
            ]
        }
    }
)
```

The `update_endpoint` API allows you to set the `Type` parameter of the `TrafficRoutingConfiguration` dictionary to the value `CANARY`. The `Value` parameter of the `CanarySize` dictionary sets the percentage of your green fleet you want to use as the canary. In the example, we configured the endpoint to shift 30% of the ingress traffic to the green fleet. We could have chosen to direct traffic to the green fleet based on `INSTANCE_COUNT` instead of `CAPACITY_PERCENT`, which is another valid option for `Type`.

The `WaitIntervalInSeconds` parameter denotes the duration (in seconds) of the canary baking period. In the preceding example, Amazon SageMaker AI waits for 10 minutes after the canary shift and then completes the second and final traffic shift.

When comparing Canary with All At Once, it is important to remember that the All At Once approach shifts 100% of the traffic to the green fleet in a single step as soon as the deployment starts. Although this method is faster, it carries higher risk because any undetected issues in the new fleet can affect all users immediately. All At Once relies heavily on extensive predeployment testing and a robust rollback plan, as the entire user base is exposed to the new version immediately.

As a result, the key difference between the two approaches lies in the risk management and traffic transition speed. Canary deployments provide a safer, more controlled rollout by gradually increasing traffic and monitoring each phase for stability, whereas All At Once deployments prioritize speed and immediate transition but come with higher risks. Choosing between these methods depends on your application's tolerance for risk and the criticality of ensuring seamless, uninterrupted user experience.

### Linear

The linear Blue/Green deployment option provides the most granular control over traffic shifting. Instead of deploying your green fleet in one step (All At Once) or in two steps (Canary), linear traffic shifting gradually directs traffic from the blue fleet to the green fleet in small, equal increments over a specified period.

Just like Canary traffic shifting, you can choose the increment size by specifying the number of instances or the percentage (10–50%) of the green fleet's capacity to activate during each phase.

For each phase of the deployment, you define a baking period where your preconfigured Amazon CloudWatch alarms monitor the green fleet's metrics. If the baking period concludes without any alarms being triggered, the green fleet continues to receive a greater share of traffic as the process moves to the next phase. Should any alarms go off during any of these baking periods, all the endpoint traffic will immediately revert to the blue fleet.

The following example shows how to implement the linear traffic-shifting pattern using the `update_endpoint` API:

```
import boto3
client = boto3.client("sagemaker")

response = client.update_endpoint(
    EndpointName="<your-endpoint-name>",
    EndpointConfigName="<your-config-name>",
    DeploymentConfig={
        "BlueGreenUpdatePolicy": {
            "TrafficRoutingConfiguration": {
                "Type": "LINEAR",
                "LinearStepSize": {
                    "Type": "CAPACITY_PERCENT",
                    "Value": 20
                },
                "WaitIntervalInSeconds": 300
            },
            "TerminationWaitInSeconds": 300,
            "MaximumExecutionTimeoutInSeconds": 3600
        },
        "AutoRollbackConfiguration": {
            "Alarms": [
                {
                    "AlarmName": "<your-cw-alarm>"
                }
            ]
        }
    }
)
```

The approach is similar to the Canary deployment. The `TrafficRoutingConfiguration` dictionary allows you to set a `Type` parameter with a value `LINEAR` and a corresponding configuration `LinearStepSize` where you can specify how to incrementally route more traffic to the green fleet. In our example, at each step we will direct live traffic to the green fleet in 20% increments (the parameter `CAPACITY_PERCENT` is set to 20). `INSTANCE_COUNT` can also be used as an alternative way to direct traffic to the green fleet. With linear traffic-shifting mode, as the name suggests, the amount of inference traffic routed to the green fleet increases in a linear fashion.

Notice how we also define a baking period for each step by assigning the value 300 to the `WaitIntervalInSeconds` parameter. In the example, Amazon SageMaker AI waits for 5 minutes between each traffic shift. If no alarms are triggered within 5 minutes, Amazon SageMaker directs 20% more traffic to the green fleet until 100% of traffic is sent to the new model. Upon completion—assuming no alarms are triggered—Amazon SageMaker AI waits for another 5 minutes (`TerminationWaitInSeconds` is set to 300) and finally terminates all the instances in the blue fleet. If an alarm is triggered in any of the five steps (0–20, 20–40, 40–60, 60–80, 80–100), Amazon SageMaker AI rolls back 100% of the endpoint traffic to the blue fleet.

The linear deployment offers the highest level of risk reduction during your model deployment process at the expense of potentially longer deployment times. This approach is perfect for critical deployments where stability and minimizing risk are essential, ensuring a smooth transition with ongoing monitoring and the ability to roll back if any issues arise.

## Orchestrating ML Workflows

You have learned so far how to ingest the data to train your ML models; engineer the relevant features; choose a suitable algorithm; train, refine, and optimize your model; and finally deploy it. These foundational steps are crucial in the ML lifecycle and set the stage for building robust and efficient models that can drive impactful insights and decisions.

However, orchestrating these steps manually can be time-consuming and prone to errors. This is where Amazon SageMaker AI's comprehensive suite of tools comes into play, providing an integrated environment to streamline and automate the entire ML workflow. By leveraging Amazon SageMaker AI, you can seamlessly manage data preprocessing tasks, engineer your features, and train, evaluate and deploy your model, all within a cohesive platform that enhances productivity and reduces complexity.

One of the standout features in this ecosystem is `Amazon SageMaker Pipelines`. This powerful tool enables the design, deployment, and management of end-to-end ML workflows with ease. Amazon SageMaker Pipelines comes with its own SDK, allowing you to define and visualize your workflows programmatically, ensuring consistency and repeatability, which are both key characteristics of modern ML operations.

In the upcoming sections you will learn Amazon SageMaker Pipelines' main capabilities you need to know for the exam.

### Introducing Amazon SageMaker Pipelines

In the rapidly evolving world of ML, operationalizing ML models—often referred to as `MLOps`—has become a cornerstone of successful AI-driven projects. MLOps bridges the gap between ML model development and production, ensuring seamless integration, deployment, monitoring, and maintenance of models.
