
# Information Security Program Framework

To organize the effort, a framework is required. A framework lends itself to many easily related metaphors. The most obvious is that of any building: no foundation, no building. More specifically, the better the framing of any building, the longer it will last, the more it can hold, and the more functional it becomes. Of course, with any building there must first be a plan. We hire architects and engineers to design our buildings, to think about what is possible, and relay the best way to achieve those possibilities.

In the same way, we need a framework for our information security program. Much like the many rooms in a building, each with its own functions, we segment our information security program into logical and tangible units called domains. `Security domains` are associated with designated groupings of related activities, systems, or resources. For example, the Human Resources Security Management domain includes topics related to personnel, such as background checks, confidentiality agreements, and employee training. Without the framework, every new situation will see us repeating, redesigning, and reacting, which all together can be referred to as “unplanned,” or spending time in crisis. Fortunately, in the information security arena there is absolutely no reason to choose crisis over preparedness. Strategies involving proactive, rather than reactive, procedures have become the ad hoc standard for systems of cybersecurity governance. A number of public and private organizations, including the International Organization for Standardization (ISO) and the National Institute of Standards and Technology (NIST), have all invested considerable time and energy to develop standards that enable proactive cybersecurity frameworks.

In this chapter, you are introduced to the standards developed by both organizations. Before we begin building our information security program and policies, we need to first identify what we are trying to achieve and why. We begin this chapter by discussing the three basic tenets of information security. We then look at the escalating global threat, including who is behind the attacks, their motivation, and how they attack. We apply this knowledge to building the framework of our information security program and how we write our policies.

## Confidentiality, Integrity, and Availability

The elements of confidentiality, integrity, and availability are often described as the CIA model. It is easy to guess that the first thing that popped into your mind when you read those three letters was the United States Central Intelligence Agency. In the world of cybersecurity, these three letters represent something we strive to attain and protect. Confidentiality, integrity, and availability (CIA) are the unifying attributes of an information security program. Collectively referred to as the `CIA triad` or `CIA security model`, each attribute represents a fundamental objective of information security.

You may be wondering which is most important: confidentiality, integrity, or availability? The answer requires an organization to assess its mission, evaluate its services, and consider regulations and contractual agreements. As [Figure 3-1](#ch03.xhtml#ch03fig01) illustrates, organizations may consider all three components of the CIA triad equally important, in which case resources must be allocated proportionately.

![](graphics/03fig01.jpg)

### What Is Confidentiality?

When you tell a friend something in confidence, you expect them to keep the information private and not share what you told them with anyone else without your permission. You also hope that they will never use this against you. Likewise, `confidentiality` is the requirement that private or confidential information not be disclosed to unauthorized individuals.

There are many attempts to define what confidentiality is. As an example, the ISO 2700 standard provides a good definition of confidentiality as “the property that information is not made available or disclosed to unauthorized individuals, entities, or processes.”

Confidentiality relies on three general concepts, as illustrated in [Figure 3-2](#ch03.xhtml#ch03fig02).

![](graphics/03fig02.jpg)

There are several ways to protect the confidentiality of a system or its data; one of the most common is to use encryption. This includes encryption of data in transit with the use of site-to-site and remote access virtual private networks (VPNs), or by deploying server and client-side encryption using Transport Layer Security (TLS).

Another important element of confidentiality is that all sensitive data needs to be controlled, audited, and monitored at all times. This is often done by `encrypting data at rest`. Here are some examples of sensitive data:

*   Social security numbers
*   Bank and credit card account information
*   Criminal records
*   Patient and health records
*   Trade secrets
*   Source code
*   Military secrets

The following are examples of security mechanisms designed to preserve confidentiality:

*   Logical and physical access controls
*   Encryption (in motion and at rest)
*   Database views
*   Controlled traffic routing

Data classification is important when you’re deciding how to protect data. By having a good data classification methodology, you can enhance the way you secure your data across your network and systems.

Not only has the amount of information stored, processed, and transmitted on privately owned networks and the public Internet increased dramatically, so has the number of ways to potentially access the data. The Internet, its inherent weaknesses, and those willing (and able) to exploit vulnerabilities are the main reasons why protecting confidentiality has taken on a new urgency. The technology and accessibility we take for granted would have been considered magic just 10 years ago. The amazing speed at which we arrived here is also the reason we have such a gap in security. The race to market often means that security is sacrificed. So although it may seem that information security requirements are a bit extreme at times, it is really a reaction to the threat environment.

You also have to pay attention to confidentiality laws. For example, information exchanged between doctors and patients or lawyers and clients is protected by confidentiality laws called the “doctor-patient privilege” and the “attorney-client privilege,” respectively.

As it pertains to information security, confidentiality is the protection of information from unauthorized people and processes. Federal Code 44 U.S.C., Sec. 3542 defines confidentiality as “preserving authorized restrictions on access and disclosure, including means for protecting personal privacy and proprietary information.”

None of us likes the thought of our private health information or financial information falling into some stranger’s hands. No business owner likes the thought of her proprietary business information being disclosed to competitors. Information is valuable. Social security numbers are used for identity theft. Bank account credentials are used to steal money. Medical insurance information can be used to fraudulently obtain services or to make counterfeit claims. Military secrets can be used to build weaponry, track troop movements, or expose counterintelligence agents. The list goes on and on.

Because there is value in confidential information, it is often a target of cybercriminals. For instance, many breaches involve the theft of credit card information or other personal information useful for identity theft. Criminals look for and are prepared to exploit weaknesses in network designs, software, communication channels, and people to access confidential information. The opportunities are plentiful.
