
**Audits and assessments monitor compliance with requirements.** Audits are externally commissioned, formal reviews of the capability of an organization to achieve its control objectives. Assessments are less rigorous reviews of security issues, often performed or commissioned by IT staff. Organizations providing services to other entities may wish to conduct a service organization controls (SOC) audit under SSAE 18.

## Review Questions

1.  Joe is authoring a document that explains to system administrators one way in which they might comply with the organization's requirement to encrypt all laptops. What type of document is Joe writing?

    1.  Policy
    2.  Guideline
    3.  Procedure
    4.  Standard

2.  Which one of the following statements is not true about compensating controls under PCI DSS?

    1.  Controls used to fulfill one PCI DSS requirement may be used to compensate for the absence of a control needed to meet another requirement.
    2.  Controls must meet the intent of the original requirement.
    3.  Controls must meet the rigor of the original requirement.
    4.  Compensating controls must provide a similar level of defense as the original requirement.

3.  What law creates privacy obligations for those who handle the personal information of European Union residents?

    1.  HIPAA
    2.  FERPA
    4.  GDPR
    4.  PCI DSS

4.  Which one of the following is *not* one of the five core security functions defined by the NIST Cybersecurity Framework?

    1.  Identify
    2.  Contain
    3.  Respond
    4.  Recover

5.  What ISO standard provides guidance on privacy controls?

    1.  27002
    2.  27001
    3.  27701
    4.  31000

6.  Which one of the following documents must normally be approved by the CEO or similarly high-level executive?

    1.  Standard
    2.  Procedure
    3.  Guideline
    4.  Policy

7.  Greg would like to create an umbrella agreement that provides the security terms and conditions for all future work that his organizations does with a vendor. What type of agreement should Greg use?

    1.  BPA
    2.  MOU
    3.  MSA
    4.  SLA

8.  What organization is known for creating independent security benchmarks covering hardware and software platforms from many different vendors?

    1.  Microsoft
    2.  Center for Internet Security
    3.  Cloud Security Alliance
    4.  Cisco

9.  What type of security policy often serves as a backstop for issues not addressed in other policies?

    1.  Account management
    2.  Data ownership
    3.  Code of conduct
    4.  Continuous monitoring

10.  Which one of the following would *not* normally be found in an organization's information security policy?

     1.  Statement of the importance of cybersecurity
     2.  Requirement to use AES-256 encryption
     3.  Delegation of authority
     4.  Designation of responsible executive

11.  Darren is working with an independent auditor to produce an audit report that he will share with his customers under NDA to demonstrate that he has appropriate security controls in place. The auditor will not be assessing the effectiveness of those controls. What type of audit report should Darren expect?

     1.  SOC 2 Type 1
     2.  SOC 2 Type 2
     3.  SOC 3 Type 1
     4.  SOC 3 Type 2

12.  Tonya discovers that an employee is running a side business from his office, using company technology resources. What policy would most likely contain information relevant to this situation?

     1.  NDA
     2.  AUP
     3.  Data ownership
     4.  Data classification

13.  What compliance obligation applies to merchants and service providers who work with credit card information?

     1.  FERPA
     2.  SOX
     3.  HIPAA
     4.  PCI DSS

14.  Which one of the following policies would typically answer questions about when an organization should destroy records?

     1.  Data ownership policy
     2.  Account management policy
     3.  Password policy
     4.  Data retention policy

15.  Colin would like to implement a security control in his accounting department that is specifically designed to detect cases of fraud that are able to occur despite the presence of other security controls. Which one of the following controls is best suited to meet Colin's need?

     1.  Separation of duties
     2.  Least privilege
     3.  Dual control
     4.  Mandatory vacations

16.  Which one of the following security policy framework components does not contain mandatory guidance for individuals in the organization?

     1.  Policy
     2.  Standard
     3.  Procedure
     4.  Guideline

17.  The board of directors of Kate's company recently hired an independent firm to review the state of the organization's security controls and certify those results to the board. What term best describes this engagement?

     1.  Assessment
     2.  Control review
     3.  Gap analysis
     4.  Audit

18.  Allan is developing a document that lists the acceptable mechanisms for securely obtaining remote administrative access to servers in his organization. What type of document is Allan writing?

     1.  Policy
     2.  Standard
     3.  Guideline
     4.  Procedure

19.  Which one of the following is not a common use of the NIST Cybersecurity Framework?

     1.  Describe the current cybersecurity posture of an organization.
     2.  Describe the target future cybersecurity posture of an organization.
     3.  Communicate with stakeholders about cybersecurity risk.
     4.  Create specific technology requirements for an organization.

20.  Which one of the following items is *not* normally included in a request for an exception to security policy?

     1.  Description of a compensating control
     2.  Description of the risks associated with the exception
     3.  Proposed revision to the security policy
     4.  Business justification for the exception

# Chapter 17

Risk Management and Privacy

Organizations face an almost dizzying array of cybersecurity risks, ranging from the reputational and financial damage associated with a breach of personal information to the operational issues caused by a natural disaster. The discipline of risk management seeks to bring order to the process of identifying and addressing these risks. In this chapter, we examine the risk management process and discuss a category of risk that is closely related to cybersecurity: the privacy and protection of personal information.

## Analyzing Risk

We operate in a world full of risks. If you left your home and drove to your office this morning, you encountered a large number of risks. You could have been involved in an automobile accident, encountered a train delay, or been struck by a bicycle on the sidewalk. We're aware of these risks in the back of our minds, but we don't let them paralyze us. Instead, we take simple precautions to help manage the risks that we think have the greatest potential to disrupt our lives.

In an `enterprise risk management` (`ERM`) program, organizations take a formal approach to risk analysis that begins with identifying risks, continues with determining the severity of each risk, and then results in adopting one or more `risk management` strategies to address each risk.

Before we move too deeply into the risk assessment process, let's define a few important terms that we'll use during our discussion:

*   `Threats` are any possible events that might have an adverse impact on the confidentiality, integrity, and/or availability of our information or information systems.
*   `Vulnerabilities` are weaknesses in our systems or controls that could be exploited by a threat.
*   `Risks` occur at the intersection of a vulnerability and a threat that might exploit that vulnerability. A threat without a corresponding vulnerability does not pose a risk, nor does a vulnerability without a corresponding threat.
