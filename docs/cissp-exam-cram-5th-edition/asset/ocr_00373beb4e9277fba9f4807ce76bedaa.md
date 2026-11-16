+   **Identify assets**: This step includes making an inventory of what applications are used, where those assets are located, and what security measures are in place. Knowing such things as when new assets are brought online or whether assets go live without the prescribed security controls is key to managing and reducing risk.

+   **Conduct threat intelligence**: Threat intelligence should be focused on three areas: assets, attackers, and software. You should have a good understanding of the tools and techniques used to exploit vulnerabilities and the motivations of the attackers. Another approach is to build an attack tree.

+   **Model and categorize threats**: You can use multiple methodologies to categorize and catalog threats. Two methodologies, STRIDE and DREAD, are discussed later in this chapter.

+   **Map and diagram potential attacks**: One approach to this step is to use a process flow diagram, which provides a high-level view of the system and focuses on the ways users and executing code move through a system. Another approach is to build an attack tree, which consists of a series of parent and child nodes representing different events. The root node, which is the topmost parent in the diagram, is the overall goal of the attack. The child nodes must test as true in order for the parent nodes to be true. The goal is for threat modelers to see what set of circumstances must come together in order for a threat to be successful.

+   **Mitigate threats**: Mitigation capabilities generally refer to technology to protect, detect, and respond to a certain type of threat. For threat mitigation to be successful, the threat modeling team must decompose the application, understand trust boundaries and input points, and rank the discovered threats. Identified threats need to be prioritized, and controls need to be deployed to remediate identified threats.

> **Note**
> Some of the common ways to reduce threats identified during threat modeling include the following: