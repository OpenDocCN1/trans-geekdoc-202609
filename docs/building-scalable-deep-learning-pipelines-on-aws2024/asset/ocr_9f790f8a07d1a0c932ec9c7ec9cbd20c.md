Click “Create NAT gateway” as in Figure 10-7.

![](bbox=[0.1, 0.15, 0.9, 0.3])

+   * Select the public subnet where the NAT gateway will be created.
* Allocate an Elastic IP to the NAT gateway.
* For more details, refer to the AWS NAT gateways documentation:
https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html

+   * Update Route Tables:
    * Navigate to the Route tables section
    * Update the route tables of your private subnets to route Internet-bound traffic through the NAT gateway.
    * For more details, refer to the AWS “Configure route tables” documentation:
https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html