
Typically, such attacks flood the servers, systems or networks with the traffic so as to overwhelm the victim’s resources for the purpose of making it difficult or impossible for the authorized users to access it.

The United States Computer Emergency Readiness Team (US-CERT)¹ affords various guidelines so as to determine when a DoS attack occurs, which are as follows:

- Difficulty in reaching a specific website
- Degradation in the performance of the network

Whenever a suspicion arises regarding a DoS attack, the organizations or enterprises contact their Internet Service Provider (ISP) to check whether it is owing to a DoS attack or due to something else. Afterwards, the ISP assists in mitigating the attack by throttling the malicious traffic by employing the load balancers for reducing the impact of attacks. Similarly, the feasibility of DoS detection can be explored through intrusion prevention systems, intrusion detection systems, etc. Moreover, in distributed denial-of-service attacks, the network-connected devices along with the computer are infected by malware. The various types of DoS attacks are as shown in Figure 14.5.

![](img/57d9c6707468cbe6ea69c555dd9498fc_238_0.png)

Figure 14.5 Types of DoS attacks.

### 14.4 Globus Security Architecture

The idea of security policy and the mode that security mechanisms contribute in distributed systems for enforcement of such types of policies are best established by considering an example. Let us discuss the security policy involved for the Globus wide-area system [3]. Basically, Globus is a system that supports large-scale distributed computations where many hosts, files, and other resources are concurrently employed for carrying out a computation. These environments are also referred to as computational grids. Furthermore, many times, resources in these grids are located in distinct domains of administration which may be positioned in several parts of the world.

The security policy for Globus includes the following statements:

- The environment consists of a number of administrative domains.
- Local operations: It represents the operations which are conducted only within a single domain. These are merely subject to a local domain security policy.
- Global operations: This represents the operations concerning several domains that require the concerned initiator to be known in every domain wherever the operation is being conducted.
- Operations between entities in distinct domains need mutual authentication.
- Local authentication is replaced by Global authentication.
- Controlling access to the resources is mainly merely subject to local security.
- Users can delegate rights to processes.
- Credentials can be shared among processes in the same domain.

It is assumed that the environment consists of a number of administrative domains, such that every domain possesses its policy for local security. It is further understood that local policies cannot be altered since the domain takes part in Globus. Subsequently, security in Globus prohibits itself from operations that can hamper several domains relevant to this issue. Furthermore, Globus assumes that operations which are completely local to a domain are subject only to the concerned domain’s security policy. The Globus security policy means that various requests for operations can be initiated either locally or globally. The initiator can be a user or process acting on behalf of a user, and must be locally known within each domain.

Once a user or a process acting on behalf of a user gets authenticated, it becomes essential to verify the exact access rights with respect to resources. For example, a user wishing to update a file will first have to be authenticated; afterwards, it can be verified whether or not the concerned user is practically permitted to update the file. The Globus security policy depicts that the access control decisions are framed completely locally within the domain of the location of the accessed resource. Furthermore, Globus focuses on security threats involving multiple domains. Specifically, the security policy demonstrates that the crucial design issues involve the representation of a user in any remote domain, as well as the allocation of resources from a remote domain to a user or his representative. The architecture of the Globus security policy is as shown in Figure 14.6.

![](img/57d9c6707468cbe6ea69c555dd9498fc_240_0.png)

Figure 14.6 Globus security policy architecture.

### 14.5 Distribution of Security Mechanisms

The dependency existing among services concerning trust gives rise to the notion of a Trusted Computing Base (TCB). A TCB represents a set of all security mechanisms in a distributed computer system that are necessary for ensuring a security policy, and which are required to be trusted. The smaller the TCB is, the better it will be. Furthermore, a TCB in a distributed system can incorporate the local operating systems at several hosts. A file server in a distributed file system might need to rely on the several protection mechanisms afforded by the corresponding local operating system. Moreover, middleware-based distributed systems need to trust in the existing local operating systems. If no trust exists, then part of the functionality of the local operating systems has to be incorporated into the distributed system itself.

## Security in Healthcare Applications Based on Fog and Cloud Computing

ROJALINA PRIYADARSHINI¹, MOHIT RANJAN PANDA², BROJO KISHORE MISHRA¹

¹ Department of Computer Science and Information Technology, C. V. Raman College of Engineering, Bhubaneswar, India  
² Department of Computer Science and Engineering, C. V. Raman College of Engineering, Bhubaneswar, India

brojikishoremishra@gmail.com

### Abstract

The last few years have seen remarkable advancements in the e-healthcare system. This is due to the growth of digitization in the healthcare sector, especially the use of wearable devices equipped with sensors, IoT devices and body area network. e-Healthcare is not only limited to storing clinical data. Sophisticated digital applications are able to be designed and developed which cater to an array of varied health-related services. Some examples are telemonitoring of elderly persons, tracking mobility of patients, monitoring sugar levels and blood pressure, and giving early notifications in case of emergencies. This has brought about a revolution in e-healthcare. At the same time, these applications are challenged by different security issues. The security challenges are multi-fold when these solutions are built on a virtual environment like cloud or fog. In this chapter we have tried to accumulate some of the security issues which arise in the healthcare sector. The chapter also discusses existing solutions and emerging threats.

### Keywords

e-Healthcare, confidentiality, integrity, availability, threats, vulnerabilities

### 15.1 Introduction

Recent years have seen a rise in the use of electronic equipment, such as sensors, for developing digital healthcare solutions. Nowadays, healthcare applications are not limited to digital record keeping of various clinical data generated from patients, doctors, etc. Current healthcare applications focus on telemonitoring patients, tracking their mobility, and giving early notifications to doctors and relatives in case of critical situations. This is possible due to the emergence of Internet of Things (IoT) devices and the use of embedded sensors in a patient’s body. The general architecture of the healthcare monitoring system is depicted in Figure 15.1. Reliable communication, handling and mobility, latency control and energy-efficient routing are some of the issues which need to be addressed. Due to the digital transformation, there has been a staggering quantity of unstructured data like video and images generated in the healthcare field. The healthcare field has produced a virtual and connected world of clinical devices which continuously send out unstructured, and potentially unsecured data, which is vulnerable to attack. These data need to be transmitted in a channel, which may not always be secured. But, the physiological data of an individual contain highly personal and sensitive information. So, security is a predominant need of healthcare applications, especially if the solutions use IoT devices equipped with sensors or body area networks.

![](img/57d9c6707468cbe6ea69c555dd9498fc_243_0.png)

Figure 15.1 General architecture of healthcare monitoring systems.

But, when the healthcare solutions are deployed in cloud and fog environment, the security concerns are doubled due to the following reasons:
