continued security, SDL, and privacy policy and requirements compliance reviews; and software product security release requirements.

These best practices result in the definition of the software's overall structure from a security perspective. They identify those components whose correct functioning is essential to security. They also identify the appropriate security design techniques applicable for the software product architecture, including the application of least privilege, and minimize the attack surface of the software product and any supporting infrastructure. Although a higher layer may depend on the services of lower layers, the lower layers are forbidden from depending on higher layers. Although the security architecture identifies an overall perspective on security design, the specifics of individual elements of the architecture will be detailed in individual design specifications.

The identification and measurement of the individual elements of the attack surface provides the development and software security team with an ongoing metric for default security and enables them to detect instances in which the software has been made susceptible to attack. During this phase, all exceptions to reducing the attack surface must be reviewed because the goal is to maximize security as a default for a software product that is being developed. Threat modeling uses a structured approach at a component-by-component level, identifying the assets that the software must manage and the interfaces by which those assets can be accessed. The likelihood of harm being done to any of the assets identified during threat modeling is estimated as a measure of risk. Countermeasures or compensating controls to mitigate the risk are also identified. Where appropriate and feasible, tools should be used that can capture the threat models in machine-readable form for storage and updating. Specific pre-ship software security criteria are also identified at this stage of the SDL.

Toward the end of the chapter, we discussed key success factors and their importance, deliverables, and metrics that should be collected from this phase.

# Chapter Quick-Check

+   1. Threats are identified using a process described by this mnemonic:
+   a. THREATEXPOSE
+   b. STRIDE
+   c. DREAD
+   d. CAPEC

+   2. Risk is calculated for each identified threat to prioritize findings and needs for remediation using which technique?
+   a. RISKCOMPUTE
+   b. DANGER
+   c. DREAD
+   d. THREATORDER

+   3. Which of the following is not a mitigation method for threats identified in threat modeling?
+   a. Redesign to eliminate vulnerability
+   b. Apply a standard mitigation