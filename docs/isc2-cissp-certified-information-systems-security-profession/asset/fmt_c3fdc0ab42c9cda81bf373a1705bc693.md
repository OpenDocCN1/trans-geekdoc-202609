
Security classifications indicate a hierarchy of sensitivity. For example, if you consider the military security labels of `Top Secret`, `Secret`, `Confidential`, and `Unclassified`, the `Top Secret` label includes the most sensitive data and `Unclassified` is the least sensitive. Because of this hierarchy, someone cleared for `Top Secret` data is cleared for `Secret` and less sensitive data. However, classifications don’t have to include lower levels. It is possible to use MAC labels so that a clearance for a higher-level label does not include clearance for a lower-level label.

Classifications within a MAC model use one of the following three types of environments:

`Hierarchical Environment` *A hierarchical environment* relates various classification labels in an ordered structure from low security to medium security to high security, such as `Confidential`, `Secret`, and `Top Secret`, respectively. Each level or classification label in the structure is related. Clearance in one level grants the subject access to objects in that level as well as to all objects in lower levels but prohibits access to all objects in higher levels. For example, someone with a `Top Secret` clearance can access `Top Secret` data and `Secret` data.

`Compartmentalized Environment` In a *compartmentalized environment*, there is no relationship between one security domain and another. Each domain represents a separate isolated compartment. To gain access to an object, the subject must have specific clearance for its security domain.

`Hybrid Environment` A *hybrid environment* combines both hierarchical and compartmentalized concepts so that each hierarchical level may contain numerous subdivisions that are isolated from the rest of the security domain. A subject must have the correct clearance and the need to know data within a specific compartment to gain access to the compartmentalized object. A hybrid MAC environment provides granular control over access, but becomes increasingly difficult to manage as it grows. [Figure 14.3](#c14.xhtml#figure14-3) is an example of a hybrid environment.

## Understanding Access Control Attacks

As mentioned in Chapter 13, one of the goals of access control is to prevent unauthorized access to objects. This includes access into any information system, including networks, services, communications links, and computers, and unauthorized access to data. In addition to controlling access, IT security methods seek to prevent unauthorized disclosure and unauthorized alteration, and to provide consistent availability of resources. In other words, IT security methods attempt to prevent loss of confidentiality, loss of integrity, and loss of availability.

Security professionals need to be aware of common attack methods so that they can take proactive steps to prevent them, recognize them when they occur, and respond appropriately. The following sections provide a quick review of risk elements and cover some common access control attacks.

While this section focuses on access control attacks, it’s important to realize that there are many other types of attacks, which are covered in other chapters. For example, Chapter 6, “Cryptography and Symmetric Key Algorithms,” covers various cryptanalytic attacks.

### Risk Elements

Chapter 2, “Personnel Security and Risk Management Concepts,” covers risk and risk management in more depth, but it’s worth reiterating some terms in the context of access control attacks. A *risk* is the possibility or likelihood that a threat will exploit a vulnerability resulting in a loss such as harm to an asset. A *threat* is a potential occurrence that can result in an undesirable outcome. This includes potential attacks by criminals or other attackers. It also includes natural occurrences such as floods or earthquakes, and accidental acts by employees. A *vulnerability* is any type of weakness. The weakness can be due to a flaw or limitation in hardware or software, or the absence of a security control such as the absence of antivirus software on a computer.

*Risk management* attempts to reduce or eliminate vulnerabilities, or reduce the impact of potential threats by implementing controls or countermeasures. It is not possible, or desirable, to eliminate risk. Instead, an organization focuses on reducing the risks that can cause the most harm to their organization. The key tasks that security professionals complete early in a risk management process are as follows:

*   Identifying assets

*   Identifying threats

*   Identifying vulnerabilities

### Identifying Assets

*Asset valuation* refers to identifying the actual value of assets with the goal of prioritizing them. Risk management focuses on assets with the highest value and identifies controls to mitigate risks to these assets.

The value of an asset is more than just the purchase price. For example, consider a web server hosting an ecommerce site that is generating $10,000 a day in sales. It is much more valuable than just the cost of the hardware and software. If this server fails causing the ecommerce site to become unavailable, it would result in the loss of revenue from direct sales and the loss of customer goodwill.

Knowing the asset value also helps with cost-benefit analysis, which seeks to determine the cost-effectiveness of different types of security controls. For example, if an asset is valued at hundreds of thousands of dollars, an effective security control that costs $100 is justified. In contrast, spending a few hundred dollars to protect against the theft of a $10 mouse is not a justifiable expense. Instead, an organization will often accept risks associated with low-value assets.

In the context of access control attacks, it’s important to evaluate the value of data. For example, if an attacker compromises a database server and downloads a customer database that includes privacy data and credit card information, it represents a significant loss to the company. This isn’t always easy to quantify, but attacks on Equifax provide some perspective. (See the sidebar “Data Breaches at Equifax.”)

The Equifax data breach can negatively impact the finances and credit ratings of tens of millions of individuals for years to come. It is also impacting Equifax directly. Shares dropped 35 percent within a week after Equifax officials publicly announced the data breach in September. This effectively wiped out about $6 billion of the company’s market value. One class-action lawsuit is seeking $70 billion in damages. The U.S. Internal Revenue Service (IRS) reportedly suspended a $7.2 million contract with Equifax after the October attack. Additionally, the Federal Trade Commission (FTC) reported that it is investigating Equifax, and legislators are urging other federal agencies to investigate the company too.

### Identifying Threats

After identifying and prioritizing assets, an organization attempts to identify any possible threats to the valuable systems. *Threat modeling* refers to the process of identifying, understanding, and categorizing potential threats. A goal is to identify a potential list of threats to these systems and to analyze the threats.

Threat modeling isn’t meant to be a single event. Instead, it’s common for an organization to begin threat modeling early in the design process of a system and continue throughout its lifecycle. For example, Microsoft uses its Security Development Lifecycle process to consider and implement security at each stage of a product’s development. This supports the motto of “Secure by Design, Secure by Default, Secure in Deployment and Communication” (also known as SD3+C). Microsoft has two primary goals in mind with this process:

*   To reduce the number of security-related design and coding defects

*   To reduce the severity of any remaining defects
