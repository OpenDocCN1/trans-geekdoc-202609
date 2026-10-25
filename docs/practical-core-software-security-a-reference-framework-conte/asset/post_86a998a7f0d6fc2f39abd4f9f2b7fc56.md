
- **Threat Modeling**
  - Identify Security Objectives
  - Survey the Application
  - Decompose it
  - Identify Threats
  - Identify Vulnerabilities

### Architectural Threat Analysis

### Ranking of Threats

### Risk Analysis

### Risk Mitigation Plan

and examine vulnerable points in design, and can uncover flaws that may result in a security compromise. Without the proper training and experience, it is easy to misinterpret results and difficult to create any necessary actionable remediation strategy. Essentially, the review of any open-source software or component used in your software product will require both tool assessment and follow-on threat modeling as well as risk assessment conducted by a seasoned software security architect.

## 4.5 Privacy Information Gathering and Analysis

It is important to consider if the system will transmit, store, or create information that may be considered privacy information early in the SDLC. The gathering of information and identification and development of a plan for implementing proper safeguards and security controls, including processes to address privacy information incident handling and reporting requirements, are determined at this stage. This stage of the SDL is where the information gathering and analysis for the Privacy Impact Assessment (PIA) begins. The analysis phase determines how PII will be handled to ensure that it conforms to applicable legal, regulatory, and policy requirements regarding privacy and what the risks and effects are of collecting, maintaining, and disseminating privacy information in identifiable form in the software and overall system being developed or one that it potentially interfaces with in a cloud or SaaS environment, and it examines and evaluates protections and alternative processes for handling information to mitigate potential privacy risks.

## 4.6 Key Success Factors and Metrics

### 4.6.1 Key Success Factors

The success of this second phase of the SDL depends on how well the SDLC identifies the threats, requirements, and constraints in functionality and integration and mitigates the risk. Key success factors for this second phase are listed in Table 4.1.

### Table 4.1 Key Success Factors

| Key Success Factor | Description |
|---|---|
| 1. Identification of business requirements and risks | Mapping of business requirements and risks defined in terms of CIA |
| 2. Effective threat modeling | Identifying threats for the software |
| 3. Effective architectural threat analysis | Analysis of threats to the software and probability of threat materializing |
| 4. Effective risk mitigation strategy | Risk acceptance, tolerance, and mitigation plan per business requirements |
| 5. Accuracy of DFDs | Data flow diagrams used during threat modeling |

### Success Factor 1: Identification of Business Requirements and Risks

During this phase, key stakeholders, including the software security group, help write out business risks and requirements. Business requirements are defined through the CIA pillars of information security. A successful SDL cycle must identify and capture all requirements to the best extent possible.

### Success Factor 2: Effective Threat Modeling

Though it is a complex and challenging task, the entire risk mitigation plan rests on threat modeling. Any gaps in a threat model will result in ineffective secure development and deployment controls.

### Success Factor 3: Effective Architectural Threat Analysis

Architectural threat analysis enables the identification of threats and ranks them in order of priority. All threat vectors resulting in the risk must be identified and prioritized.

### Success Factor 4: Effective Risk Mitigation Strategy

A key outcome from threat modeling and analysis is risk acceptance and a mitigation plan. Business appetite for risk acceptance and tolerance must be thoroughly vetted, including legal and finance.

### Success Factor 5: Accuracy of DFDs

DFDs are used during threat modeling to identify various components/elements of interest. DFDs should be as detailed as possible. Any assumptions should be reviewed carefully. Specifically, trust boundaries (client/server, private/public infrastructure, tiered architecture) should be properly documented and reviewed.

### 4.6.2 Deliverables

Table 4.2 lists deliverables for this phase of the SDL.

### Table 4.2 Deliverables for Phase A2

| Deliverable | Goal |
| :--- | :--- |
| Business requirements | Software requirements, including CIA |
| Threat modeling artifacts | Data flow diagrams, elements, threat listing |
| Architecture threat analysis | Prioritization of threats and risks based on threat analysis |
| Risk mitigation plan | Plan to mitigate, accept, or tolerate risk |
| Policy compliance analysis | Analysis of adherence to company policies |

### Business Requirements

A formal business requirement is an artifact that lists software requirements and business risks mapped to the three pillars of information security: confidentiality, integrity, and availability.

### Threat Modeling Artifacts

Key artifacts include DFDs, technical threat modeling reports, high-level executive threat modeling reports, threat lists, and recommendations for threat analysis.

### Architecture Threat Analysis

The key artifact from this step of the SDL is an artifact that outlines the risks of threat materializing. Another one that should be required from this step is threat ranking/priority.

### Risk Mitigation Plan

The risk mitigation plan outlines risks (and threats) to be mitigated, accepted, or tolerated. For each of these categories, it also outlines steps on mitigation risks. Finally, this report should be presented to the business for sign-off before actual work on the project begins.

### Policy Compliance Analysis

This artifact is a report on compliance with different security and nonsecurity policies within the company—for example, how software or its components comply with information security policy, data governance policy, data retention, cryptography policy, etc.

### 4.6.3 Metrics

The following metrics should be collected and recorded for this second phase of the SDL cycle:

- List of business threats, technical threats (mapped to business threats), and threat actors
- Number of security objectives unmet after this phase
- Percent compliance with company policies (existing)
- Number of entry points for software (using DFDs)
- Percent of risk (and threats) accepted, mitigated, and tolerated
- Percent of initial software requirements redefined
- Number of planned software architectural changes (major and minor) in a product
- Number of software architectural changes needed based on security requirements

## 4.7 Summary

The primary goal of the Architecture (A2) phase of our SDL model is to identify the overall requirements and structure for the software from a security perspective. The key elements of this phase are threat modeling, documentation of elements of the software attack surface from an architectural perspective; definition of security architecture and design guidelines; continued security, SDL, and privacy policy and requirements compliance reviews; and software product security release requirements.

These best practices result in the definition of the software's overall structure from a security perspective. They identify those components whose correct functioning is essential to security. They also identify the appropriate security design techniques applicable for the software product architecture, including the application of least privilege, and minimize the attack surface of the software product and any supporting infrastructure. Although a higher layer may depend on the services of lower layers, the lower layers are forbidden from depending on higher layers. Although the security architecture identifies an overall perspective on security design, the specifics of individual elements of the architecture will be detailed in individual design specifications.

The identification and measurement of the individual elements of the attack surface provides the development and software security team with an ongoing metric for default security and enables them to detect instances in which the software has been made susceptible to attack. During this phase, all exceptions to reducing the attack surface must be reviewed because the goal is to maximize security as a default for a software product that is being developed. Threat modeling uses a structured approach at a component-by-component level, identifying the assets that the software must manage and the interfaces by which those assets can be accessed. The likelihood of harm being done to any of the assets identified during threat modeling is estimated as a measure of risk. Countermeasures or compensating controls to mitigate the risk are also identified. Where appropriate and feasible, tools should be used that can capture the threat models in machine-readable form for storage and updating. Specific pre-ship software security criteria are also identified at this stage of the SDL.

Toward the end of the chapter, we discussed key success factors and their importance, deliverables, and metrics that should be collected from this phase.

## Chapter Quick-Check

- 1. Threats are identified using a process described by this mnemonic:
  - a. THREATEXPOSE
  - b. STRIDE
  - c. DREAD
  - d. CAPEC

- 2. Risk is calculated for each identified threat to prioritize findings and needs for remediation using which technique?
  - a. RISKCOMPUTE
  - b. DANGER
  - c. DREAD
  - d. THREATORDER

- 3. Which of the following is not a mitigation method for threats identified in threat modeling?
  - a. Redesign to eliminate vulnerability
  - b. Apply a standard mitigation
