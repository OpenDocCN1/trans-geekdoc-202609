Target Tracking Scaling Policies: Our recommendation is to leverage target tracking scaling policies. Here, you select a CloudWatch metric and set a target value. Auto scaling takes care of creating and managing CloudWatch alarms, adjusting the number of instances to maintain the metric close to the specified target value. For instance, a scaling policy targeting the InvocationsPerInstance metric with a target value of 70 ensures the metric hovers around that value.

Step Scaling Policies: Step scaling is for advanced configurations, allowing you to specify instance deployment under specific conditions. However, for simplicity and full automation, target tracking scaling is preferred. Note that step scaling is managed exclusively through the AWS CLI or Application Auto Scaling API.

Creating a target tracking scaling policy involves specifying the metric, such as the average number of invocations per instance, and the target value, for example, 70 invocations per instance per minute. You have the flexibility to create target tracking scaling policies based on predefined or custom metrics. Cooldown periods, which prevent rapid capacity fluctuations, can also be configured optionally.

# Scale Based on a Schedule

Scheduled actions enable scaling activities at specific times, either as a one-time event or on a recurring schedule. These actions can work in tandem with your scaling policy, allowing dynamic decisions based on changing workloads. Scheduled scaling is managed exclusively through the AWS CLI or Application Auto Scaling API.

# Minimum and Maximum Scaling Limits

Before crafting a scaling policy, it’s essential to set minimum and maximum scaling limits. The minimum value, set to at least 1, represents the minimum number of instances, while the maximum value signifies the upper cap. SageMaker auto scaling adheres to these limits and automatically scales in to the minimum specified instances when traffic becomes zero.

You have three options to specify these limits:

+   • Use the console to update the Minimum instance count and Maximum instance count settings.

+   • Use the AWS CLI, including the --min-capacity and --max-capacity options with the register-scalable-target command.

+   • Call the RegisterScalableTarget API, specifying the MinCapacity and MaxCapacity parameters.

# Cooldown Period