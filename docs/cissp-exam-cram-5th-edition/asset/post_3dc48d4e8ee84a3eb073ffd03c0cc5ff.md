
destination addresses cannot be seen by someone sniffing traffic. For example, think of a police TV series that pulls a pen register on a phone. The police officers see a list of numbers the phone has called, the times, and the durations of the calls. While the officers cannot hear what was said on the calls, they can derive useful information about the frequency and duration of calls. IP headers can provide similar information about endpoints.

> **Note**
>
> A man-in-the-middle attack may be used against link encryption to see the routing information and perform traffic analysis, which involves looking at the source and destination IP addresses to determine what systems are communicating and how often they are communicating.

- **End-to-end encryption**: This type of encryption is generally performed by the end user, who can pass through each node without further processing. However, source and destination addresses are passed in plaintext, so they can be seen by someone sniffing traffic.

Data can be encrypted using either of these two methods with or without the IP header being encrypted. With both link encryption and end-to-end encryption, the confidentiality of data is protected. If a VPN is set up to use link encryption, the IP information is encrypted, as is the data traffic.

> **Caution**
>
> Because link encryption requires the encryption of the IP header, it would be very difficult to use it for routing over a LAN or the Internet; each routing device would have to have a copy of the secret key used.

## Endpoint Security

A review of logical asset security would not be complete without a discussion of endpoint security. Endpoint security consists of the controls placed on client or end-user systems, such as antivirus, anti-malware, anti-spyware, and so on. Much of the IT security world has moved to a zero-trust environment, in which networked devices, such as laptops, are not trusted by default, even if they are connected to a managed corporate network.

Other controls placed on a client system, including the following, are also very important:

- Removable media: Malware is commonly propagated via USB thumb drive. Malware such as Stuxnet, Conficker, and Flame were all able to spread using thumb drives. Removable drives should be restricted and turned off when possible.

- Disk encryption: Disk encryption software such as PGP and BitLocker can be used to encrypt the contents of desktop and laptop hard drives. Also, corporate smartphones and tablets should have encryption enabled.

- Application whitelisting: This approach only allows known good applications and software to be installed, updated, and used. Whitelisting techniques can include code signing, digital certificates, known good cryptographic hashes, or trusted full paths and names. Blacklisting, on the other hand, involves blocking known bad software from being downloaded and installed.

- Host-based firewalls: For defense in depth, a company should consider not just enterprise firewalls but also host-based firewalls.

- Configuration lockdown: Not just anyone should have the ability to make changes to equipment or hardware. Configuration controls can be used to prevent unauthorized changes.

- Antivirus: Antivirus software is the most commonly deployed endpoint security product. While it is still a needed component, traditional, signature-based antivirus has become much less effective over the past several years as AI driven solutions have increased market share.

One basic starting point is to apply the principle of least privilege to each logical asset: Each computer, system component, or process should have the least authority necessary to perform its duties.

## Baselines

A *baseline* is a standard of security. Baselines are usually mapped to industry standards. For example, an organization might specify that all computer systems must be certified to Common Criteria Evaluation Assurance Level (EAL) 3. Another example of baselining can be seen in NIST 800-53, which describes a tailored baseline as a starting point for determining the needed level of security (see Figure 2.4).

Some methods used to establish baselines includes the following:

- **IT structure analysis (survey)**: Analysis of technical, operation, and physical aspects of the organization, division, or group.

- **Assessment of protection needs**: Determination of the needed level of protection. This activity can be quantitative or qualitative.

- **Selection of actions**: Determination of what specific controls need to be implemented.

- **Running comparison of nominal and actual**: Periodic review of activities and actions to measure the change between what was previously occurring and what is currently occurring.

## Baselines Provided by Special Publication 800-53

**Master Security Control Catalog**
Complete Set of Security Controls and Control Enhancements

| Category | Baseline | Description |
|---|---|---|
| Minimum Security Controls – Low Impact Information Systems | Baseline #1 | Selection of a subset of security controls from the master catalog—consisting of basic level controls |
| Minimum Security Controls – Moderate Impact Information Systems | Baseline #2 | Selection of a subset of security controls from the master catalog—consisting of basic level controls, plus additional controls and control enhancements, as needed |
| Minimum Security Controls – High Impact Information Systems | Baseline #3 | Selection of a subset of security controls from the master catalog—consisting of basic level controls, plus additional controls and control enhancements, as needed |

**Figure 2.4** NIST 800-53 Scoping and Baselining Controls

NIST 800-53 specifies scoping or tailoring activities and categorizes information based on impact (low, moderate, or high).

- Low impact
- Moderate impact
- High impact

Scoping or tailoring determines how standards are used to get the right level of protection for an organization. Scoping is the process of determining which portions of a standard will be implemented by an organization. For example, a high-security facility may decide not to deploy Wi-Fi and might state that Wi-Fi standards are out of scope and shall not apply. Tailoring is the process of customizing a standard for an organization.

NIST 800-52 (Security and Privacy Controls for Federal Information Systems and Organizations) describes the tailoring process:

- 1. Identify and designate common controls in initial security control baselines.

- 2. Apply scoping considerations to the remaining baseline security controls.

- 3. Select compensating security controls, if needed.

- 4. Assign specific values to organization-defined security control parameters (such as password complexity policies) via explicit assignment and selection statements.

- 5. Supplement baselines with additional security controls and control enhancements, if needed.

- 6. Provide additional specification information for control implementation, if needed.

> **ExamAlert**
>
> The CISSP exam will expect you to understand terms such as scoping, tailoring, and supplementation. For example, you might reduce the standard logout time from 24 hours to 8 hours.
> *Supplementation* is the addition of specific details to your specified controls. For example, you might replace the term *cloud hosting* with *Microsoft Azure*.

By scoping a project to remove items, you might be able to reduce costs, but in doing so, you might expose the system to unnecessary threats. Therefore, due care must be used to determine the proper level of controls. Scoping and tailoring activities should be well documented with appropriate justification. In some cases, information and information systems must be protected regardless of the cost because of laws that govern certain industries.

## Exam Prep Questions

- 1. Which of the following levels does the military classification system include?

- A. Confidential, private, sensitive, and public

- B. Top secret, secret, private, sensitive, and public

- C. Top secret, confidential, private, sensitive, and unclassified

- D. Top secret, secret, confidential, sensitive, and unclassified

- 2. Your company is considering implementing NIST 800-53. Which of the following terms refers to the process of modifying security controls to align with the mission of the organization?

- A. Standards selection

- B. Tailoring

- C. Scoping

- D. Conforming

- 3. Which of the following endpoint security controls could have been used to potentially prevent malware such as Stuxnet, Conficker, and Flame?

- A. Implementing disk encryption

- B. Hardening edge devices

- C. Blocking removable media

- D. Enforcing application whitelisting

- 4. Which of the following shows the proper order?

- A. Determine SLE, ARO, and ALE and then asset value.

- B. Determine asset value and then ARO, SLE, and ALE.

- C. Determine asset value and then SLE, ALE, and SLE.

- D. Determine asset value and then SLE, ARO, and ALE.

- 5. With which of the following assessment types do you not work with dollar values, which can make it difficult to communicate the results of the assessment to management?

- A. Qualitative
