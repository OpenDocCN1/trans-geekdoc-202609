
# Artificial Intelligence and Machine Learning in Security

Artificial Intelligence attempts to provide software and systems the ability to function in a manner that has historically been thought to only be available to human intelligence. Learning constitutes one of those characteristics of intelligence thought previously reserved for human intelligences that has long been a focus of study within artificial intelligence. "Machine Learning is the study of computer algorithms that improve automatically through experience" [[9]](#Ch008_361-457_B9780443187346000064_2.xhtml#bb0050). Machine Learning algorithms require vast quantities of training data that is processed by the algorithm with the goal of being able to successfully discern information as would a human intelligence. AI and ML have many potential applications to information security. A fundamental goal has been to leverage these tools' capabilities to differentiate malicious activity from benign. Monitoring-oriented applications such as User and Entity Behavior Analytics (UEBA), Security Information and Event Management (SIEM), and general intrusion detection seem particularly well-suited to benefit from artificial intelligence and machine learning.

## Third-Party Provided Security Services

Leveraging resources beyond one's own organization has become commonplace in security. Given the importance, ever-changing nature, and scope of security, dependence upon third-party providers comes as little surprise. The degree of control, scope of work, and expectations of the third parties vary drastically. Virtually every organization avails itself of hardware and software developed by external providers, but increasingly organizations also employ third parties for ongoing security services. Although the phrase Managed Security Service Provider (MSSP) does not encompass all the varied third-party security service offerings in the marketplace, it serves as a good example of a commonly employed service.

Though the justification, rationale, and functions can vary widely, the basic idea of employing an MSSP is to bolster an organization's security operations through leveraging a third party's staff and operational maturity. Finding security professionals to fill open positions has long proven challenging. However, even organizations that consider themselves fully staffed often struggle to keep up with the cadence and operational workload required for effective security operations. Many organizations will look to MSSPs as a form of security staff augmentation or security operations force multiplier. While not exclusively used for this purpose, an incredibly common function for which organizations seek outside assistance from MSSPs involves providing robust 24 × 7 × 365 detection and response capabilities.

## Honeypots

A `honeypot` is a system designed to attract attackers. This allows information security researchers and network defenders to better analyze network-based attacks. Honeypots have no production value beyond research.

Internal honeypots can provide high-value warnings of internal malware or attackers. While an internet-facing honeypot will be frequently compromised, internal honeypots should never become compromised. If this happens, it usually means that other preventive and detective controls, such as firewalls and IDSs, have failed.

Low-interaction honeypots simulate systems (or portions of systems), usually by scripting network actions (such as simulating network services by displaying banners). High-interaction honeypots run actual operating systems, in hardware or via virtualization.

Consult with legal staff before deploying a honeypot. There are legal and practical risks posed by honeypots: what if an attacker compromises a honeypot, and then successfully penetrates further into a production network? Could the attackers argue they were "invited" into the honeypot, and by extension the production network? What if an attacker penetrates a honeypot and then successfully uses it as a base to attack a third party? These risks should be considered before deploying a honeypot.

## Honeynets

A `honeynet` is a (real or simulated) network of honeypots. Traditional honeypots focus on offering instrumented decoy services or a single system. Honeynets involve an entire network of systems and services that lack any legitimate devices. As with the intent of the standard honeypot, the goal of a honeynet is to allow the organization to discover adversary activity. Honeynets can include a `honeywall` (honeynet firewall) that is intended to limit the likelihood of the honeynet being used to attack other systems.

# Asset Management

A holistic approach to operational information security requires organizations to focus on systems as well as the people, data, and media. Systems security is another vital component to operational security, and there are specific controls that can greatly help system security throughout the system's lifecycle.

## Configuration Management

One of the most important components of any systems security work is the development of a consistent system security configuration that can be leveraged throughout the organization. The goal is to move beyond the default system configuration to one that is both hardened and meets the operational requirements of the organization. One of the best ways to protect an environment against future zero-day attacks (attacks against vulnerabilities with no patch or fix) is to have a hardened system that only provides the functionality strictly required by the organization.

Development of a security-oriented baseline configuration is a time consuming process due to the significant amount of research and testing involved. However, once an organizational security baseline is adopted, then the benefits of having a known, hardened, consistent configuration will greatly increase system security for an extended period of time. Further, organizations do not need to start from scratch with their security baseline development, as different entities provide guidance on baseline security. These predefined baseline security configurations might come from the vendor who created the device or software, government agencies, or also the non-profit Center for Internet Security (see <https://www.cisecurity.org/>). Basic `configuration management` practices associated with system security will involve tasks such as: disabling unnecessary services, removing extraneous programs, enabling security capabilities like firewalls, antivirus, and intrusion detection or prevention systems, and the configuration of security and audit logs.

### Baselining
