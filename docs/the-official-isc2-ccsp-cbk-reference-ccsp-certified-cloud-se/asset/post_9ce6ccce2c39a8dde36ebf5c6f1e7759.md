
- **Days to patch:** How long does it take a security team to fully patch a cloud system?
- **Access management:** How many users have administrative access?

A good method for communicating risks in a way that is easy to digest and understand is the risk register. As you have seen, a risk can be quantitatively expressed by multiplying a threat likelihood by the magnitude of impact.

**RISK** = Threat Likelihood × Magnitude of Impact

A risk register is a critical part of any incident response plan and provides a clear, visual way to see risks and their potential impacts. A risk register may contain the following (see Figure 6.3):

- A description of the risk
- The expected impact if the associated event occurs
- The probability of the event occurring
- Steps to mitigate the risk
- Steps to take should the event occur
- Rank of the risk

## Risk Assessment

| Risk Number | Risk Status | Data Identified | Risk Description | Impact (1–4) | Probability (1–4) | Risk Factor (I × P) | Mitigation Strategy/Status | Owner | Next Review or Expected Mitigation Date |
|---|---|---|---|---:|---:|---:|---|---|---|---|
| 1 | Retired | 22-Jul-15 | Security compromise becomes public before July 31st—before mitigation is finalized and verified with Microsoft and Mandiant. | 4 | 3 | 12 | Whack-a-mole and monitor very closely. Bring in Mandiant and Microsoft ASAP. (We are not ready to scramble to remediate today!) |  | 13-Aug-15 |
| 2 | Retired | 22-Jul-15 | Security compromise becomes public after July 31st—after mitigation finalized but before planned communication date/time. | 1 | 2 | 2 | Go dark and have an intense review before beginning to execute communication plan. (Each day beyond August 3rd, situation should gradually improve and risk will diminish.) |  | 14-Aug-15 |

**FIGURE 6.3** Risk register

Risk is not an exact science, and calculating/categorizing risk is a difficult exercise that must be revisited often. A risk register can be an important tool for decision-makers to have a clear picture of what risks can be avoided, modified, shared, or retained.

## Assessment of Risk Environment

As the cloud becomes more and more of a critical operating component for many companies, identifying and understanding the risks posed by a cloud service provider is vital for any company that’s using cloud services. Cloud providers are subject to change of business models, acquisition, and even bankruptcy and shutdown. It is important to consider a number of questions when considering a cloud service, vendor, or infrastructure provider.

- Is the provider subject to takeover or acquisition?
- How financially stable is the provider?
- In what legal jurisdiction(s) are the provider’s offices located?
- Are there outstanding lawsuits against the provider?
- What pricing protections are in place for services contracted?
- How will a provider satisfy any regulatory or legal compliance requirements?
- What does failover, backup, and recovery look like for the provider?

And on and on. It can be a daunting challenge for any cloud customer to perform due diligence on their provider. But because the company maintains all legal and regulatory obligations as the data controller, it is an important part of any vendor selection. Fortunately, there are some industry certifications that can help companies make informed selections and mitigate risk.

### ISO 15408-1:2009: The Common Criteria

The Common Criteria for Information Technology Security Evaluation is an international standard for information security certification. The evaluation process is designed to establish a level of confidence in a product or platform’s security features through a quality assurance process. This is done through testing laboratories where the product or platform is evaluated.

Most cloud service providers do not have common criteria evaluations, but many cloud-based products do. One common example relevant to CCSPs are security tools designed to be deployed in virtual environments.

Does Common Criteria evaluation mean that a product is secure? Not necessarily. Though Windows operating systems have received certification under the program, they have later been found to have major security flaws. In addition, CC does not include any study of the administrative or business processes of a company that produced a product or platform; it is merely an evaluation of the technical merits of the platform itself. An up-to-date list of certified products can be found at www.commoncriteriaportal.org/products.

### Cloud Security Alliance (CSA) STAR

It is worth revisiting the Security, Trust, and Assurance Registry (STAR) provided by the CSA (cloudsecurityalliance.org/star/levels) as a valuable tool in displaying transparency and assurance for cloud service providers. CSA STAR makes use of the cloud control matrix version 4.0. STAR consists of three levels of certification.

- Level 1, Self-Assessment, is a complimentary offering that documents the security controls provided by various cloud computing offerings, helping users assess the security of cloud providers they currently use or are considering using.
- Level 2, Attestation, is a collaboration between CSA and the AICPA to provide guidelines for CPAs to conduct SOC 2 engagements using criteria from the AICPA (Trust Service Principles, AT 101) and the CSA Cloud Controls Matrix. STAR Attestation provides for rigorous third-party independent assessments of cloud providers.
- Level 3, Continuous Auditing, consists of monitoring through automated processes that ensure security controls are monitored and validated at all times.

Since the registry of certified providers is publicly available, the STAR program makes it easy for a company to assess the relative risk of a provider and should certainly be consulted when assessing any new CSP.

## ENISA Cloud Certification Schemes List and Metaframework

ENISA has provided another resource that can be used by cloud security professionals to assess the relative risk of a cloud service provider. (See `resilience.enisa.europa.eu/cloud-computing-certification`.) The Cloud Certification Schemes List (CCSL) provides an up-to-date summary of existing certification schemes that could be relevant for cloud computing. The list as of 2020 is as follows:

- Certified Cloud Service, TÜV Rheinland
- CSA Attestation, OCF Level 2
- CSA Certification, OCF Level 2
- CSA Self-Assessment, OCF Level 1
- EuroCloud Self-Assessment
- EuroCloud Star Audit Certification
- ISO/IEC 27001 Certification
- Payment Card Industry Data Security Standard v3
- Leet Security Rating Guide
- Service Organization Control (SOC) 1
- Service Organization Control (SOC) 2
- Service Organization Control (SOC) 3
- Cloud Industry Forum Code of Practice

ENISA describes the Cloud Certification Schemes Metaframework (CCSM) as an extension of CCSL. (See Figure 6.4.) It is a metaframework of cloud certification schemes. The goal of the metaframework is to provide a neutral high-level mapping from the customer's network and information security requirements to security objectives in existing cloud certification schemes, which facilitates the use of existing certification schemes during procurement. The agency also provides an online tool where it is possible to select from 27 different security objectives to see how the relative certifications compare.

| CCSM security objectives | Certified Cloud Service - TÜV Rheinland | CSA Attestation - OCF Level 2 | CSA Certification - OCF Level 2 | CSA Self Assessment - OCF Level 1 | EuroCloud Self Assessment | EuroCloud Star Audit Certification | ISO/IEC 27001 Certification | Leet Security Rating Guide | Service Organization Control (SOC) 2 | Service Organization Control (SOC) 3 | Cloud Industry Forum Code of Practice |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Information security policy | • | • | • | • | • | • | • | • | • | • | • |
| Risk management | • | • | • | • | • | • |  | • | • | • | • |
| Security roles | • | • | • | • | • | • | • | • | • | • | • |
| Security in Supplier relationships | • | • | • | • | • | • | • | • | • | • | • |
| Background checks | • |  | • | • |  | • | • | • | • | • |  |
| Security knowledge and training | • | • | • | • |  | • | • | • | • | • | • |
| Personnel changes | • | • | • | • |  | • | • | • | • | • | • |
| Physical and environmental security | • | • | • | • | • | • | • | • | • | • | • |
| Security of supporting utilities | • | • | • | • |  | • | • | • | • | • | • |
| Access control to network and information systems | • | • | • | • | • | • | • | • | • | • | • |
| Integrity of network and information systems | • | • | • | • | • |  | • | • | • |  | • |
| Operating procedures | • | • | • | • |  | • | • | • | • | • | • |

**FIGURE 6.4** CSA CCSM online tool

## UNDERSTANDING OUTSOURCING AND CLOUD CONTRACT DESIGN

Outsourcing is defined as “the business practice of hiring a party outside a company to perform services and create goods that traditionally were performed in-house by the company’s own employees and staff.” (See www.investopedia.com/terms/o/outsourcing.asp.) Outsourcing was traditionally a practice undertaken by companies as a cost-cutting measure or to make use of outside expertise or specialization. As the practice gained favor, it affected a wide range of jobs, ranging from customer support to manufacturing to the back office.
