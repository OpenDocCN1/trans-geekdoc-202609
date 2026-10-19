
## OBJECTIVES

According to the (ISC)² Candidate Information Bulletin (Exam Outline), a CISSP candidate is expected to be able to:

- Understand and support investigations.
- Understand requirements for investigation types.
- Conduct logging and monitoring activities.
- Secure the provisioning of resources.
- Understand and apply foundational security operations concepts.
- Employ resource protection techniques.
- Conduct incident response.
- Operate and maintain preventative measures.
- Implement and support patch and vulnerability management.
- Participate in and understand change management processes (e.g., versioning, baselining, security impact analysis).
- Implement recovery strategies.
- Implement disaster recovery processes.
- Test disaster recovery plan.
- Participate in business continuity planning and exercising.
- Implement and manage physical security.
- Participate in personnel safety (e.g., duress, travel, monitoring).

## Investigations

One area that has traditionally been lacking in most organizations is proper evidence handling and management. The exact name given to this area ranges from computer forensics, digital forensics, and network forensics to electronic data discovery, cyber forensics, and forensic computing. For the sake of clarity, the term digital investigations will be used to encompass all the components expressed in the other terms mentioned; thus, no one definition will be provided. Instead, digital investigations will include all domains in which the evidence or potential evidence exists in a digital or electronic form, whether in storage or on the wire. We intentionally omit digital multimedia from the mix, as this is a related, yet highly differentiated, field within the umbrella of digital forensic science. Unlike the media depiction, computer forensics/digital investigations is not some piece of software or hardware. It is based on methodical, verifiable, and “auditable” sets of procedures and protocols.

Digital investigations fall under the larger domain of digital forensic science. In 2008, the American Academy of Forensic Sciences (AAFS) in the United States formally recognized digital forensic science as a discipline under the category of Digital and Multimedia Sciences; it was the first time in 28 years that a new section had been recognized by the AAFS. The Digital Forensic Science Research Workshop (DFRWS) defines digital forensic science as:

> “The use of scientifically derived and proven methods toward the preservation, collection, validation, identification, analysis, interpretation, documentation and presentation of digital evidence derived from digital sources for the purpose of facilitating or furthering the reconstruction of events found to be criminal, or helping to anticipate unauthorized actions shown to be disruptive to planned operations.”

As a forensic discipline, this area deals with evidence and the legal system and is really the marriage of computer science, information technology, and engineering with law. The inclusion of the law introduces concepts that may be foreign to many security practitioners and security professionals. These include crime scene, chain of custody, best evidence, admissibility requirements, rules of evidence, etc. It is extremely important that anyone who may potentially be involved in an investigation is familiar with the basics of dealing with and managing evidence. There is nothing worse than finding the proverbial smoking gun only to learn that the evidence cannot be used, will be suppressed, or, even worse, the information security professional has violated the rights of the individuals in question and is now in worse trouble than the “bad guys.” Although different countries and legal systems have slight variations in determining how evidence and the digital crime scene should be handled, there are enough commonalities that a general discussion is possible.¹

Like incident response, there are various computer forensics guidelines (e.g., International Organization of Computer Evidence (IOCE), Scientific Working Group on Digital Evidence (SWGDE), Association of Chief Police Officers (ACPO)). These guidelines formalize the computer forensic processes by breaking them into numerous phases or steps. A generic guideline would include the following areas of focus and practice:

- **Identifying Evidence** — Correctly identifying the crime scene, evidence, and potential containers of evidence.
- **Collecting or Acquiring Evidence** — Adhering to the criminalistic principles and ensuring that the contamination and the destruction of the scene are kept to a minimum. Using sound, repeatable, collection techniques that allow for the demonstration of the accuracy and integrity of evidence or copies of evidence.
- **Examining or Analyzing the Evidence** — Using sound scientific methods to determine the characteristics of the evidence, conducting comparison for individuation of evidence, and conducting event reconstruction.
- **Presentation of Findings** — Interpreting the output from the examination and analysis based on findings of fact and articulating these in a format appropriate for the intended audience (e.g., court brief, executive memo, report).

### The Crime Scene

Before the security professional can begin to identify evidence, the larger crime scene needs to be dealt with. A crime scene is nothing more than the environment in which potential evidence may exist. The same holds for a digital crime scene. The principles of criminalistics apply in both cases:

- 1. Identify the scene
- 2. Protect the environment
- 3. Identify evidence and potential sources of evidence
- 4. Collect evidence
- 5. Minimize the degree of contamination

With digital crime scenes, the environment consists of both the physical and the virtual, or cyber. The physical (e.g., server, workstation, laptop, smartphone, digital music device, tablet) is relatively straightforward to deal with; the virtual is more complicated because it is often more difficult to determine the exact location of the

of thumb" were developed by the Australian Computer Emergency Response Team (AusCERT) and should be a part of an investigator’s methodology:

- Minimize handling/corruption of original data.
- Account for any changes and keep detailed logs of your actions.
- Comply with the five rules of evidence.
- Do not exceed your knowledge.
- Follow your local security policy and obtain written permission.
- Capture as accurate an image of the system as possible.
- Be prepared to testify.
- Ensure your actions are repeatable.
- Work fast.
- Proceed from volatile to persistent evidence.
- Do not run any programs on the affected system.

It is important for the security architect, the security practitioner, and the security professional to all stay up to date with the latest techniques, tools, processes, and requirements for admissibility of evidence. The entire area of computer forensics is coming under increased scrutiny by both the courts and the public and will undergo significant changes in the next few years as the field matures and develops, as did other more traditional forensic disciplines, such as DNA and latent fingerprint analysis.

For a more in-depth look at the world of Cyber Forensics and its impact on the Information Security Specialist, please see the Official (ISC)² Guide to the CCFP CBK. While this book targets the Certified Cyber Forensics Professional and candidates for the exam, it is also an authoritative reference and research book for all matters in the Cyber Forensics arena.

## Policy, Roles, and Responsibilities

To have effective and efficient incident handling, an organization must possess a solid foundation of knowledge and policy. In this instance, the foundation is comprised of a corporate incident handling and response policy, clearly articulated procedures and guidelines that take into consideration the various legal implications of reacting to incidents, and the management and handling of evidence (digital, physical, and document based). The policy must be clear, concise, and provide a mandate for the incident response/handling team to deal with any and all incidents. The policy must also provide direction for employees on the escalation process to follow when a potential incident is
