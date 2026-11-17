# # Network mapping Info

The load balancer routes traffic to targets in the selected subnets, and in accordance with your IP address settings.

# ## VPC Info

Select the virtual private cloud (VPC) for your targets. Only VPCs with an internet gateway are enabled for selection. The selected VPC cannot be changed after the load balancer is created. To confirm the VPC for your targets, view your target groups .

```
vpc-0794b53ffdc52faed4
IPv4: 172.31.0.0/16
```

# ## Mappings Info

Select at least two Availability Zones and one subnet per zone. The load balancer routes traffic to targets in these Availability Zones only. Availability Zones that are not supported by the load balancer or the VPC are not available for selection.

+   - us-west-2a
+     - Subnet: subnet-08c67a67021afa335
+     - IPv4 settings: Assigned by AWS
+   - us-west-2b

Figure 13.31: Application Load Balancer–Network mapping

After that, remove the default security group and choose the security group from the dropdown created in the previous section. A security group can also be created through the Create new security group link. It will take you to the main page of the security group only, as seen in the previous section. The following figure shows the security group mlapp-lb-sg chosen for the load balancer:

# # Security groups Info

A security group is a set of firewall rules that control the traffic to your load balancer.

+   Select up to 5 security groups
+   mlapp-lb-sg sg-0615e0e759807c03f
+   VPC: vpc-0794b53ffdc52faed4

Figure 13.32: Application Load Balancer–Security groups