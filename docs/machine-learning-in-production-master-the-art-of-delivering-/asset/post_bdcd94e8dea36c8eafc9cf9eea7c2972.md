
## Step 3: Review IP targets to include in your group

At this point, you can repeat steps 1 and 2 if you want to add additional IP targets. However, you have not specified any IP address is specified in step 2, so go ahead and hit the Create target group button at the bottom. It will take you back to the main page of the targets group and display a successful message, as shown in the following figure:

![](img/cc4299656808e62a294f1843a1e18e72_380_0.png)

Figure 13.24: Target Groups–mlapp-tg

Amazon Resource Names (ARNs) are unique identifiers of AWS resources. AWS ARN format could be any one of the following formats:

- arn:partition:service:region:account-id:resource-id
- arn:partition:service:region:account-id:resource-type/resource-id
- arn:partition:service:region:account-id:resource-type:resource-id

A partition is a group of AWS regions, and each account has a limited scope: one partition.

## Security Groups

A security group is a set of firewall rules that control the traffic toward the load balancer. It has not been created yet, so let's go ahead and create a new security group. Follow these steps:

Services | All Services | EC2 | Network & Security | Security Groups

First off, specify basic details for the security group, such as name and description, as shown in the following figure. A Security group name is mlapp-lb-sg, where lb stands for the load balancer and sg stands for the security group.

### Create security group

A security group acts as a virtual firewall for your instance to control inbound and outbound traffic. To create a new security group, complete the fields below.

### Basic details

Figure 13.25: Security Group for load balancer—Create a security group

Next, configure inbound rules for the security group. Hit the Add rule button. A load balancer should be able to access port 80 from anywhere, so specify port 80 under the Port range and choose Source type as anywhere, as shown in the following figure. More rules can be added through the Add rule button.

### Inbound rules

Figure 13.26: Security Group for load balancer—Inbound rules

Then, hit the Create security group button in the bottom-right corner of the page and complete the process. The following figure shows the details of the security group after creation:

![](img/cc4299656808e62a294f1843a1e18e72_382_0.png)

Figure 13.27: Security Group for load balancer–mlapp-lb-sg

This security group, mlapp-lb-sg will be used for the load balancer.

## Application Load Balancers (ALB)

Application Load Balancer (ALB) accepts incoming requests and routes them to registered targets, such as EC2 instances. It also checks the health of its registered targets (by default, the root path is set to '/'; however, it can be changed to a different path of application). Application Load Balancer (ALB) is client-facing. It routes the traffic to healthy targets only. It can be easily integrated with Amazon Elastic Container Service (Amazon ECS), Amazon Elastic Container Service for Kubernetes (Amazon EKS), AWS Fargate, and AWS Lambda.

Once security and target group is created, create a load balancer. Go to the Load balancing section again and choose Load Balancers.

Services | All Services | EC2 | Load balancing | Load Balancers

Then, hit the Create Load Balancer button. The following figure shows the main page of the load balancer:

![](img/cc4299656808e62a294f1843a1e18e72_383_0.png)

Figure 13.28: Application Load Balancer–Create Load Balancer

After clicking the Create Load Balancer button, it will show three options with brief descriptions and architecture to choose from, as shown in the following figure:

![](img/cc4299656808e62a294f1843a1e18e72_383_1.png)

Figure 13.29: Application Load Balancer–Select load balancer type

The application load balancer distributes the incoming requests across targets, such as containers, microservices, and EC2 instances, depending on the requests. Before passing the incoming requests to the targets, it evaluates whether the listeners’ rules are configured.

In the current scenario, choose the first type, which is Application Load Balancer, by hitting the Create button.

Now, configure the load balancer. First, specify the name for the load balancer mlapp-lb, where lb stands for the load balancer. Next, choose the scheme as Internet-facing. The main difference between the Internet-facing and the Internal scheme is the internet. An Internet-facing load balancer routes the requests coming from clients over the internet to specified targets. On the other hand, an Internal load balancer will only route the request from clients with private IPs to specified targets. Select the IP address type as IPv4, which is used by specified subnets. The following figure shows the basic configuration of the Application Load Balancer:

EC2 > Load balancers > Create Application Load Balancer

### Create Application Load Balancer

The Application Load Balancer distributes incoming HTTP and HTTPS traffic across multiple targets such as Amazon EC2 instances, microservices, and containers, based on request attributes. When the load balancer receives a connection request, it evaluates the listener rules in priority order to determine which rule to apply, and if applicable, it selects a target from the target group for the rule action.

### How Application Load Balancers work

### Basic configuration

Load balancer name
Name must be unique within your AWS account and cannot be changed after the load balancer is created.
mlapp-lb
A maximum of 32 alphanumeric characters including hyphens are allowed, but the name must not begin or end with a hyphen.

Scheme cannot be changed after the load balancer is created.

| Scheme | Info |
|--------|------|
| Internet-facing | An internet-facing load balancer routes requests from clients over the internet to targets. Requires a public subnet. Learn more |
| Internal | An internal load balancer routes requests from clients to targets using private IP addresses. |

Figure 13.30: Application Load Balancer–Basic configuration

Then, configure the network mapping. Network mapping enables the load balancer to route incoming requests to specific subnets and IP addresses. For mapping, select at least two availability zones and one subnet per zone where the load balancer can route the traffic. By default, it will display the available zones for selection. A load balancer will route the requests to targets in these availability zones only. Choose the default VPC and two Subnet (2a and 2b) from the dropdown, as shown in the following figure:

### Network mapping Info

The load balancer routes traffic to targets in the selected subnets, and in accordance with your IP address settings.

### VPC Info

Select the virtual private cloud (VPC) for your targets. Only VPCs with an internet gateway are enabled for selection. The selected VPC cannot be changed after the load balancer is created. To confirm the VPC for your targets, view your target groups .

```
vpc-0794b53ffdc52faed4
IPv4: 172.31.0.0/16
```

### Mappings Info

Select at least two Availability Zones and one subnet per zone. The load balancer routes traffic to targets in these Availability Zones only. Availability Zones that are not supported by the load balancer or the VPC are not available for selection.

- us-west-2a
  - Subnet: subnet-08c67a67021afa335
  - IPv4 settings: Assigned by AWS
- us-west-2b

Figure 13.31: Application Load Balancer–Network mapping

After that, remove the default security group and choose the security group from the dropdown created in the previous section. A security group can also be created through the Create new security group link. It will take you to the main page of the security group only, as seen in the previous section. The following figure shows the security group mlapp-lb-sg chosen for the load balancer:

### Security groups Info

A security group is a set of firewall rules that control the traffic to your load balancer.

- Select up to 5 security groups
- mlapp-lb-sg sg-0615e0e759807c03f
- VPC: vpc-0794b53ffdc52faed4

Figure 13.32: Application Load Balancer–Security groups
