# C. Elasticity

# D. Measured service

+   B. Multitenancy is the concept of having multiple customers sharing the same physical infrastructure and systems. With a traditional data center model, different customers use their own dedicated and segregated physical hardware, typically within their cages and with totally separate networking cabling and hardware as well. With a cloud deployment, all customers share the same physical hardware, thus requiring the use of logical segregation to ensure security.

+   A is incorrect because resource pooling does not deal with the segregation or isolation of resources and access without a shared environment. Resource pooling is the aggregation and allocation of compute resources across all customers.

+   C is incorrect because elasticity refers to the ability of a system to scale up or down based on current demands, and to ensure that at given point a system or application has the exact resources it needs. This is done to eliminate an excess or deficit of resources at any time, and so that customers are paying for exactly what they need and consuming.

+   D is incorrect because measured service refers to the concept within cloud computing where the cloud customer only pays for services they use. It does not relate to any technical capabilities or the segregation of services within the environment.

100. Which common threat is mitigated by DNSSEC?

+   A. Spoofing

+   B. Snooping

+   C. XSS

+   D. DoS

DNSSEC is explicitly designed to prove the validity and authenticity of DNS lookups from their authoritative host. It is intended to eliminate the possibility of rogue DNS servers intercepting lookup requests from devices or clients and inserting incorrect IP address resolutions in an attempt to direct traffic away from the legitimate destination. DNSSEC works by applying digital keys to the authoritative host and signing lookup and resolution requests when sending them back to the requester. With the ability to authenticate those keys back to the authoritative host, trust is established that the DNS resolutions are correct and from the proper authority, not inserted by a rouge or malicious host. DNSSEC ensures the integrity of DNS resolutions, but not the confidentiality or availability of them. It is also intended to work without requiring additional lookups when making the initial DNS request, instead sending back all required information from a single query.