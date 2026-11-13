
### 8.7.3.4 Distributed Storage Problems and Concerns in the Chain of Custody

Because there is no viable defense against attacks using the traditional chain of custody administration, the only alternative for evidence retention is central storage, which exposes data and leaves the evidence open to modification or falsification. To overcome these constraints, we have created Filecoin global storage systems that interface with the suggested Sawtooth architecture and smart contracts to automatically collect, identify, inspect, analyze, report, and keep data [32]. These distributed applications use a digital contract-based method that helps the judicial process and the media forensics authority safeguard the chain of custody as well as the integrity of the evidence.

### 8.7.3.5 Problems with Regulatory Compliance

The normal chain of custody for collecting multimedia evidence has issues with mistakes in digital case activities, especially when records are kept on a central server and reliance is placed on external security solutions. Also, the information from portable video cameras is collected using poor and unreliable technologies before being examined and processed using various forensics techniques.

## 8.8 Concepts in Cloud Forensics

There are several concepts that can help identify alternative sources of evidence and significantly assist scientists working in this field, such as cloud crime types and where to conduct investigations in/on the cloud [33].

### 8.8.1 Kind of Crime

In that it is recognized as a crime in cloud computing, any crime committed utilizing the cloud as an object, topic, or instrument is comparable to computer crimes. Cloud computing becomes an important topic when the CSP has been the target of criminal activities, including distributed denial-of-service (DDoS) attacks, when crimes like identity theft, which happened in the Google case, are committed via the cloud environment. The cloud is finally seen as a tool when it is utilized to attack the system of another provider, such as when a dark cloud is deployed.

### 8.8.2 Conducting Investigations

A case supported by cloud-based evidence is known as an “in” cloud inquiry in the cloud building. Businesses must understand a CSP’s incident response approach, which includes issue identification, notification, and recovery, to meet the use of contemporary digital forensics technology. Snapshots give a picture of the systems at a particular moment. It can be considered an important source of proof for services delivered by dispersed or virtual systems. Nonetheless, it is important to assess the snapshot’s authenticity for forensics, given the current ways of acquiring it. As a precaution, cloud users should check whether their online reality snapshots are accessible offline and consider the frequency of these snapshots [34][35]. For instance, Elastic Compute Cloud and Amazon Elastic Block Storage (EBS) Boot Volume both offer block-level storage services (EC2). The user storage is available as snapshots via the EBS. A snapshot from a cyberattack can be later examined offline without affecting the original storage or interfering with operations. As mentioned, recording volatile data will cause modifications to the target system when examiners must access “live” systems. From our perspective, preserving an audit trail of the examiners’ actions while also taking a consistent snapshot of an operational system.

### 8.8.3 Performing Investigation on Cloud

Recently, Dell made a forensics-as-a-service offering available. Before employing the data center’s capability to image physically taken goods, Dell used the digital forensics process. A reasonable timeline of events should finally be able to be produced by the examiners. Petabytes of data cannot be photographed and analyzed, and seizing the service provider’s servers will probably violate users’ legitimate rights to privacy [36]. According to a speed test report from the AccessData Forensics Toolkit (FTK), it would take roughly 5.5 hours to examine a 120 GB hard drive utilizing top-of-the-line workstations. In line with that, evaluating a 2 TB hard disk would take roughly 85 hours.

## 8.9 Cloud Security

Before attempting to investigate the complexities of cloud forensics, it is necessary to comprehend cloud security. We go over the crucial concerns around cloud security in terms of cloud services’ architecture and assaults on them.

### 8.9.1 Cloud Architecture

Cloud architectures are helpful for comprehending how different suggestions work together to offer a comprehensive solution [37]. Enterprises interested in cloud computing are advised to take the reference design into consideration, according to a white paper created jointly by VMware and Savvis.

The following security elements should be put in place:

- Every level needs to have a defined security profile.
- CSP is required to maintain the hardware and software inside a demilitarized zone (DMZ).
- The management of operating systems and virtualization on a CSP must take place behind the DMZ.
- The CSP is responsible for managing resource provisioning by isolating and separating VM resources.
- Either router ACLs, a perimeter firewall, or web application security must be used to offer network security.
- CSP must offer access routes to real-world servers that are authorized to perform the requested functionality.
- The CSP is required to offer security authentication, authorization, and auditing (AAA).

### 8.9.2 Cloud Security Attacks

Some of the assaults that can occur in a cloud computing environment include the following:

- Wrapping attack. When a user sends a request from his virtual machine to the browser, a SOAP (Simple Object Access Protocol) message is produced. The web server receives the request. The attackers conduct a wrapping attack by using a duplicate username and password during the login process to influence the SOAP messages sent between the web browser and server during the setup phase.
- Flooding attack. The attacker creates false or harmful data, such as requests for resources or code to execute in an application. To process the virus requests, the server uses its CPU, memory, and other resources just like a genuine user would [38][39]. When the servers ultimately exhaust their capacity, they transfer the workload to another server, which causes flooding.
- Browser attack. This attack compromises the signature and encryption of messages as they are transferred between the site and the web server, tricking the browser into recognizing an adversary as a legitimate user and executing all requests submitted to the web server.
- Malware-injection attack. In this type of attack, the hacker creates a standard action, like deleting a user, and embeds another command, like setAdminRight, into it. Instead of following the user account deletion instructions when a user request is delivered to the server, the server divulges a user account to the attacker.
- Unsecured interfaces and APIs. Businesses that provide cloud computing services make several software interfaces or APIs accessible for users to manage and interact with services that use the cloud. Reliance on a subpar set of interfaces might subject a business to certain security vulnerabilities concerning password security, availability, and secrecy [40].
- Site administrators. The cloud services process is controlled, supervised, and maintained by site administrators. By default, they have access to all the data, papers, and restricted corporate assets. In revenge or for other reasons, administrators may wind up leaking or allowing the leak of critical information.
- Data theft. One of the most serious unrecognized security flaws with virtualized data is that system administrators can take any amount of data without leaving a trail of proof. A virtual machine can be replicated with just three easy steps: logging in as the superintendent’s administrator, mounting the disk image, and unmounting the original copy.
- Data leakage. The term “data leakage” refers to the transfer of data from one client to another. When a customer deletes their disk and a new client starts a new drive, data leakage is a concern [41][42]. The physical disks for old and new drives can have some overlapped portions. Hence, the new customer might attempt to image from written tons of data.
