
## Key Terms

- Internet of Things
- Infrastructure as a Service
- Platform as a Service
- SaaS: Software as a Service
- Function as a Service
- Virtual Machines
- Content Delivery Networks
- Application Programming Interface (APIs)
- Multi-access Edge Computing
- Cloud Service Provider

## CHAPTER 10

### Secure Edge Development and Implementation

### Introduction

This chapter embarks on a journey into the realm of Secure Edge implementation, in which the fusion of cutting-edge technologies and robust security measures is redefining the way we perceive, design, and safeguard our digital ecosystems. As we delve into the step-by-step implementation of edge computing, we will unravel the intricacies of why securing the edge is no longer a luxury but a strategic imperative for businesses across industries.

Picture the edge as the first line of defense, the gatekeeper to a treasure trove of data, and the stage for a new era of applications that demand not just speed but resilience. From the sprawling Internet of Things (IoT) to the demands of low-latency applications, the edge is the crucible where the future is being forged.

Our exploration will traverse AWS and Azure Secure Edge implementation, dissecting the anatomy of edge computing and its integration with security frameworks. We will navigate through the maze of challenges that developers face when crafting solutions that seamlessly balance performance with protection.

As we venture deeper, we introduce you to tools that make the collaborative efforts of developers, security experts, and innovators who are pushing the boundaries of what is possible at the edge. The convergence of cloud capabilities, artificial intelligence, and robust encryption at the edge is transforming how we perceive and interact with technology, offering both unparalleled opportunities and unprecedented risks.

So, fasten your seatbelts as we embark on this expedition into Secure Edge implementation. Let us navigate the uncharted waters where innovation meets security, and where the promise of a connected future is safeguarded by the resilient foundations we lay today.

### Structure

In this chapter, the following topics will be covered:

- Architecture of Cattle Farm IoT and Edge Computing
- Step-by-Step Set up of Cattle Farm IoT and Edge Computing Implementation

### Objectives

In this chapter, our attention is directed towards harnessing the capabilities of IoT and Edge Computing technologies to elevate different facets of cattle farming. This spans from monitoring the health of the cattle and managing resources to fostering sustainability and promoting collaboration within the farming community. The execution of the design formulated in the preceding chapter will be carried out by establishing a secure edge in Azure.

### Architecture of Cattle Farm IoT and Edge Computing

Cattle IoT Tags provide a comprehensive overview of your livestock operations, enabling you to monitor inventory, breeding, pregnancies, calving, weaning, and other essential aspects. With Cattle IoT Tags, you can easily categorize your animals into groups using customizable criteria, such as animal type, age, pasture, and more. Streamline your record-keeping process by updating the records of each group after work sessions or pregnancy checks in a single step, saving valuable time.

![](img/31919f230142cc926c349c85b30fe4d2_714_0.png)

Figure 10.1: Cattle Farm Edge Architecture

### Step-by-Step Set Up and Implementation

Before delving into the step-by-step, below is the application flow of our implementation.

![](img/31919f230142cc926c349c85b30fe4d2_715_0.png)

Figure 10.2: Cattle Farm Edge Application Architecture

The process of the implementation is described below.

Transfer device data from an IoT Edge-operating data sender application to IoT Hub.

Azure Functions then receive this device data from IoT Hub and register it in MongoDB.

Machine Learning retrieves the data from MongoDB.

The Machine Learning process involves sending some data to MongoDB and some to the Azure Container Registry.

Before we get into full gear of setting up our edge infrastructure, let us look into some of the edge Operating Systems (OS) available in the market and supported by Ubuntu which will be our official Linux OS for all of our implementations. It should be noted that you can use Windows Operating System but this book’s implementation will only focus on Linux.

Below is the table with various types of Edge OS that can be used with Ubuntu OS.

| OS. OS. |
|---|
| OS. |
| OS. |
| OS. |
| OS. |
| OS. |
| OS. |
| OS. |

Table 10.1: IoT OS Platform Download Table

Based on the US geographic structure, let us set up edge infrastructure in three Azure cloud data centers to handle our 16 Cattle ranch we owned in the United States of America.

### Azure Step-by-Step Set Up

Creating an Azure virtual network is a fundamental step in building a secure and scalable cloud infrastructure. Whether you are setting up a new environment or expanding an existing one, the process involves several key steps to ensure proper configuration and connectivity. Let us walk through the step-by-step guide to create an Azure virtual network, empowering you to establish a robust foundation for your cloud-based resources.

Step 1A: Create 3 Azure private virtual network (VNET) segments to be used at the edge as follows.

Network/Segment 1: This network will be 10.10.10.0/23 for the gateway and internet facing edge applications.

Network/Segment 2: This network will be 10.10.20.0/23 for the middleware and internal facing edge applications.

Network/Segment 3: This network will be 10.10.30.0/23 for the Artificial Intelligence and Machine Learning edge applications.

Step 1B: Login to Azure at https://portal.azure.com

Step 1C: Click on Create a

![](img/31919f230142cc926c349c85b30fe4d2_718_0.png)

Figure 10.3: Create Azure Resources Icon

Step 1D: Search for the virtual network in the search box

![](img/31919f230142cc926c349c85b30fe4d2_718_1.png)

Figure 10.4: Azure Virtual Network Search Box

Step 1E: Select Virtual and click create.

![](img/31919f230142cc926c349c85b30fe4d2_719_0.png)

Figure 10.5: Azure Create Virtual Network Icon

Step 1F: Populate the form as follows.

Basic:

Azure Virtual Network (VNet) is the fundamental building block for your private network in Azure. VNet enables many types of Azure resources, such as Azure Virtual Machines (VM), to securely communicate with each other, the internet, and on-premises networks. VNet is similar to a traditional network that you'd operate in your own data center, but brings with it additional benefits of Azure's infrastructure such as scale, availability, and isolation.
Learn more.

### Project details

Select the subscription to manage deployed resources and costs. Use resource groups like folders to organize and manage all your resources.

- Subscription *: Azure Free Subscription
- Resource group *: book127-edge1-westus-network-rg
- Create new

### Instance details

- Virtual network name *: book127-edge1-westus-edgateway-network
- Region *: (US) West US

### Figure 10.6: Azure Create Virtual Network Basic Form

Security form:

Basics Security IP addresses Tags Review + create

### Azure Firewall

Azure Firewall is a managed cloud-based network security service that protects your Azure Virtual Network resources. Learn more.

Enable Azure Firewall

Azure Firewall name book127-edge1-westus-edgateway-network-Firewall

Subnet name * AzureFirewallSubnet

Tier * Basic

Policy * (New) book127-edge1-westus-edgateway-network-firewall-policy Create new

Azure Firewall public IP address * (New) book127-edge1-westus-edgateway-network-firewall Create a public IP address

Management traffic public IP address * (New) book127-edge1-westus-edgateway-network-traffic-management Create a public IP address

Figure 10.7: Azure Create Virtual Network Security Form

### IP Address:
