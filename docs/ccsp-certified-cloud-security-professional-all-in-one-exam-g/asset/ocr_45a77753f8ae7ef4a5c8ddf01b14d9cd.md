# Appendix A: Exam Review Questions
341

was encrypted with strong encryption, the chances of it ever being accessed again are extremely low; for the most part, it's virtually impossible.

A is incorrect because physical destruction of media is virtually impossible within a cloud environment. With multitenancy and resource pooling, you can be assured that every physical device houses more than one cloud customer. Due to this, the idea of having the cloud provider destroy the physical media housing the data is an impossibility. Also, with how much data is always moving and balanced within a cloud environment, it is almost impossible to fully determine all the physical locations of data at any one point so that such destruction could ever be requested.

B is incorrect because shredding is a form of physical destruction of media and, as explained for answer A, would not be possible within a cloud environment.

C is incorrect because the realities of a cloud environment, with the use of virtualization and constant balancing and migrating of data, make it impossible to perform overwriting in a manner where it could be ensured that all data is overwritten. It would also be virtually impossible to isolate a particular customer's data, even if one could determine all the locations of that data, and perform overwriting in a manner that would not impact other tenants within the same environment.

24. Which of the following technologies will often make elasticity a bigger challenge in a cloud environment?

+   A. IPS

+   B. XML accelerator

+   C. Vulnerability scanner

+   D. Web application firewall

A. The use of IPS systems can be complicated with elasticity and auto-scaling; as systems are expanded programmatically, it is difficult to ensure that traffic is accurately routed through IPS systems and the correct signatures, policies, and rules are applied. Within a traditional data center, network pathways are known and routing, as well physical network connections, will ensure that the correct paths are always taken. In cloud environments, where the infrastructure is in a constant state of flux, this is far more difficult to achieve. The primary means to implement IPS to get around the shortcomings of virtual network-based IPS is the use of host-based IPS systems in a cloud environment.

B is incorrect because XML accelerators will be placed around load balancers and will automatically be added as systems are expanded programmatically. This differs from IPS because it relates to where in the network flow XML accelerators are placed and how the network is routed. XML accelerators are also used in conjunction with established web services, regardless of the number of virtual machines accessing them, will remain the same.