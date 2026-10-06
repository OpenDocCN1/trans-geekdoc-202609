# Self-Test 289

# Content Distribution Networks

Content Distribution Networks (CDN, also called Content Delivery Networks) use a series of distributed caching servers to improve performance and lower the latency of downloaded content. They automatically determine the servers closest to end users, download content from the fastest and closest servers on the Internet. Examples include Akamai, Amazon CloudFront, Cloudflare, and Microsoft Azure.

CDNs also increase availability and can reduce the effects of denial-of-service attacks: "While content delivery networks solve all ancillary problems such as improving availability and reducing bandwidth, the main problem they address is: the amount of time it takes for the host server to receive, process, and deliver on request a page resource (images, CSS files, etc.). Latency depends largely on how far away the user is from the server, and it’s compounded by the number of resources a web page contains.

For example, if all resources are hosted in San Francisco, and a user is visiting your page in London, then each request has to make a long round trip from London back to SF. If your web page contains 100 objects (which is at the low end of normal), your browser has to make 100 individual requests to your server in order to retrieve these objects" [19].

# Summary of Exam Objectives

Communication and Network Security is a large and complex domain, requiring broad and sometimes deep understanding of technical issues. Our world relies on networks, and those networks must be kept secure. It is important to not only understand why we use concepts like packet-switched networks and the OSI model, but also how we implement these concepts.

We have evolved from hubs to switches that provide traffic isolation. We have added detective devices such as HIDS and NIDS and preventive devices such as HIPS and NIPS. We have deployed secure protocols such as TLS and IPsec.

We have improved our network defense-in-depth every step of the way, and increased the confidentiality, integrity, and availability of our network data.

# Self-Test

> Note
Please see the Self-Test Appendix for explanations of all correct and incorrect answers.

+   1. Which protocol should be used for an audio streaming server, where some less is acceptable?
   A. IP
   B. ICMP
   C. TCP
   D. UDP