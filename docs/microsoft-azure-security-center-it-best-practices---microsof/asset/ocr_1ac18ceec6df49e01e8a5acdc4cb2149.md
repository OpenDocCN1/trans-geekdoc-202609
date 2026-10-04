vices and provide capabilities to quickly restore services that were interrupted. You should also ensure that deployed services are operated, maintained, and supported in accordance with the service-level agreement (SLA) established with the CSP.

# Endpoint protection

Cloud security is not only about the security of the CSP infrastructure; it is a shared responsibility. Endpoint protection is one aspect of security for which organizations are responsible. Organizations that adopt cloud computing should consider increasing endpoint security because these endpoints will be exposed to more external connections and access apps that may be housed by different cloud providers.

Users are the main target of attacks, and an endpoint might be a user's workstation, a user's smartphone, or any other device that may be employed to access cloud resources. Attackers know that the user is the weakest link in the security chain, and attackers will continue to use in social-engineering techniques, such as phishing emails, to entice users to perform actions that can compromise an endpoint.

> IMPORTANT Securing privileged access is a critical step to establishing security assurances for business. Make sure to read more about Privileged Access Workstations at://://.ms/cyberpaw and know more about Microsoft's methodology for protecting high-value assets.

One approach to enable the end-to-end visibility of your endpoint protection and your cloud workloads is the integration of your Cloud Workload Protection Platform (CWPP) with your Endpoint Detection and Response (EDR) solution.

# Data protection

Regarding cloud security, the goal when migrating to the cloud is to ensure that data is secure no matter where it is located. Data might exist in any of the following states and locations:

+   - Data at rest on the user's device: In this case, the data is located at the endpoint, which can be any device. You should always enforce data encryption at rest for company-owned devices and in BYOD scenarios.
- Data in transit from the user's device to the cloud: When data leaves the user's device, you should ensure that the data is protected. There are many technologies that can encrypt data regardless of its location—for example, Azure Rights Management. It is also imperative to ensure that the transport channel is encrypted. Therefore, you should enforce the use of Transport Layer Security (TLS) to transfer data.
- Data at rest in the cloud provider's datacenter: When data arrives at the cloud provider's servers, the CSP's storage infrastructure should ensure redundancy and protection. Make sure you understand how your CSP performs data encryption at rest, who is responsible for managing the keys, and how data redundancy is performed.