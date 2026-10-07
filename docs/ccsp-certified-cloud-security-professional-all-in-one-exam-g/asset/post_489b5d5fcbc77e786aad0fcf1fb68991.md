
# Questions

- 1. Which of the following are common threats facing cloud computing platforms?
(Choose two.)

- A. Denial of service
- B. Cryptographic hashing
- C. Data breaches
- D. Phishing attacks

- 2. Which of the following standards is commonly applied to cloud computing security?

- A. ISO/IEC 27001:2010
- B. ISO/IEC 27003:2013
- C. ISO/IEC 27013:2000
- D. ISO/IEC 27001:2013

- 3. Which of the following methods is commonly used to ensure data removed from a cloud system is not recoverable?

- A. Deletion
- B. Degaussing
- C. Overwriting
- D. Shredding

- 4. Which type of hypervisor is a software implementation that runs on top of an operating system rather than tied to the hardware?

- A. Type 1
- B. Type 2
- C. Type 3
- D. Type 4

- 5. Which component of the NIST Cloud Technology Roadmap pertains to the minimum requirements between the cloud provider and cloud customer to meet contractual satisfaction?

- A. SLAs
- B. Regulatory requirements
- C. Governance
- D. Auditability

- 6. Which of the following is a unique benefit of a private cloud versus other models?

- A. Scalability
- B. Right-sizing resources
- C. Disaster recovery
- D. Ownership retention

- 7. Which of the following characteristics of cloud computing would be *most* attractive to management when looking to save money?

- A. On-demand self-service
- B. Measured service
- C. Resource pooling
- D. Rapid elasticity

- 8. What feature of IaaS would be most beneficial to a new company starting up with more limited capital?

- A. Scalability
- B. Physical hardware costs
- C. Physical security requirements
- D. High availability

- 9. Which common threat, which a customer could be totally unaware of the time, could lead to a direct financial cost without loss of reputation or privacy exposure?

- A. Data breaches
- B. Malicious insiders
- C. Denial of service
- D. Insufficient diligence

- 10. What certification would be most appropriate to use for financial statement auditing?

- A. NIST SP 800-53
- B. FIPS 140-2
- C. ISO/IEC 27001
- D. SOC 1, SOC 2, and SOC 3

- 11. Which component of the NIST Cloud Computing Roadmap pertains to the ability to split applications and reuse components?

- A. Portability
- B. Interoperability
- C. Auditability
- D. Availability

# Chapter 2: Architectural Concepts and Design Requirements

- 12. Which problem would make it least likely for an application or system to be able to easily move to another cloud provider?

- A. Data lock-in
- B. Operating systems
- C. Patching cycles
- D. Insecure APIs

- 13. Which cloud hosting model would be the most appropriate for a company looking to leverage multiple cloud providers for disaster recovery or load bursts?

- A. Public cloud
- B. Community cloud
- C. Private cloud
- D. Hybrid cloud

- 14. Which concept would be most important to consider for data security while it is being used by an application?

- A. Malicious insiders
- B. Data in transit
- C. Data at rest
- D. Denial of service

- 15. Which phase of the cloud data lifecycle typically occurs immediately after with the Create phase?

- A. Use
- B. Share
- C. Store
- D. Consume

# Questions and Answers

1. Which of the following are common threats facing cloud computing platforms?
(Choose two.)

- A. Denial of service
- B. Cryptographic hashing
- C. Data breaches
- D. Phishing attacks

> A, C. Denial-of-service attacks are used to overwhelm system resources with traffic or malformed requests with the intent to block legitimate and authorized users from the application or data and legitimate business access. Data breaches involve a malicious actor accessing, viewing, copying, or transferring data that they do not have an authorization or legitimate business use to do. Cryptographic hashing ensures the protection of data and is not a threat facing cloud computing platforms, and phishing attacks can target any application regardless of hosting configurations or technologies used, and is not cloud-specific author.

2. Which of the following standards is commonly applied to cloud computing security?
A. ISO/IEC 27001:2010
B. ISO/IEC 27003:2013
C. ISO/IEC 27013:2000
D. ISO/IEC 27001:2013

ISO/IEC 27001:2013 is commonly applied to cloud computing security as a standard and certification system for promoting and continually improving upon the security applied to a system or application. The other certifications listed are not relevant or fabricated numbers for example purposes.

3. Which of the following methods is commonly used to ensure that data removed from a cloud system is not recoverable?
A. Deletion
B. Degaussing
C. Overwriting
D. Shredding

Overwriting is a common method for ensuring removed data is no longer accessible in a cloud environment by replacing valid and sensitive data with random data, null values, or repeating data so that it cannot be read. Simple deleting only removes pointers to data and not the data itself, and degaussing and shredding are physical media destruction techniques that would not be available within a cloud environment.

4. Which type of hypervisor is a software implementation that runs on top of an operating system rather than tied to the hardware?
A. Type 1
B. Type 2
C. Type 3
D. Type 4

B. Type 2 is the type of hypervisor that is hosted on top of an operating system as a software package, rather than connected directly to the underlying physical hardware like a Type 1 hypervisor would be. Type 3 and 4 hypervisors do not exist and were simply included for example purposes.

5. Which component of the NIST Cloud Technology Roadmap pertains to the minimum requirements between the cloud provider and cloud customer to meet contractual satisfaction?

- A. SLAs
B. Regulatory requirements
C. Governance
D. Auditability

SLAs are the minimum requirements between the cloud provider and cloud customer to meet contractual satisfaction. Regulatory requirements are the laws and regulations that must be followed. Governance refers to the overall framework of how the cloud environment is managed. Auditability refers to the ability for a system to be examined and verified.

6. Which of the following is a unique benefit of a private cloud versus other models?

- A. Scalability
B. Right-sizing resources
C. Disaster recovery
D. Ownership retention

Ownership retention is a unique benefit of the private cloud model, where customers have significantly more input and control over how the cloud is deployed and managed. Scalability is a feature of all models and is not specific to private cloud. Right-sizing resources is synonymous with what elasticity provides and are not specific to any model. Disaster recovery is a larger concept that applies to any type of hosting including cloud environments.

7. Which of the following characteristics of cloud computing would be *most* attractive to management when looking to save money?

- A. On-demand self-service
- B. Measured service
- C. Resource pooling
- D. Rapid elasticity

While all aspects could potentially save an organization money, measured service and only paying for what you consume—when you consume it—would be the most attractive option. With a traditional data center, a system must essentially be built to handle peak load, leaving a lot of excess resources at most times. With a cloud environment, resources can be scaled up and added when needed and only incur these costs when they are actually used. On-demand self-service refers to the mechanism for scaling a system and provisioning resources, and itself is not a specific way to save money. Resource pooling refers to the overall aggregation of resources tenants of a cloud environment and the allocation between them to meet demand. Rapid elasticity is the concept that enables a cloud customer to add resources when needed, but is not the specific cost-saving mechanism.

8. What feature of IaaS would be most beneficial to a new company starting up with more limited capital?

- A. Scalability
- B. Physical hardware costs
- C. Physical security requirements
- D. High availability

B. Physical hardware costs would be most beneficial to a new company starting out with limited capital because IaaS would remove the need for a large upfront investment in data center expenses. A startup would only need to pay for the specific resources they need and when they need them, and not the full data center and all the components that are necessary for it. Physical security requirements are also a component that would make IaaS attractive to a customer, but it would be the same for PaaS and SaaS as well; the physical hardware costs are more directly related to the specific question. Scalability and high-availability are not appropriate answers as they may not be requirements of an individual customer and would not necessarily factor into the hosting decisions and costs.
