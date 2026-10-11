
## 4. C

Emulation is important in fighting obsolescence and keeping data available. Emulation lets you model older hardware and software and re-create them using current technology. With emulation, you can use a current platform to access an older application, operating system, or data while the older software still thinks it is running in its original environment.

`Type 1 hypervisor` is a hypervisor installed on a bare-metal server, meaning that the hypervisor is its own operating system. `Type 1 hypervisors` usually perform better due to the direct access to physical hardware. `Type 2 hypervisors` run inside an operating system of a physical machine.

`Platform as a service (PaaS)` is a kind of cloud computer service that enables a customer to develop and manage applications without a need to build and maintain the usual infrastructure.

## 5. D

The only answer that is a benefit to virtualization is faster provisioning and disaster recovery. Risks to virtual environments include patching, maintenance, and oversight, but the biggest is probably sprawl. It is easy to create `VMs`, push them out, duplicate machines, and forget about them. Once you bring them up, they could be up for weeks or months and get behind in patching, which creates a vulnerability.

## 6. A

The management of your application requires end-to-end monitoring, so a connection from your location to the cloud environment is the best way to have great control over and visibility into attacks that threaten your environment.

## 7. D

A `community cloud` is defined by `National Institute of Standards and Technology (NIST)` as a collaborative effort in which infrastructure is shared between several organizations from a specific community with shared concerns. It can be managed and controlled by a group of organizations with shared interests so that costs are spread over several users.

The `public cloud` model is the most widely used cloud service. This cloud type is a popular option for web applications, file sharing, and nonsensitive data storage. A `public cloud` model is available to anyone, but a `private cloud` belongs to a specific organization. That organization controls the system and manages it in a centralized fashion. A `hybrid cloud` environment is a combination of public, private, or community.

## 8. D

While single tenancy is more secure due to isolation and you control access and backups and cost with scaling, it requires more maintenance because single-tenant environments need more updates and upgrades that are managed by the customer.

## 9. D

A `virtual private cloud (VPC)` customer has exclusive access to a segment of a public cloud. This deployment is a compromise between a private and a public model in terms of price and features. Access can also be restricted by the user's physical location by employing firewalls and IP address whitelisting. Using the cloud is a trade-off—you gain speed, performance, and cost, but you still lose control over the security processes.

## 10. B

`Electronic vaulting` will enable you to transmit bulk data to an offsite data backup storage facility. You can choose to back up hourly, daily, or weekly. If a server fails, you can restore data quickly, but because the information is sent over the Internet, it should be encrypted.

`File storage` organizes and represents data as a hierarchy of files in folders; `block storage` chunks data into arbitrarily organized, evenly sized volumes; and `object storage` manages data and links it to associated metadata.

## 11. C

Virtualization creates an abstract computing platform. Many servers can be replaced by one larger physical server to decrease the need for hardware. Many hosts enable the execution of complete operating systems, and access can be restricted for security depending on the hardware access policy created by the host. In this scenario, the most secure option with a focus on confidentiality would be to assign virtual hosts to the client and physically partition storage. If confidentiality is in the question, look for encryption in the answer.

## 12. D

When you drag a file into the trash and empty the trash, it doesn't actually erase the file. It simply indicates to the file system that the file is deleted, but the data in the file remains on the hard drive until the file system eventually overwrites the file. We call this problem `data remanence`.

Cloud computing complicates the `data remanence` issue. You have little or no visibility into the physical location of your data in the cloud, so overwriting the physical media is virtually impossible. The cloud infrastructure may distribute your storage or virtual machine instance across multiple physical drives. Deprovisioning that instance is similar to dragging it to the trash. The data that is written to various drives remains until the cloud provider reallocates the sectors you were using to other customers.

## 13. D

Creating an `audit trail` is vital. Security policy often specifies which data should be collected, how it should be stored, and how long it will be kept. An `audit trail` is often used to find unauthorized activity on a network.

## 14. B

A `virtual private network (VPN)` is a tool to protect privacy and security on the Internet. `VPN` securely connects two computers with an encrypted tunnel to transfer data between a remote user and a corporate network. Employees should use `VPNs` when accessing cloud storage services. If you connect to the cloud over an unsecured Internet connection, there is a risk of exposing data to attackers.

## 15. B

An alert from any one of these assets should trigger the security organization to take a closer look at the cause of the alert. Monitoring and alerting are interrelated and have the ability to provide visibility into the health of your systems and help you understand trends in usage or behavior and the impact of changes you make. If the metrics fall outside of your expected ranges, these systems can send notifications to prompt someone to take a look and can assist in surfacing information to help identify the possible causes.

## 16. D

`IP Security (IPSec)` is a suite of protocols used across an IP network providing authentication, integrity, and confidentiality. This includes `Authentication Header (AH)`, `Encapsulating Security Payloads (ESP)`, and `Security Associations (SA)`, which provide the different configurations and keys used for those connections. `Internet Security Association and Key Management Protocol (ISAKMP)` is a component of `SA` and how the keys are managed and exchanged between the devices. An `IPSec VPN` will protect traffic being forwarded from client to server or from server to server.

## 17. A

For these specific requirements, the ability to audit event logs that include source address and timestamps is most critical. If the systems are on premises, you have more physical control. Assets in the cloud require more technical controls.

## 18. D

Defining user access as well as devices and idle time are especially important to a network security policy. You should also decide what authentication methods are used, how authentication will be implemented, and what the `standard operating procedures (SOPs)` are, should your organization be compromised.
