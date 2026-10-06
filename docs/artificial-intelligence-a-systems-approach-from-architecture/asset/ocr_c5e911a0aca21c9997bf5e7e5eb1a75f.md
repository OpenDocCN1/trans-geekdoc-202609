Once the AI ecosystem is in place as described in SRL 4, the AI developers and users can proceed to SRL 5, where the initial integration, verification, and validation of the AI architecture subsystems are demonstrated in a prototype system.

Once the prototype system is successfully integrated and evaluated, SRL 6 to be completed, an MVP or AI service must transition into an online demonstration in the users' operational environment (i.e., sidecar). This can be done on-premise, in an enterprise/edge environment, or both. The testing, verification, and validation should be assessed according to the set of attributes illustrated in the outer perimeter of the AI architecture implementation framework in figure 10.3. This assessment, performed in close collaboration between the AI developers (and, of course, the AI integration team) and users, helps in reaching SRL 7.

SRL 8 involves an in-depth integration

For SRL 9, the online (i.e., sidecar) demonstrated in SRLs 5 through 8 can be released into operations. This step means transitioning from an online configuration to an inline configuration, where the AI system is part of the day-to-day operational environment. SRL 9 also requires CI/CD and monitoring to identify necessary upgrades resulting from operational gaps, or identified after an initial capability is demonstrated (as defined in the envisioned future within the AISDM framework), or motivated by the desire to incorporate new technology.

The AI ecosystem consists of the foundational constituents to implement MLOps practices. We discuss MLOps in great depth in chapter 11. However, it is useful to provide readers with our working MLOps definition.

Historically, MLOps evolved as a discipline within the AI and ML community, patterned after the well-established development, security, and operations (DevSec-Ops) methodology for developing software systems. DevSecOps is a repeatable and somewhat automated discipline that has been adapted as an approach to migrate into operations. A common DevSecOps definition—among other similar and useful definitions [16]—is:

> DevSecOps: A set of practices that works to automate and integrate the processes between software development and information technology (IT) teams so they can build, test, and release software faster and more reliably in a secure manner.

The Dev part of the approach includes steps to plan, code, build, test, release,