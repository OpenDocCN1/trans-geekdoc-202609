
# 4. The level and hierarchy analysis of the cyber-resilience memory control system made it possible to identify the following strata: monitoring of group and mass cyber-attacks and immunity accumulation; self-recovery program development and verification of the disturbed system behavior; recovery, which achieves cyber system self-recovery when solving the target problems.

# 2 Cyber Risk Management

DOI: 10.1201/9781003337300-3

The present chapter reviews the best practices of the cyber risks management based on guidelines and requirements of the well-known international and national standards `ISO 31000:2018 (AS/NZ 4360:2004)`, `ISO/IEC 27005:2018`, `ISO/IEC 15408:2009`, `NIST SP 800-30 Rev. 1 (September 2012)`, `NIST SP 800-37 Rev. 2 (December 2018)`. A brief historical overview of the standards development of cyber risks analysis and management has been made through the examples of `NIST SP 800-30 "Guide for Conducting Risk Assessments"`, `OCTAVE – Operationally Critical Threat, Asset and Vulnerability Evaluation` SEI/CMU, `MG-2 – A Guide to Security Risk Management for Information Technology Systems`, `SA-CMM – Software Acquisition Capability Maturity Model` SEI/CMU etc. The main stages of the cyber risks management life cycles have been considered in details: detecting (identification) of cyber risks; dimensioning of a cyber risk; developing a cyber risks management plan; current monitoring and improvement. It was demonstrated that the proper cyber risk management depends on the choice of the criteria and cyber resiliency indices. Therefore, in addition to the requirements and guidelines of the well-known standards `ISO/IEC 27005:2018`, `NIST SP 800-30 Rev. 1 (September 2012)`, `NIST SP 800-37 Rev. 2 (December 2018)` it is obligatory to develop the quantitative metrics and cyber resilience measures. There has been proposed a possible metric and cyber resilience measure based on the mathematical tools technique of `Petri Nets`. It is essential that the proposed metric and cyber resilience measure allows controlling the behavior semantics of the protected vital informational infrastructure under conditions of the heterogeneous mass cyber attacks of intruders. Here the examples of development for corporate methods of cyber risks management, as well as recommendations for their improvement are given. Cyber risks analysis and management tools frontier through the examples of `COBRA`, `CRAMM`, `RiskWatch`, `Avangard` and `Cytegic` are shown.

## 2.1 Best Practices of Cyber Risk Management

A modern practice of cyber risk management ([Figure 2.1](#Ch03.xhtml#cap_lbl0148)) allows assessing the existing level of `residual risks of business interruption`. That is extremely important in cases where the increased demands are raised to cyber resilience (and cyber security) of the vital informational infrastructure. It also becomes possible to conduct comparative analysis of `efficiency – cost` for various options of building-up a corporate system of cyber resilience, to select and implement adequate `organizational` and `technical` measures for ensuring cyber resilience on reasonable grounds [71, 72, [281](#Reference.xhtml#ref0285)].

### 2.1.1 History of Cyber Risk Management Standards

An approach to a cyber resilience (and cyber security) on the basis of cyber risks management `ISO/IEC 27005 (2018)`, `ISO/IEC 22301 (2012)`, `NIST SP 800-160 (2018)` is relatively recent [34, 133, 282]. This approach has been attended by the driving forces from the two most advanced groups of regulatory documents ([Figure 2.2](#Ch03.xhtml#cap_lbl0149)):

![Figure 2.1 Principles, framework and risk management process from ISO 31000:2018.](Images/fig00113.jpg)

[**Figure 2.1**](#Ch03.xhtml#bck_cap_lbl0148) Principles, framework and risk management process from ISO 31000:2018.

*   □ Standards and recommendations for `IT risks management` within the entire company (there is a large group of standards among which the `Australian standard is clearly distinguished' AS/NZS 4360 (2004)`. First of all, due to the wide practical application, and secondly, due to the fact that several related and developing documents, such as - `HandBook 231` `Information security risk management guidelines`, `HandBook 240` `Guidelines for managing risk in outsourcing` and `Information Security Risk Management Guideline for NSW Goverment` are directly related to risk management in IT). Currently, the standard `AS/NZS 4360 (2004)` is the basis of the international standard `ISO 31000:2018-Risk management-Guidelines`;
*   □ Set of standards `ISO/IEC 27000 (ISO/IEC 17799:2000)`, `ISO/IEC 15408` and `ISO/IEC 22300 (BS 25999:2006)` for cyber security management and business continuity, respectively.

![Figure 2.2 Evolution of cyber risk management standards.](Images/fig00120.jpg)

[**Figure 2.2**](#Ch03.xhtml#bck_cap_lbl0149) Evolution of cyber risk management standards.

As a result, these driving forces have generated several national guidelines and standards, which have been recognized by the international community as the best cyber risk management practices [156, 234–[237](#Reference.xhtml#ref0241)]. Thus, the following publications have achieved the certain prominence:

*   – `Specific NIST publication (American Standards Institute) NIST SP 800-30 Guide for Conducting Risk Assessments`^();
*   \- Guidelines and the method `OCTAVE - Operationally Critical Threat, Asset and Vulnerability Evaluation` of the initiative group of specialists from the `Carnegie Mellon University (Software Engineering Institute (SEI) at Carnegie Mellon University)`^();
*   \- `Canadian governmental guide to security risk management for information technology systems MG-2` `MG-2 (A Guide to Security Risk Management for Information Technology Systems)` (having the status of recommendations for government agencies)^();
*   \- Highly specialized IT risk management recommendations, including the Australian security outsourcing guidelines, Risk management guidelines for software acquisition capability at `Carnegie Mellon University (SACMM) (Software Acquisition Capability Maturity Model)`^().

The main goals of the specialized standards and risk management guidelines are the following [212, [283](#Reference.xhtml#ref0287), [284](#Reference.xhtml#ref0288)]:

*   □ Filling a void between the senior management, operating with terms of business processes, business continuity and sustainability, and the technicians operating with terms of vulnerabilities and technical/organizational security tools;
*   □ Specifying the adequate organizational and technical tools required for proper cyber security ([Figures 2.3](#Ch03.xhtml#cap_lbl0150) and [2.4](#Ch03.xhtml#cap_lbl0151)).

![Figure 2.3 Generic algorithm of cyber risk management.](Images/fig00123.jpg)

[**Figure 2.3**](#Ch03.xhtml#bck_cap_lbl0150) Generic algorithm of cyber risk management.

![Figure 2.4 Role and place of cyber risk management.](Images/fig00124.jpg)

[**Figure 2.4**](#Ch03.xhtml#bck_cap_lbl0151) Role and place of cyber risk management.

These are the following key terms in this area [89–[91](#Reference.xhtml#ref0092)]:

*   □ `Cyber risk` - a combination of an event probability and its consequences;
*   □ `Vulnerability` - is an error or a defect of organizational processes, structure or implementation of technical means which can cause (accidentally or deliberately) violation of cyber resilience (cyber security);
*   □ `Threat` - a potential for implementation of a certain vulnerability;
*   □ `Impact` - a degree and form of damage caused to the asset by the vulnerability realization.
*   □ `Cyber risk management` is a set of the coordinated events to manage the company (both the components of informational infrastructure and means of resiliency and cyber security, and the entire vertical of management in general) in order to minimize the overall cyber risk.
