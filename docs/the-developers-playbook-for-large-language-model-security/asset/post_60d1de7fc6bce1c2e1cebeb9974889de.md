
confirms that the watermark matches the expected signature for a model. Signatures validate origin and prevent tampering via cryptography.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_141_0.png)

Because this technology evolves quickly, consider visiting the Coalition for Content Provenance and Authenticity (C2PA), a leader in developing standards for content authenticity, for the latest resources and standards.

Both digital signing and watermarking should be techniques in your arsenal for securing LLMs. Together, these techniques can uniquely authenticate models throughout their lifecycle and use. As models grow more powerful, establishing authenticity and preventing interference becomes critical. Embedding signatures and watermarked fingerprints provides the needed controls for model integrity across supply chains.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_141_1.png)

Some Google researchers have been promoting a combination of a tool called Sigstore and a management framework called Supply-chain Levels for Software Artifacts (SLSA) to sign and manage ML models. There aren’t many standardized approaches yet, so you may want to monitor how this combination evolves.

## Vulnerability Classifications and Databases

*Vulnerability classifications* refer to categorizing security weaknesses in software components based on their characteristics, impact, and exploitability. These classifications provide a standardized framework for identifying and describing vulnerabilities, facilitating a common understanding among stakeholders. Examples include the Common Weakness Enumeration (CWE) for software weaknesses and the Common Vulnerability Scoring System (CVSS) for assessing the severity of security vulnerabilities.

Vulnerability databases are essential repositories that gather and document identified vulnerabilities within software components. These databases are vital for monitoring and referencing known vulnerabilities, furnishing users with in-depth information, including descriptions of the vulnerability, its potential impact, suggested mitigation strategies, and related references. A notable example of such a database is the National Vulnerability Database (NVD), a comprehensive catalog of security vulnerabilities. The NVD integrates with the Common Vulnerabilities and Exposures (CVE) system, providing each listed vulnerability with a unique CVE identifier that facilitates easy reference and cross-linking between databases.

Vulnerability classifications and databases are crucial in supply chain security for several key reasons:

- **Identification and awareness** They provide a systematic way to identify and catalog known vulnerabilities in software components. This awareness is the first step in protecting against potential exploits.

- **Standardized communication** Vulnerability classifications offer a standardized language for describing security weaknesses, which is essential for clear communication among developers, security professionals, and other stakeholders.

- **Risk assessment and prioritization** By classifying vulnerabilities, organizations can assess their potential impact and prioritize mitigation efforts accordingly. This helps allocate resources more effectively to address the most critical vulnerabilities first.

- **Tracking and monitoring** Vulnerability databases enable organizations to continuously track new and existing vulnerabilities. Regularly monitoring these databases helps organizations stay updated with the latest security threats and take proactive measures.

- **Compliance and reporting** Many regulatory frameworks require organizations to manage known vulnerabilities effectively. Access to a comprehensive vulnerability database aids in compliance and can be critical for audit and reporting purposes.

- **Facilitating patch management** By keeping an up-to-date record of vulnerabilities, these databases help in the timely patching of software components, which is a critical aspect of maintaining secure systems.

- **Enhancing overall security posture** Regularly referring to vulnerability classifications and databases helps organizations develop a more robust security posture by enabling them to anticipate, prepare for, and respond to various security threats promptly and effectively.

In the context of supply chain security, where various components and dependencies can introduce vulnerabilities, vulnerability classifications and databases are invaluable for maintaining the integrity and security of the entire chain.

## MITRE CVE

MITRE.org is the online presence of the MITRE Corporation, a not-for-profit organization that operates multiple federally funded research and development centers in the United States. MITRE’s work primarily supports various US government agencies, and its mission is to solve problems for a safer world. It manages the CVE program and has developed several key frameworks and models, such as the ATT&CK framework, which provides a comprehensive matrix of tactics and techniques used by threat actors in cyberattacks.

The MITRE CVE database is a public online repository of reported security vulnerabilities and exposures. It's a linchpin in cybersecurity, serving as a reference point for identifying and classifying vulnerabilities in software and firmware.

Here's a breakdown of CVE's key features:

### Standardized identifiers

Each entry in the CVE database is uniquely identified by a CVE ID. This standardization enables security professionals and software developers to speak the same language when discussing security vulnerabilities.

### Wide range of sources

The database includes vulnerabilities reported by vendors, researchers, and users. This broad source base ensures a comprehensive collection of known issues.

### Detailed descriptions

Entries typically include detailed descriptions of the vulnerabilities, providing insights into how malicious actors might exploit them, their potential impact, and, sometimes, suggested mitigations.

### Vulnerability scoring

Many CVE entries include a CVSS score, which gives a quantitative measure of the vulnerability's severity and aids in prioritization for patching or mitigation.

### Free and open access

The CVE database is accessible to everyone, promoting transparency and wide-spread vulnerability information sharing. This open approach is crucial for timely and effective responses to security threats.

### Integration with other tools

The database is often integrated with various security tools and platforms, enhancing vulnerability management and threat assessment capabilities.

The MITRE CVE database primarily focuses on software and firmware vulnerabilities, emphasizing traditional cybersecurity concerns like network security, application security, and operating system flaws. The database includes vulnerabilities in various software products and systems, including those you might use in AI or LLM applications, like server software, databases, and operating systems.

However, the database wasn't designed to capture vulnerabilities unique to AI systems or LLMs. AI-specific vulnerabilities often require a different approach than conventional software vulnerabilities.

## MITRE ATLAS

MITRE ATLAS (Adversarial Threat Landscape for Artificial Intelligence Systems) is an initiative focused on the specific vulnerabilities and threats associated with AI systems, particularly in the context of national security. It represents a significant step toward understanding and mitigating the unique risks that AI technologies pose.

Here are some important aspects of MITRE ATLAS:

### Focus on AI security

Unlike traditional vulnerability databases like CVE, which cover a broad range of software and hardware vulnerabilities, ATLAS is dedicated exclusively to AI. ATLAS includes threats like adversarial attacks, where intentionally crafted inputs manipulate or deceive AI models.

### Comprehensive threat modeling

ATLAS provides detailed models of potential adversarial tactics, techniques, and procedures (TTPs) specific to AI systems. This threat modeling is crucial for understanding how AI systems can be exploited and for developing robust defense mechanisms.

### Collaborative effort

MITRE ATLAS is a collaborative effort involving various stakeholders in the AI and cybersecurity communities, including researchers, industry experts, and government agencies. This collaboration ensures diverse perspectives and expertise, which is vital for tackling complex AI security challenges.

### Educational resource

ATLAS is an educational resource for AI and cybersecurity professionals. It offers insights into the nature of AI threats and guidance on protecting against them. This guidance is valuable for developing training programs and security protocols for AI systems.

### Guidance for policy and standards

By providing a detailed understanding of AI threats, ATLAS can inform policy-making and the development of security standards for AI technologies. This is increasingly important as AI becomes more integral to critical infrastructures and national security.

As of the writing of this book, there isn’t an authoritative source of AI or LLM-specific security incident or vulnerability information, despite several projects that have been started. In the coming years, we’ll see organizations like MITRE, OWASP, and Hugging Face push forward to create more standard classifications of AI and LLM vulnerabilities and allow for the creation or extension of databases to track vulnerabilities. The growth of such databases will be critical in maturing supply chain security for LLMs.
