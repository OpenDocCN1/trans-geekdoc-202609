• VPC accessible services to constrain Google Cloud APIs (services) are accessible from a VPC network.

Now let us take a look at how VPC Service Controls can be used for API access restriction.

![](bbox=[0.191, 0.189, 0.81, 0.517])

Figure 10.10 – Control APIs

As shown in Figure 10.10, VPC Service Controls allows you to control which APIs can be accessed from within the service perimeter:

+   - Private Google Access or Private Service Connect: privately access Google Cloud APIs using Private Google Access.

+   - restricted.googleapis.com: Limit access to Google Cloud services that can be isolated with VPC Service Controls using the restricted Virtual IP (VIP) address range. To allow access to Cloud and Developer APIs protected by VPC Service Controls, use restricted.googleapis.com. The restricted.googleapis.com domain resolves to the 199.36.153/30 VIP range. The internet does not have access to this IP address range. The restricted.googleapis.com denies access to Google APIs and services that are not supported by VPC Service Controls.

+   - VPC accessible services: Specify the exact list of APIs that can be accessed from a VPC.

Now we have seen how to restrict API access, let us see how we can allow access to the APIs within the perimeter.