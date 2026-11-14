
testing its detection capabilities? Are you testing a new product that is being released soon?

- Set up secure communication channels with your stakeholders and other members of your communication team. Protect the output from your testing tools and reports. Use encrypted e-mail. Ensure your document repository is secure. Set up multifactor authentication on your e-mail, document repository, and anything that allows remote access to your testing or reporting environment.

- Define the scope of the assessment in writing and discuss it with your assessment team and stakeholders. Is social engineering in scope? How in depth should the website assessment be?

- Be sure to inquire about any fragile systems—that is, systems that have unexpectedly shut down, restarted, or slowed down recently or systems that are critical for business operations. Formulate a plan to address them.

- Describe your methodology in detail to your stakeholders or team. Talk about the rules of engagement. Should they try to stop your attack emulation if they detect it? Who should know about the testing? What should they tell users who report any testing activities?

- Remain accountable for your actions. Log and document all your testing activities. It's not uncommon to perform a penetration test only to discover you are not the first one to the party and that a breach is in progress. Be sure to discuss start and stop dates and blackout periods.

The typical steps of the penetration test are briefly described here and are discussed in more depth in following chapters:

- 1. Compile Open Source Intelligence (OSINT). Gather as much information about the target as possible while maintaining zero contact with the target. Compiling OSINT, otherwise known as "passive scanning," can include using the following:

  - Social networking sites
  - Online databases
  - Google, LinkedIn, and so on
  - Dumpster diving

- 2. Employ active scanning and enumeration. Probe the target's public exposure with scanning tools and the following techniques:

  - Network mapping
  - Banner grabbing
  - War dialing
  - DNS zone transfers
  - Traffic sniffing
  - Wireless war driving

- 3. Perform fingerprinting. Perform a thorough probe of the target systems to identify the following:

  - Operating system type and patch level
  - Applications and patch level
  - Open ports
  - Running services
  - User accounts

- 4. Select a target system. Identify the most useful target(s).

- 5. Exploit the uncovered vulnerabilities. Execute the appropriate attacks targeted at the suspected exposures. Keep the following points in mind:

  - Some may not work.
  - Some may kill services or even kill the server.
  - Some may be successful.

- 6. Escalate privileges. Escalate the security context so that you have more control.

  - Gain root or administrative rights.
  - Use cracked passwords for unauthorized access.
  - Carry out a buffer overflow attack to gain local versus remote control.

- 7. Preserve access. This step usually involves installing software or making configuration changes to ensure access can be gained later.

- 8. Document and report. Document everything you found, how it was found, the tools that were used, the vulnerabilities that were exploited, the timeline of activities, and successes, and so on. The best methodology is to report as you go, frequently gathering evidence and taking notes.

![](img/5f597c6a70133069118d9e804ace3775_39_0.png)

NOTE: A more detailed approach to the attacks that are part of each methodology are included throughout the book.

## What Would an Unethical Hacker Do Differently?

The following steps describe what an unethical hacker would do instead:

- 1. Select a target. Motivations could be due to a grudge or for fun or profit. There are no ground rules, no hands-off targets, and the security team is definitely blind to the upcoming attack.

- 2. Use intermediaries. The attacker launches their attack from a different system (intermediary) than their own, or a series of other systems, to make tracking back to them more difficult in case the attack is detected. Intermediaries are often victims of the attacker as well.

- 3. Proceed with the penetration testing steps described previously.

  - Open Source Intelligence gathering
  - Active scanning and enumeration
  - Fingerprinting
  - Select a target system
  - Exploiting the uncovered vulnerabilities
  - Escalating privileges

- 4. Preserve access. This involves uploading and installing a rootkit, back door, Trojan applications, and/or bots to ensure that the attacker can regain access at a later time.

- 5. Cover tracks. This step involves the following activities:

  - Scrubbing event and audit logs
  - Hiding uploaded files
  - Hiding the active processes that allow the attacker to regain access
  - Disabling messages to security software and system logs to hide malicious processes and actions

- 6. Harden the system. After taking ownership of a system, an attacker may fix the open vulnerabilities so no other attacker can use the system for other purposes.

Attackers will use compromised systems to suit their needs—many times remaining hidden in the network for months or years while they study the environment. Often, compromised systems are then used to attack other systems, thus leading to difficulty attributing attacks to the correct source.

## Frequency and Focus of Testing

Ethical hacking should be a normal part of an organization's operations. Most organizations would benefit from having a penetration test performed at least annually. However, significant changes to a technical environment that could have a negative impact on its security, such as operating system or application upgrades, often happen more than just once a year. Therefore, ongoing security testing is recommended for most organizations because of how quickly technical environments tend to change. Red teaming exercises and quarterly penetration testing are becoming more and more common.

Red teaming exercises are usually sanctioned but not announced. Your client will know you are authorized to test but often doesn't know when the testing will occur. Many red team assessments occur over a long period of time, with the goal of helping an organization refine its defenses—or *blue team* capabilities. Testing often runs over the duration of a year, with quarterly outbriefs and a variety of reports and other deliverables created to help an organization gauge progress. When the blue team, or defensive security team, sees an attack, they do not know if it's a real-world attack or a red teaming exercise and will begin their incident response process. This allows an organization to practice a "cat-and-mouse" game, where ethical hackers are helping the defensive security team test and refine their security controls and incident response capabilities. Red teaming is often reserved for organizations with more mature incident response capabilities. *Chapter 7* provides more information on this topic.

Many organizations are moving to a model where penetration tests occur at least quarterly. This allows these organizations to choose a different focus for each quarter. Many organizations align quarterly penetration testing with their change management process, thus ensuring testing activities take a thorough look at parts of the environment that have recently changed.

## Evolution of Cyberlaw

Cybersecurity is a complex topic, and cyberlaw adds many more layers of complexity to it. Cyberlaw reaches across geopolitical boundaries and defies traditional governance structures. When cyberattacks range across multiple countries or include botnets spread throughout the world, who has the authority to make and enforce laws? How do we apply existing laws? The challenges of anonymity on the Internet and difficulty of attributing actions to an individual or group make prosecuting attackers even more complex.

Governments are making laws that greatly apply to private assets, and different rules apply to protecting systems and data types, including critical infrastructure, proprietary information, and personal data. CEOs and management not only need to worry about profit margins, market analysis, and mergers and acquisitions; they also need to step into a world of practicing security with due care, understand and comply with new government privacy and information security regulations, risk civil and criminal liability for security failures (including the possibility of being held personally liable for certain security breaches), and try to comprehend and address the myriad ways in which information security problems can affect their companies.

## Understanding Individual Cyberlaws

Individual cyberlaws address everything from the prohibition of unauthorized account access to the transmission of code or programs that cause damage to computers. Some laws apply whether or not a computer is used and protect communications (wire, oral, and data during transmission) from unauthorized access and disclosure. Some laws pertain to copyrighted content itself and protect it from being accessed without authorization. Together these laws create a patchwork of regulation used to prosecute cybercrime. This
