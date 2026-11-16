
## FIGURE 3.7 Cost of Risk Versus Level of Control

**Note**

Any risk involving human life is extremely high and should be given the highest priority.

![](img/cd307d33c10f35ada49ea76811ef60ad_151_0.png)

At the completion of the risk-handling step, the risk assessment team produces a final report that presents all the findings, information, assessments, and recommendations for the organization. The final assessment report becomes the instrument used by management to make sound business decisions pertaining to the organization’s overall risk and vulnerability assessment; it is the basis for how the organization will mitigate the identified risks, threats, and vulnerabilities.

**Note**

The cost–benefit analysis of a safeguard or protection measure is measured as the control gap:

ALE before the safeguard – ALE after the safeguard = Control gap (value of the safeguard to the organization)

This formula can be used to evaluate the cost-effectiveness of a safeguard or to compare various safeguards to determine which are most effective. The higher the resulting value, the more cost-effective the safeguard. In most cases, you want to avoid spending more funds on a control than the cost of the asset itself. However, this is not always true. For example, federal, state, and local governments may sometimes provide controls to protect critical systems regardless of the cost of the controls. As discussed earlier in this chapter, it is not always easy to measure the potential for damage with a numeric value.

ExamAlert Some organizations use a risk analysis matrix, which looks at likelihood and impact. For an example, see MITRE’s Risk Matrix, at https://www.mitre.org/research/technology-transfer/open-source-software/risk-matrix.

## Threat Modeling Concepts and Methodologies

Threat modeling is a structured approach to evaluating threats. Threat modeling is typically used during the planning, design, and implementation of security controls to validate that countermeasures are effective and placed where needed. When done periodically, threat modeling can also help security teams ensure that protections are sufficient based on known or emerging threats. If threat modeling is not done on a periodic basis, new threats may remain unsecured, leaving systems and data vulnerable.

## Threat Modeling Steps

The general steps in the threat modeling process are as follows:

- **Identify assets**: This step includes making an inventory of what applications are used, where those assets are located, and what security measures are in place. Knowing such things as when new assets are brought online or whether assets go live without the prescribed security controls is key to managing and reducing risk.

- **Conduct threat intelligence**: Threat intelligence should be focused on three areas: assets, attackers, and software. You should have a good understanding of the tools and techniques used to exploit vulnerabilities and the motivations of the attackers. Another approach is to build an attack tree.

- **Model and categorize threats**: You can use multiple methodologies to categorize and catalog threats. Two methodologies, STRIDE and DREAD, are discussed later in this chapter.

- **Map and diagram potential attacks**: One approach to this step is to use a process flow diagram, which provides a high-level view of the system and focuses on the ways users and executing code move through a system. Another approach is to build an attack tree, which consists of a series of parent and child nodes representing different events. The root node, which is the topmost parent in the diagram, is the overall goal of the attack. The child nodes must test as true in order for the parent nodes to be true. The goal is for threat modelers to see what set of circumstances must come together in order for a threat to be successful.

- **Mitigate threats**: Mitigation capabilities generally refer to technology to protect, detect, and respond to a certain type of threat. For threat mitigation to be successful, the threat modeling team must decompose the application, understand trust boundaries and input points, and rank the discovered threats. Identified threats need to be prioritized, and controls need to be deployed to remediate identified threats.

> **Note**
> Some of the common ways to reduce threats identified during threat modeling include the following:

- Providing more training to staff
- Changing business processes or procedures
- Implementing administrative controls such as rotation of duties or dual controls
- Changing an application's configuration
- Modifying source code
- Using technical controls such as web application firewalls, proxies, or other screening and filtering device

## Threat Modeling Tools and Methodologies

As mentioned earlier, a number of threat modeling tools and methodologies are in use. For example, Microsoft developed STRIDE, which stands for the following.

- Spoofing: Using a falsified identity
- Tampering: Making unauthorized changes
- Repudiation: Ensuring plausible deniability
- Information disclosure: Distributing information to external or unauthorized entities
- Denial of service (DoS): Preventing unauthorized use of a resource
- Elevation: Using a limited user account to gain greater access

Another methodology is OpenStack's DREAD, which provides a rating system and is designed to be flexible. DREAD considers the following:

- Damage potential: How severe is the damage likely to be?
- Reproducibility: How complicated is it for attackers to reproduce the exploit?
- Exploitability: How hard is it to perform the attack?
- Affected users: What percentage of users are going to be affected?
- Discoverability: How hard is it for an attacker to discover this weakness?

PASTA (Process for Attack Simulation and Threat Analysis) is a seven-step process focused on aligning technical security requirements with business objectives. Each step consists of several substeps. The sequence is as follows:

- 1. Define the objectives.
- 2. Define the technical scope.
- 3. Perform application decomposition.
- 4. Conduct threat analysis.
- 5. Conduct vulnerability and weaknesses analysis.
- 6. Conduct attack modeling.
- 7. Conduct risk and impact analysis.

OCTAVE (Operationally Critical Threat, Asset, and Vulnerability Evaluation) is a threat modeling methodology developed at Carnegie Mellon University that focuses on organizational risks rather than technological risks. It consists of three phases:

- 1. Build asset-based threat profiles.
- 2. Identify infrastructure vulnerabilities.
- 3. Develop a security strategy and plans.

VAST (Visual, Agile, and Simple Threat Modeling) is an automated threat modeling platform that distinguishes between application and operational threat models. VAST was created to be integrated into workflows built around the DevOps philosophy.

Trike is a threat modeling platform that operates from a defensive viewpoint rather than trying to emulate the thought process of the threat actor. It is different from the other methodologies in that it has you model the system you are trying to defend.

Regardless of which methodology you deploy, it is most important to start this process in system development. It is cheaper to build in controls early than to wait until later and attempt to add them.

## Managing Risk with the Supply Chain and Third Parties

Today, multinational corporations often operate in different parts of the world and use a variety of vendors, contractors, and suppliers. As reliance on these third parties continues to grow, so does the need to manage a number of relationships.

For example, say that you are the CISO for a company that manages a natural gas pipeline and a power generating plant. You would have many supervisory control and data acquisition (SCADA) devices, IP cameras, automated pumps, sensors, computers, and so on as a part of your production control system. In this case, you would be concerned with who are you buying these from and can the vendor be trusted and whether these devices are compliant with your needs.

This is where supply chain risk management comes in. Supply chain risk management involves applying techniques to manage and understand risk along the supply chain. In our example, a large portion of the power plant’s equipment is commercially available technology that uses either Microsoft Windows or the Linux operating system, which are common targets for hackers. To reduce the supply chain risk, you might carry out a continuous risk assessment to reduce vulnerabilities and ensure continuity of operations.

Supply chain risk management (SCRM) is but one small piece of the process you must consider. Third-party entities must verify compliance with all stated security objectives, requirements, regulations, and contractual agreements. The following are some of the documents, agreements, and memorandums used for third-party governance:

- Interconnection security agreement (ISA): An ISA is a security document that specifies the requirements for establishing, maintaining, and operating an interconnection between systems or networks or between an agency and external systems. The document lists the requirements for connecting the systems and networks and details what security controls are to be used to protect the systems and sensitive data with external systems. An ISA typically maintains a drawing of
