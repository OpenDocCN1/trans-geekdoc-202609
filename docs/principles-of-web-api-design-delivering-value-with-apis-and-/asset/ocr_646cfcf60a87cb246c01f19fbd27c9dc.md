# CHAPTER 15 PROTECTING APIs

![](bbox=[0.135, 0.105, 0.782, 0.368])

**Figure 15.1** The components of a service mesh, including the proxy instances, connected to a central control plane for oversight and configuration.

# Web Application Firewalls

WAFs protect APIs from network threats, including common scripting and injection attacks. Unlike API gateways, they monitor OSI layer 3 and layer 4 network activity, allowing for deeper packet inspection than is possible with API gateways focus on the HTTP protocol only. As such, they can detect more attack vectors and prevent common ones before request reaches backend API servers.

WAFs offer an additional layer of protection against DDoS attacks that may be sourced from a variety of locations and IP addresses.

It is important to note that the capabilities offered by WAFs are important, they are merged into APIMs, content delivery networks, and other layers that may eliminate the need to install an eslint WAF.

# Content Delivery Networks

Content delivery networks (CDNs) distribute cacheable content to spread across the world, reducing load on API servers. They improve application performance by responding with cached data to API clients more quickly than waiting for API servers to handle the request.

Some CDN vendors are taking on many of aspects of a WAF by acting as a reverse proxy for dynamic content alongside caching static content. This reduces unwanted traffic on APIs and Web applications. Some CDNs also offer an additional layer of protection against DDoS attacks before they ever reach cloud infrastructure.