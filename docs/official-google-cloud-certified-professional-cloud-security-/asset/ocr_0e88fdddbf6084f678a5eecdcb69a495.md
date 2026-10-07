# Virtual Private Cloud

traffic will not traverse the internet and instead use Google's own operated and managed encrypted private network. This provides better reliability and security.

The Standard Tier option is what service providers use, that is, hot potato, meaning when a user tries to access the services hosted on Google Cloud, the service will go via the internet, which is non-deterministic and will not use Google's private network. This, although a more cost-effective option, does not provide the reliability, security, and availability of a Premium Tier network.

In the VPC deployment models section, where we will walk through the setup of VPC, we will highlight where you can configure the network tiers.

# Google Cloud regions and zones

This topic is not part of the view blueprint. Due to the fact that this is related to the design and architecture and how services are organized, it's important to understand some of the foundational concepts of how Google organizes its regions and zones. We will also look at what global, regional, and zonal resources are.

Regions refer to geographic locations where Google Cloud has data centers that offer cloud services. For example, in the United States, Google has regions in Iowa (us-central), Virginia (us-east), and Los Angeles (us-west); across the globe, Google Cloud has regions in Australia, Singapore, India, the UK, Germany, and a full list of Google Cloud regions can be found here: https://packt.link/jbTVP.

![](bbox=[0.151, 0.545, 0.848, 0.753])

![](bbox=[0.263, 0.773, 0.735, 0.816])

COMING SOON: Google Cloud will continue expanding into the following regions: Doha (Qatar), Geta (Japan), Paris (France), Milan (Italy), Madrid (Spain), Tokyo (Japan), Colombia (Colombia), Berlin (Germany), Copenhagen (Denmark), Riyadh (Saudi Arabia), Dallas (Texas), and Tel Aviv (Israel).

Figure 7.2 – Google cloud region locations