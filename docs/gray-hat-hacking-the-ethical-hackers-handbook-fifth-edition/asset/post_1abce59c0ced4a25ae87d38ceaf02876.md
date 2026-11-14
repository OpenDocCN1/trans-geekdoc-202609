
used to protect us can also be used to attack us. The criminal community has evolved to abuse technology on a scale that brings in enormous profits, costing the global economy an estimated $450 billion a year.

Respect your enemy. Malicious actors have a variety of motivations and tactics, and the scale and complexity of their attacks are increasing. Consider the following:

- In February 2016, attackers targeted Swift, a global bank transfer system, and fraudulently transferred $81 million from the Bangladesh Bank’s account at the Federal Reserve Bank of New York. Most funds were not recovered after being routed to accounts in the Philippines and diverted to casinos there.¹

- In July 2016, it was discovered that the Democratic National Committee (DNC) was compromised and damaging e-mails from officials were leaked on WikiLeaks. The attack was attributed to two Russian adversary groups. The CIA concluded that Russia worked during the 2016 US election to prevent Hillary Clinton from winning the US presidency.²

- In October 2016, millions of insecure Internet of Things (IoT) cameras and digital video recorders (DVR) were used in a distributed denial-of-service (DDoS) attack targeting Dyn, a DNS provider. The Mirai botnet was used to take down the likes of Twitter, Netflix, Etsy, GitHub, SoundCloud, and Spotify a month after its source code was released to the public.³

- In December 2016, Ukraine’s capital Kiev experienced a power outage caused by a cyberattack affecting over 225,000 people for multiple days. The attackers sabotaged power-distribution equipment, thus complicating attempts to restore power. The attack prompted discussions about the vulnerabilities in industrial control systems (ICSs) and was linked to Russia.⁴

In recent years, we’ve seen the Federal Bureau of Investigation (FBI), Department of Homeland Security (DHS), Sony Entertainment, Equifax, Federal Deposit Insurance Corporation (FDIC), and Internal Revenue Service (IRS) all have major breaches—sometimes multiple large breaches. We’ve seen hospitals like the infamous Hollywood Presbyterian Medical Center pay ransoms to be able to continue to operate. While some attacks have a larger impact than others, on average a cyberattack costs organizations about $4 million, with some breaches costing hundreds of millions of dollars.

The security industry is also evolving. Products designed to promote self-healing networks competed in the first DARPA Cyber Grand Challenge. Malware solutions based on machine learning are replacing signature-based solutions. Integrated Security Operations Centers (ISOCs) are helping the security field collaborate. Cybersecurity conferences, degree programs, and training are increasingly popular. The security industry is responding to increasing cyberattacks with new tools, ideas, and collaborations.

Attackers have different motivations. Some are financially motivated and aim to make the biggest profit possible, some are politically motivated and aim to undermine governments or steal state secrets, some are motivated by a social cause and are called hacktivists, and some are angry and just want revenge.

## Recognizing an Attack

When an attack occurs, there are always the same questions. How did the attacker get in? How long have they been inside the network? What could we have done to prevent it? Attacks can be difficult to detect, and bad actors can stay in the environment for a prolonged amount of time. Ethical hacking helps you learn how to recognize when an attack is underway or about to begin so you can better defend the assets you are protecting. Some attacks are obvious. Denial-of-service and ransomware attacks announce themselves. However, most attacks are stealth attacks intended to fly under the radar and go unnoticed by security personnel and products alike. It is important to know how different types of attacks take place so they can be properly recognized and stopped.

Some attacks have precursors—activities that can warn you an attack is imminent. A ping sweep followed by a port scan is a pretty good indication that an attack has begun and can be used as an early warning sign. Although tools exist to help detect certain activities, it takes a knowledgeable security professional to maintain and monitor systems. Security tools can fail, and many can be easily bypassed. Relying on tools alone will give you a false sense of security.

Hacking tools are just IT tools that are good when used for sanctioned purposes and bad when used for malicious purposes. The tools are the same, just applied toward different ends. Ethical hackers understand how these tools are used and how attacks are performed, and that’s what allows them to defend against these attacks. Many tools will be mentioned throughout this book. Tools that will help you recognize an attack are covered specifically in Chapters 7 and 8 as well as dispersed throughout the book.

## The Gray Hat Way

To get to the “ground truth” of their security posture and understand its risks, many organizations choose to hire an ethical hacker, or penetration tester, to perform attack simulations. A penetration tester will use the same tools and tactics as a malicious attacker, but in a controlled and secure way. This allows an organization to understand how a bad actor might get into the environment, how they might move around inside of the environment, and how they might exfiltrate data. This also enables the organization to determine the impact of attacks and identify weaknesses. Emulating attacks allows an organization to test the effectiveness of security defenses and monitoring tools. Defense strategies can then be refined based on lessons learned.

A penetration test is more than a vulnerability scan. During a vulnerability scan, an automated scanning product is used to probe the ports and services on a range of IP addresses. Most of these tools gather information about the system and software and correlate the information with known vulnerabilities. This results in a list of vulnerabilities, but it does not provide an idea of the impact those vulnerabilities could have on the environment. During a penetration test, attack emulations are performed to demonstrate the potential business impact of an attack. Testers go beyond creating a list of code and configuration vulnerabilities and use the perspective of a malicious attacker to perform controlled attacks. A penetration tester will chain together a series of attacks to demonstrate how a malicious attacker might enter the environment, move throughout the environment, take control of systems and data, and exfiltrate data out of the environment. They will use weaknesses in code, users, processes, system configurations, or physical security to understand how an attacker might cause harm. This includes creating proof-of-concept attacks, using social engineering techniques, and picking locks and cloning physical access badges.

In many instances, penetration tests demonstrate that an organization could potentially lose control of its systems and, sometimes more importantly, its data. This is especially significant in highly regulated environments or those with industry compliance requirements where penetration testing is often required. Penetration tests often justify the implementation of security controls and can help prioritize security tasks.

Tests will vary, depending on the information you have about the environment. Black box testing is when you begin with no prior knowledge of the environment. White box testing is when you are provided detailed information about the environment such as the IP address scheme and URLs. Gray box testing is when you start with no information about the environment and after demonstrating that you can penetrate the environment you are given information to make your efforts more efficient.

Also, the nature and duration of tests will vary widely. Assessments can be focused on a location, business division, compliance requirement, or product. The methodologies used for exploiting embedded devices are different from those used during red team assessments (both are described in later chapters). The variety of exploits described in this book, from ATM malware to Internet of Things exploits, are demonstrative of the fascinating variety of specialties available to ethical hackers.

## Emulating the Attack

This book includes information about many exploits and areas of ethical hacking. An overview of the ethical hacking process is provided here, and the process is further described in later chapters.

When you’re performing attack emulations, maintaining good communication with the assessment team and stakeholders is very important. Study the technical environment and ask questions that will allow you to formulate a plan. What is the nature of their business? What kind of sensitive information do they work with? Be sure the following areas are accounted for:

- Ensure everyone knows the focus of the assessment. Is this a compliance-focused penetration test that targets credit card data? Does the company want to focus on
