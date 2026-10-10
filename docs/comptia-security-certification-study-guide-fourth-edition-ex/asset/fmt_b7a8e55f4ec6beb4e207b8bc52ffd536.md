
### Next-generation secure web gateway (SWG)

A secure web gateway (SWG) is a gateway product that all traffic funnels through, and it prevents users from accessing web sites on the Internet or in the cloud that may have malware that could infect their system or the internal network/cloud network.

![Image](exam.jpg)

**Be sure to know the security solutions for the cloud that are mentioned in this section. Especially note that CASB allows you to define security policies that apply to network traffic flowing outside your current on-premises environment to the cloud.**

### Firewall Considerations in a Cloud Environment

When you’re looking for firewall products that work with cloud environments, a number of considerations should be put in place to help with your decision:

- **Cost** The cost of the firewall solution.
- **Need for segmentation** If you need a firewall solution that allows you to work with multiple network segments and control traffic between these segments.
- **Open Systems Interconnection (OSI) layers** The layer of the OSI model that the firewall runs at and what type of data you wish to filter traffic by. For example, if you want to be able to inspect the payload of the packet, you will want to use an application layer firewall (layer 7) versus a packet-filtering firewall (layer 3).

### Cloud Native Controls vs. Third-Party Solutions

One last point to make about implementing security controls within the cloud is that you should first investigate security controls that come with the cloud solution (native controls) before looking to third-party solutions. CSPs are constantly improving the features of their cloud solutions and increasing the number of security controls that are built into their products.

## CERTIFICATION SUMMARY

In this chapter you learned cloud computing concepts and different considerations that should be made to secure cloud resources. The following are some key points to remember regarding this chapter as you prepare for the Security+ certification exam:

- Virtualization technology allows you to run multiple virtualized computers on a single physical server.
- You can use snapshots with virtual machines as a method to revert back to a previous state of the system.
- Cloud computing is the hosting of services across the Internet to save businesses money because they don’t have to install their own servers.
- The three main cloud models to be aware of for the exam are SaaS, PaaS, and IaaS.
- Containers are like lightweight virtual machines because they share the OS kernel of the host system.
- Look to use cloud security controls to implement security within the cloud.

### TWO-MINUTE DRILL

#### Virtualization and Virtualization Security

![Image](boxsq.jpg) Virtualization allows you to run multiple operating systems on a single host computer.

![Image](boxsq.jpg) Ensure that each virtual machine is patched and secured. Be sure that the host computer is physically secured.

![Image](boxsq.jpg) VM sprawl is when a company loses track of the number of virtual machines that have been created within the organization, and there is no process in place for the creation, management, and decommissioning of virtual machines.

![Image](boxsq.jpg) VM escape is a security risk to virtualization environments that are unpatched. VM escape allows an application to access the host system from within the VM. For the exam, remember that you need to patch your virtualization environment to protect against VM escape.

#### Cloud Computing Concepts

![Image](boxsq.jpg) Cloud computing allows you to use the services of a provider from across the Internet to host your e-mail and database servers while you remotely connect and manage those servers.

![Image](boxsq.jpg) The `cloud service provider (CSP)` is the company providing cloud services to you.

![Image](boxsq.jpg) The `managed service provider (MSP)` is a company that manages the cloud environment for you and handles many of the IT functions, such as provisioning users, managing the cloud services, performing data backups and recovery, and monitoring activity.

![Image](boxsq.jpg) The `managed security service provider (MSSP)` is a company that handles the management of security for your environment. MSSPs are used for security configuration of your cloud environment, monitoring of activity, management of IDSs and firewalls, patch management, responding to security incidents, and performing security assessments within the organization.

![Image](boxsq.jpg) In the Software as a Service (SaaS) cloud model, an application is provided to the client without the client needing to install the application (such as Hotmail, Gmail, or Microsoft 365).

![Image](boxsq.jpg) With the Platform as a Service (PaaS) cloud model, the CSP supplies the runtime environment and development tools to create applications in the cloud.

![Image](boxsq.jpg) With Infrastructure as a Service (IaaS), the cloud service provider gives the customer a way to create a virtual data center, including creating virtual networks, storage, and virtual machines.

#### Cybersecurity Solutions for the Cloud

![Image](boxsq.jpg) You should secure storage resources with permissions, encryption, and replication technology.

![Image](boxsq.jpg) You should use network security controls to create virtual networks, public and private subnets, and segmentation features.

![Image](boxsq.jpg) Look to use security groups and container security with compute resources.

## SELF TEST

The following questions will help you measure your understanding of the material presented in this chapter. As indicated, some questions may have more than one correct answer, so be sure to read all the answer choices carefully.

### Virtualization and Virtualization Security

**1.** Which of the following identifies one of the security benefits of using virtualization technology?

A. You need to patch only the host operating system.
B. You need virus protection only on the host system.
C. You have less hardware to secure.
D. No drive encryption is needed.

**2.** Your manager has read about the security threat to virtualization technology known as VM escape. What security control would you implement to protect against VM escape?

A. Resource policies
B. Private subnets
C. A sandbox
D. A patch for the virtualization environment

**3.** You have a team of administrators who are responsible for creating virtual machines that are needed by the different departments within the organization. What are the risks of *not* having VM management processes in place regarding virtual machine creation?

A. VM sprawl
B. VM escape
C. VM memory leaks
D. VM patching

### Cloud Computing Concepts

**4.** Your manager would like to hire a company to monitor security events in the cloud, manage the IDSs and firewalls, and respond to security incidents. What role is your company looking to hire?

A. CSP
B. MSP
C. MSSP
D. DLP

**5.** What cloud computing model would you subscribe to if you are looking for a runtime environment for applications and development tools?

A. SaaS
B. PaaS
C. IaaS
D. XaaS

**6.** You would like to create virtual networks and host virtual servers in the cloud that can be accessed by your users. What cloud service model would you use?

A. IaaS
B. SaaS
C. XaaS
D. PaaS

**7.** What cloud security solution allows you to define security policies that apply to network traffic flowing outside your current on-premises environment to the cloud?

A. API
B. Security groups
C. SWG
D. CASB

### Cybersecurity Solutions for the Cloud

**8.** You need to create a group of virtual machines that are not accessible from the Internet. What cloud security control would you use?

A. Public subnet
