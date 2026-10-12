
# LIST OF ABBREVIATIONS

| Abbreviation | Full Form |
| --- | --- |
| API | Application Programming Interface |
| BYOT | Bring Your Own Technology |
| CAIQ | Cloud Evaluation Initiative Questionnaire |
| CCs | Cloud Clients |
| CIO | Chief Information Officer |
| CSA | Cloud Security Alliance |
| CSP | Cloud Service Provider |
| DDoS | Distributed Denial of Service |
| DoS | Denial of Service |
| DR | Disaster Recovery |
| ENISA | European Network and Information Security Agency |
| EU | European Union |
| FSI | Financial Services Institutions |
| IaaS | Infrastructure-as-a-Service |
| ISP | Internet Service Providers |
| IT | Information Technology |
| MAC | Media Access Control |
| NAT | Network Address Translation |
| NFS | Network File Systems |
| NIST | National Institute of Science and Technology |
| PaaS | Platform-as-a-Service |
| PII | Personally Identifiable Information |
| PocT | Policy as a Trust Management Technique |
| PrdT | Prediction as a Trust Management Technique |
| RecT | Recommendation as a Trust Management Technique |
| RepT | Reputation as a Trust Management Technique |
| RMF | Risk Management Frame |
| SA | Support Arrangement |
| SaaS | Software-as-a-Service |
| SLA | Service Level Agreement |
| SNMP | Simple Network Management Protocol |
| VM | Virtual Machine |

# ACKNOWLEDGMENTS

First and foremost, I would like to thank my family and friends for always standing by me. I also thank Nigel Wyatt, Michael Weiss (Griffith College Dublin), Gabriel Grecco (photography), and the Momentum Press team for the support and inspiration.

# INTRODUCTION

This second volume of my series of works dedicated to Data Security in Cloud Computing acts as a professional benchmark, as well as a practitioner’s guide to today’s most complete and concise view of cloud computing security. It offers coverage on cloud computing security concepts, technology, and practice as they relate to based technologies, and to recent advancements. It investigates practical answers to a wide assortment of cloud computing protection issues.

The primary audience for this book consists of engineers/students interested in monitoring and analyzing specific, measurable cloud computing protection environments, which may include infrastructure or transportation systems, mechanical systems, seismic events, and underwater environments. This book will also be useful for safety and related professionals interested in tactical surveillance and mobile cloud computing protection target classification and monitoring. This thorough reference and practitioner’s short book is also of significance to students in upper-division undergraduate and graduate-level classes in cloud computing security.

# CHAPTER 7: SECURE CLOUD ARCHITECTURE

![](images/line.jpg)

The Internet has provided seamless connectivity of computing nodes across continents; hence the computing paradigm in the beginning of the nineteenth century has developed into cloud computing. The elements of cloud computing architecture are all hardware and software, needed for the delivery of cloud computing solutions (`NIST` and `U.S. Department of Commerce` 2013). Furthermore, these components of a cloud computing architecture are coordinated into front-end platforms or cloud customers, backend platforms such as servers and storage devices, along with a route connecting front to the rear end to get cloud-based solutions. This route is the network, which can be either the public (Internet) or a private community, as shown in [Figure 7.1](#12_chapter07.xhtml#fig7-1). The role of this network is to give services. The general public cloud tools are made available to cloud-based customers through Internet service providers (`ISPs`).

Security can be broken in either or both the cloud infrastructure or across the Internet. Cloud computing providers offer elasticity, quick provisioning and discharging of resources, resource pooling, and higher bandwidth access, but with higher security risks. Just as data facilities were both business and technical constructs to support data processing needs of businesses, the cloud in a sense is more like a business construct, since the security and privacy in the cloud are managed more or less from the cloud service providers.

The public cloud computing service users no longer own the infrastructure; hence, the data security has to be managed by the cloud service providers. This is a change in paradigm, which also calls for redefining the governance of both privacy and security. This in no way indicates that consumers of cloud providers do not need to check their information privacy and security handling process, but should have a service level agreement (`SLA`) with all the cloud service providers and identify suitable levels of protection that are compliant with the state in which they operate.

Risk management needs to factor the dangers specific to different installation cloud models and devise solutions to mitigate those dangers. Data confidentiality, integrity, and its accessibility in a cloud installation model are somewhat more susceptible to risk compared to some noncloud deployment model. Secure cloud computing architecture has to be scalable, to react to most insider and outsider threats as well as natural disasters.

![](images/figure7-1.jpg)

**Figure 7.1.** Cloud computing structure

![](images/figure7-2.jpg)

**Figure 7.2.** Just how secure is your cloud?

Next, we itemize lots of safety risks connected with the deployment of cloud computing systems. These risks have to be addressed by the service provider and stated in the `SLA`. The client must know the full implications of the dangers because the service suppliers are offering the service to their clients required to safeguard their clients’ information (`Cloud Security Alliance` 2011):

*   **Governance:** Considering that the user doesn’t manage the computing infrastructure, the management of security and privacy is considerably looser, but has to be compliant with the local state and federal regulations.
*   **Ambiguity in governance:** The cloud service provider must cover the privacy and safety requirements of most of its customers, who could differ in their needs as to what constitutes minimal governance.
*   **Regulatory compliance:** Consumers of cloud computing have to offer the security of their clients’ data stored at the service provider facility, which in turn demands that the cloud service providers have appropriate certifications per state regulations.
*   **Security incidents:** Detection, reporting, and management of security breaches must be transparent and documented immediately to the consumers of computing.
