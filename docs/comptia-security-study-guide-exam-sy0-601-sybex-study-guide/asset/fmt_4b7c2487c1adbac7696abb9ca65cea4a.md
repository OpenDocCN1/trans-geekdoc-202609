
# 15. How does technology diversity help ensure cybersecurity resilience?

1. It ensures that a vulnerability in a single company's product will not impact the entire infrastructure.
2. If a single vendor goes out of business, the company does not need to replace its entire infrastructure.
3. It means that a misconfiguration will not impact the company's entire infrastructure.
4. All of the above.

# 16. Scott sends his backups to a company that keeps them in a secure vault. What type of backup solution has he implemented?

1. Nearline
2. Safe
3. Online
4. Offline

# 17. Gabby wants to implement a mirrored drive solution. What RAID level does this describe?

1. RAID 0
2. RAID 1
3. RAID 5
4. RAID 6

# 18. Florian wants to ensure that systems on a protected network cannot be attacked via the organization's network. What design technique should he use to ensure this?

1. A hot aisle
2. An air gap
3. A cold aisle
4. Protected cable distribution

# 19. What type of physical security control is shown here?

![](images/c09uf001.png)

1. A Faraday cage
2. An access control vestibule
3. A bollard
4. An air gap

# 20. Gurvinder identifies a third-party datacenter provider over 90 miles away to run his redundant datacenter operations. Why has he placed the datacenter that far away?

1. Because it is required by law
2. Network traffic latency concerns
3. Geographic dispersal
4. Geographic tax reasons

# Chapter 10: Cloud and Virtualization Security

Cloud computing is transforming information technology across all industries. Organizations of all sizes are drawn to the agility, flexibility, cost-effectiveness, and scalability of cloud computing solutions and are quickly integrating them into their technology environment, if not shifting completely to the cloud. New businesses are taking a "born in the cloud" approach that allows them to run their entire businesses without operating a single server.

This chapter discusses the aspects of cloud computing most important for security professionals and covered on the Security+ exam. You explore the different models of cloud computing, common cloud security concerns, and the security controls used to protect the confidentiality, integrity, and availability of cloud operations.

## Exploring the Cloud

**Cloud computing** can be an intimidating term, but the fundamental idea is straightforward: cloud service providers deliver computing services to their customers over the Internet. This can be as simple as Google providing their Gmail service to customers in a web browser or Amazon Web Services (AWS) providing virtualized servers to corporate clients who use them to build out their own technology environment. In each of these cases, the provider builds an IT service and uses the Internet to deliver that service to its customers.

Here's a more formal definition of cloud computing from the National Institute of Standards and Technology:

> Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.

Let's walk through some of the components of that definition. Cloud computing is ubiquitous and convenient. The resources provided by the cloud are available to customers wherever they may be. If you have access to the Internet, you can access the cloud. It doesn't matter whether you're sitting in your office or on the beach.

Cloud computing is also on-demand. In most cases, you can provision and deprovision cloud resources in a few minutes with a few clicks. You can acquire new cloud resources almost immediately when you need them and you can turn them off quickly (and stop paying for them!) when they are no longer required.

Many of the key benefits of the cloud derive from the fact that it uses a shared pool of resources that may be configured for different purposes by different users. This sharing allows **oversubscription** because not everyone will use all their resources at the same time and it achieves economies of scale. The fact that many different users share resources in the same cloud infrastructure is known as **multitenancy**. In a multitenant environment, the same physical hardware might support the workloads and storage needs of many different customers, all of whom operate without any knowledge of or interaction with their fellow customers.

The cloud offers a variety of configurable computing resources. We'll talk about the different cloud service models later in this chapter, but you can acquire infrastructure components, platforms, or entire applications through cloud service providers and then configure them to meet your needs.

The rapid provisioning and releasing of cloud services also takes place with minimal management effort and service provider interaction. Unlike on-premises hardware acquisition, you can provision cloud services yourself without dealing with account representatives and order processing times. If you need a new cloud server, you don't need to call up Microsoft, Amazon, or Google. You just click a few buttons on their website and you're good to go. From the perspective of most users, the cloud presents seemingly infinite capacity.

### Benefits of the Cloud

As organizations consider the appropriate role for the cloud in their technology infrastructure, the key issue they seek to address is the appropriate balance of on-premises versus cloud/off-premises resources. The correct balance will vary from organization to organization. Understanding some of the key benefits provided by the cloud is helpful to finding that correct balance:

* **On-demand self-service computing**. Cloud resources are available when and where you need them. This provides developers and technologists with incredible agility, reducing cycle times and increasing the speed of deployment.
* **Scalability**. As the demand for a cloud-based service increases, customers can manually or automatically increase the capacity of their operations. In some cloud environments, the cloud service provider may do this in a manner that is completely transparent to the customer, scaling resources behind the scenes. Cloud providers achieve scalability in two ways:
    * **Vertical scaling** increases the capacity of existing servers, as shown in [Figure 10.1](#c10.xhtml#c10-fig-0001)(a). For example, you might change the number of CPU cores or the amount of memory assigned to a server. In the physical world, this means opening up a server and adding physical hardware. In the cloud, you can just click a few buttons and add memory or compute capacity.
    * **Horizontal scaling** adds more servers to a pool of clustered servers, as shown in [Figure 10.1](#c10.xhtml#c10-fig-0001)(b). If you run a website that supports 2,000 concurrent users with two servers, you might add a new server every time your typical usage increases another 1,000 users. Cloud computing makes this quite easy, as you can just replicate your existing server with a few clicks.

    ![FIGURE 10.1 (a) Vertical scaling vs. (b) Horizontal scaling](images/c10f001.png)

    **FIGURE 10.1** (a) Vertical scaling vs. (b) Horizontal scaling

* **Elasticity**. Elasticity and scalability are closely related. Scalability is focused on rapidly increasing capacity. Elasticity says that capacity should expand *and contract* as needs change to optimize costs. If your website starts to experience a burst in activity, elasticity allows you to automatically add servers until that capacity is met and then remove those servers when the capacity is no longer needed.
