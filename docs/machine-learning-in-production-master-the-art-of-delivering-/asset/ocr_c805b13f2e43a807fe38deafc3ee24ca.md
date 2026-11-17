![](bbox=[0.4, 0.1, 0.6, 0.18])

Figure 13.19: AWS-Load Balancing

Let's understand the role and configuration of the two components of Load Balancing.

# # Target group

With a load balancer, a single DNS name is enough to access the containerized application. A load balancer will take the user requests on port **80** and route them to tasks with dynamic IP through the service. The target group will ensure connectivity between the load balancer and tasks with dynamic IP through service.

Go to the target group and create a new target group by hitting the **Create target group** button.

Creating a target is a three-step process:

+   - Specify group details
+   - Register targets
+   - Review IP targets to include in your group

# ## Step 1: Specify group details

A configuration setting cannot be changed after the creation of a target group. In this step, the target type is **IP addresses**; its features are listed in the following figure:

![](bbox=[0.23, 0.62, 0.77, 0.92])

Figure 13.20: Target Groups—Specify group details