# # Create cluster

An Amazon ECS cluster is a logical grouping of tasks or services.

# ### Cluster configuration

Cluster name
mlapp-cluster
There can be a maximum of 255 characters. The valid characters are letters (uppercase and lowercase), numbers, hyphens, and underscores.

Figure 13.13: Amazon Elastic Container Service (ECS)—Cluster configuration

Then, click on the **Create** button, and it will launch the ECS cluster. You will see ECS cluster is created with the type Fargate, but no instances are running.

# # Task definition

After that, create a task definition. Go to the **Task Definition** page and click on **Create new Task Definition**. Choose the type as **Fargate** in step 1. In step 2, provide the task definition name. In this case, it is **mlapp-cicd**. Select the **Task role ecsTaskExecutionRole** from the dropdown and select the **Operating system family** as **Linux**, as shown in the following figure:

Step 1: Select launch type compatibility
Step 2: Configure task and container definitions
Configure task and container definitions
A task definition specifies which containers are included in your task and how they interact with each other. You can also specify data volumes for your containers to use. Learn more
Task definition name* mlapp-cicd
Requires compatibilities* FARGATE
Task role ecsTaskExecutionRole
Network mode awsvpc
Operating system family Linux

Figure 13.14: Amazon Elastic Container Service (ECS)—task definition