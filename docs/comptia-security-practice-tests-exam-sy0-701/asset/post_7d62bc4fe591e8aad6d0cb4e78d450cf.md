
149. C. An infrastructure-as-a-service (IaaS) cloud-hosted model where a third-party provider focuses on scalability and administration of a containerization service will meet Geoff's needs. When scaling from low to very large load is a common event, the ability to grow or shrink in a cloud environment can also provide significant cost savings over paying for an on-premises option that can handle the full scaling event. Software as a service (SaaS) and platform as a service (PaaS) provide full applications or platforms, not containerization environments.

150. B. Financial data includes transactions, accounts, and many other types of information related to finances. Intellectual property is a broad category of data created by humans. Public information is information that is available to the public, and trade secrets are kept private to a limited number of individuals in a company for competitive advantage or other purposes.

151. B. Clustering involves using two or more systems to provide a service as though they're a single server. Load balancing spreads workloads across multiple independent systems while front-ending them with a load balancer device or service to distribute load. Fail-open means that if a network device fails, traffic continues to pass through it. Fail-closed devices stop traffic if they fail. Decisions about fail-open and fail-closed are made based on security in most cases, with fail-closed being more secure if the organization relies on the device for security.

152. C. PCI DSS is a credit card data security standard, meaning that Alaina is most likely dealing with financial information. PCI DSS does not directly address intellectual property or trade secrets, and it's not a regulation.

153. B. Snapshots are used to copy both the data and machine state for virtual machines. Journaling is used for databases and similar uses where replaying actions can be useful to recover if an issue occurs. Replication copies the data synchronously or asynchronously, allowing for a separate copy to be available at all times. Grandfather/Father/Son is a backup cycle commonly used for tape backup.

154. D. Parallel processing allows for systems to be tested without taking them offline. This means that in the event of an issue with the backup systems or facility, the primary facility can continue to operate. Parallel processing does allow for more throughput, but organizations should not rely on this as parallel processing environments need to be able to handle the full load for the organization if the primary or backup fails. Fail over does test redundant systems and does not require organizations to create a significant issue. Instead, manual fail over processes are used to conduct fail over tests.

155. D. Placing the IPS inline at position D will reduce the amount of traffic it has to filter while still allowing it to filter traffic bound for the datacenter. Points A, B, and C will all have more traffic, although point A will have the most, with reductions likely at points C and D.

156. B. Increased complexity can include jurisdictional challenges, increased cost, and regulatory challenges as well as visibility challenges, management overhead increases, and a wide range of additional challenges from operating in multiple locations and models.

157. D. In general, fail over connections should be able to handle an organization’s full throughput. Overprovisioning for 100 Gbps will typically create significantly more cost not only for connectivity but also for network devices that can handle high speeds, and underprovisioning at 5 Gbps will mean that traffic would need to be reduced in a fail over scenario.

158. A. A hot site is prepared to take over processing for an organization immediately, and infrastructure is running in parallel with your production site. A warm site would have some hardware ready to be used, but the hardware would not be configured or otherwise ready for immediate resumption of service. Cold sites are spaces that are ready to be used in a disaster but without equipment or other necessary items in place to quickly take over production if needed. The term dispersion site is not commonly used, but the concept of geographic dispersion describes placement of sites with sufficient distance between them to make the likelihood of a single disaster impacting both quite low.

159. C. Geographic dispersion is unlikely for a single building’s network core. Redundancy, power backups, and multiple connectivity options are commonly part of designing a highly available network.

160. C. The General Data Protection Regulation (GDPR), Health Insurance Portability and Accountability Act (HIPAA), Family Educational Rights and Privacy Act (FERPA), and the Gramm-Leach-Bliley Act (GLBA) are all regulations, meaning that data they cover is regulated data. Intellectual property is the result of human creativity, classified data is a designation used by governments, and trade secrets are proprietary data with limited access often used by organizations for competitive advantage.

161. A. Virtual machine (VM) escape attacks attempt to access or gain control of the underlying hypervisor through virtual machines. While uncommon, if this occurred it could result in serious issues due to the number of systems run on a single hypervisor host particularly in cloud or shared environments. The other options were made up for the question.

162. B. AH (Authentication Header), ESP (Encapsulating Security Payload), and IKE (Internet Key Exchange) are all important IPSec (Internet Protocol Security) protocols. ISA is not an IPSec protocol.

163. D. Intrusion detection systems are considered passive systems because they cannot block traffic. Active systems like firewalls, IPS, and proxies all have the ability to directly interact with and stop or allow traffic. Air gapped devices do not have a physical connection to a network, or they are on a separate network that is not connected to other networks. Fail-closed devices stop traffic when they fail. Most IPS systems are not deployed inline since they do not need to be interactive and having them inline only creates another potential failure point.

164. C. Hashing uses a one-way function and should not be able to be reversed. This means that you can use hashing to securely store a password because you can hash the password, then compare hashes without needing to know the password. If you hash a database field, however, there’s no way to know what the original data was from the hash. Hashing should not be reversible, and it does not use symmetric or asymmetric encryption.

165. C. Tokenizing the data in a separate database will allow both the original unaltered database and a secured database to be used. This reduces risk while retaining data integrity where required. Steganography hides data in images and does not fit this use case. Masking only conceals data and does not protect it against attacks against the underlying application or database in many cases. Hashing the original database will transform the data, and using a single database remains risky.

166. C. SCADA and ICS systems often suffer from a lack of patches and updates. Cost is typically amortized over long periods of time, and SCADA and ICS systems are critical to organizational functions. Scalability is rarely a concern for embedded devices, and SCADA and ICS devices are designed for long life cycles and reliability.

167. C. In a SDN environment, the SDN controller manages and controls all the network devices, including switches and routers. That means that a compromise of the SDN controller would result in compromise of the entire network. No mention is made of SD-WAN in the question, so we don’t know the connectivity or relative importance of SD-WAN in the scenario.

168. B. Third-party support availability is an example of risk transference where the support contract moves the risk to the contractor. Availability and responsiveness may be considerations for the contractor, but the ability to obtain support doesn’t imply either of these. Compute is most commonly a concern where embedded devices or hardware solutions may not have sufficient computational power to meet new needs.

169. A. Network access control (NAC) tools that can allow for authentication and authorization based on user groups or roles and VLANs that separate groups based on those roles once they’re on the network exactly fit the needs Yarif has. 802.1X can also be helpful with this, but containerization is used to allow applications to be deployed without worrying about the application environment. SDN and MAC address filtering doesn’t account for user authentication and identities, just machine hardware addresses. SD-WAN is for external connectivity, not internal networks.

170. A. A simulation is the closest you can get to a real-world event without having one. A tabletop exercise has personnel discussing scenarios, whereas a walk-through goes through checklists and procedures. A wargame is not a common exercise type.

171. B. Serverless deployments remove the need to patch underlying infrastructure. They may still have vulnerable functions and should be logged. Cost savings is not a direct security advantage.

172. D. In a large-scale disaster scenario, personnel may be unwilling or unable to report to work. Organizations planning for disaster in an area where their personnel live and work often need to identify ways to ensure staffing in a scenario that impacts their staff. Lack of facility power is not a personnel issue. Authentication should be part of the hot-site capability. Insider threats are not a common concern during disasters.

173. D. ACLs, VLANs, and firewalls are all commonly used to implement network segmentation. Due to the operational challenges that air gaps create, they are far less commonly implemented and are only used when absolutely necessary.
