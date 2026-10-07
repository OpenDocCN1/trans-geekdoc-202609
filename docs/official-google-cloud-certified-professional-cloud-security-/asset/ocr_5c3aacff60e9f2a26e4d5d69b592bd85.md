Based on your requirements, you can choose either of them. VPC comes with routing where you have the next hop already configured, and that is the default internet gateway. The VMs have the default internet gateway, where the packets are sent when the VM inside VPC sends a request to the Google APIs. Although the term default internet gateway suggests that all traffic is sent to the internet, it is not true. The default internet gateway routes traffic from VPCs to Google APIs within Google's network. Google does not allow routing traffic to Google APIs and services through other VPC instances or custom hops.

If your VPC has a default route pointing towards the default internet gateway, you can route all requests from your VM to the Google APIs and services without configuring custom routes.

You can create a custom route and define the next hop in case where you want to direct the traffic to Cloud VPN or an internal load balancer. In those cases, you can define a custom route with the next relevant hop.

# Routing using a default route

Follow these steps to route using a default route:


+   1. Go to the Routes page in the Google Cloud console.
2. Select Network Menu and Routes under the VPC sub-menu.

Here you have the ability to filter the list of routes to show just the routes for the network you need to inspect (Figure 8.3).

![](bbox=[0.138, 0.526, 0.849, 0.73])

Look for a route whose destination is 0. 0. 0. 0/0 and whose next hop is Default Internet gateway.

# Routing using custom routes

Follow these steps to using custom routes:

+   1. On the same Routes page in the Google Cloud console, use the Filter table text field to filter the list of routes using the following criteria: