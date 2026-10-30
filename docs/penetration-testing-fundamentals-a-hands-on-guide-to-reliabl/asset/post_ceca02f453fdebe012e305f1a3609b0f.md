
## Keep in Your Lane

We all have a set of skills. Hopefully, by completing this book and studying diligently, you will expand your skillset. But regardless of how much you expand your skills, there will always be limits. Be aware of your own limits and if a task is outside your skillset, then tell the client you are not the appropriate person for that specific test.

By way of example, I am reasonably competent at various aspects of cyber security and penetration testing, but I am completely unskilled in subjects such as physical penetration testing (actually trying to enter the target building) and social engineering. And some standards actually require an organization to do a physical penetration test. I always tell clients that they should hire someone else for that aspect of their testing. I am simply not very good at those things and it is unlikely that I can perform an adequate test. You might think being open about your shortcomings would cause you to lose clients, but I have found exactly the opposite. Many clients are very thankful for my honesty.

## If You Break It, You Bought It

In the process of penetration testing, you will be prodding someone’s systems—their computers, servers, devices, network, etc. It is entirely possible to cause a disruption to business. You must be very careful to avoid this.

One way you can minimize the chance of disrupting the client’s business is by conducting your test when the client has the least activity. This might be quite inconvenient for you (for example, conducting a website penetration test at 2 a.m. Sunday) but it is one way to protect your client’s systems.

The penetration testing contract should detail exactly what tests will be performed, at what times, and under what conditions. This will help clarify your role. You should take every step you can to minimize any disruption to the client’s system. With particularly sensitive systems, conducting tests on backup copies rather than the live system may be warranted.

## Legal Issues

As you progress through this book, you will learn a variety of hands-on hacking techniques. The intent is for you to utilize these skills in order to test an organization’s systems. Using these skills without explicit permission is a crime, and in many cases it can be multiple crimes. In this section, we look at several laws that affect hacking. The sections that follow cover the laws of which every penetration tester should be aware. The focus is primarily on U.S. laws, but a few laws from other countries are also discussed.

### Computer Fraud and Abuse Act (CFAA): 18 U.S. Code § 1030

This law is perhaps one of the most fundamental computer crime laws, and merits careful study by anyone interested in the field of computer crime. The primary reason to consider this legislation as pivotal is that it was the first significant federal legislation designed to provide some protection against computer-based crimes. Prior to this legislation, courts relied on common law definitions and adaptations of legislation concerning traditional, non-computer crimes in order to prosecute computer crimes.

Throughout the 1970s and early 1980s, the frequency and severity of computer crimes increased. In response to this growing problem, the Comprehensive Crime Control Act of 1984 was amended to include provisions to specifically address the unauthorized access and use of computers and computer networks. These provisions made it a felony offense to access classified information in a computer without authorization. They also made it a misdemeanor offense to access financial records in a computer system.

However, these amendments were not considered in and of themselves to be adequate. Thus, during 1985, both the House and the Senate held hearings on potential computer crime bills. These hearings eventually culminated in the Computer Fraud and Abuse Act (CFAA), enacted by Congress in 1986, which amended 18 USC § 1030. The original goal of this act was to provide legal protection for computers and computer systems that were in one of the following categories:

- Under direct control of some federal entity
- Part of a financial institution
- Involved in interstate or foreign commerce

As you can see, this law was aimed at protecting computer systems that came within the federal purview. This act made several activities explicitly criminal. First and foremost was accessing a computer without authorization in order to obtain any of the following types of information:

- National security information
- Financial records
- Information from a consumer reporting agency
- Information from any department or agency of the United States

### Unlawful Access to Stored Communications: 18 U.S. Code § 2701

The actual wording of the statute is as follows:

> Offense.—Except as provided in subsection (c) of this section whoever—
> (1) intentionally accesses without authorization a facility through which an electronic communication service is provided; or
> (2) intentionally exceeds an authorization to access that facility; and thereby obtains, alters, or prevents authorized access to a wire or electronic communication while it is in electronic storage in such system shall be punished as provided in subsection (b) of this section.

Both of these elements are germane to hacking techniques and to penetration testing. Note number 2, “intentionally exceeds an authorization to access.” Even if you have authorization, exceeding your mandate is not only unethical, it could be a federal crime. It should be noted that the first offense can get up to 5 years in prison. Up to 10 years incarceration is possible for further offenses.

### Identity Theft Enforcement and Restitution Act

This act was actually an extension of the 1984 Computer Fraud and Abuse Act. It was written in response to the growing threat of identity theft and the perceived inadequacy of existing laws. One of its most important provisions was to allow prosecution of computer fraud offenses for conduct not involving an interstate or foreign communication. This meant that purely domestic incidents occurring completely within one state were now prosecutable under federal law. Beyond that important provision, this act expanded the definition of cyber extortion to include threats to damage computer systems or steal data.

Another important aspect of this legislation was that it expanded identity theft laws to organizations. Prior to this, only natural persons could legally be considered victims of identity theft. Under this act organizations can also legally be considered victims of identity theft and fraud. This law also made it a criminal offense to conspire to commit computer fraud.

### Fraud and Related Activity in Connection with Access Devices: 18 U.S. Code § 1029

This is closely related to 18 U.S. Code § 1030 but covers access devices (such as routers). Essentially this law mimics USC 1030 but applies to devices used to access systems. What is most fascinating about this law, in my opinion, is that it also covers counterfeit access devices. Later in this book you will learn about rogue access devices and man-in-the-middle attacks. This law would expressly relate to that.

## State Laws

There are 50 different states within the United States, and it is beyond the scope of this book to cover the laws in each and every state. It is recommended that you consult the laws in any state in which you work as a penetration tester.

## International Laws

It is beyond the scope of this book to cover laws in every country. A good rule of thumb is that any access without permission is very likely to be a crime in any jurisdiction; however, we can cover a few prominent laws in this section.

### EU Directive 2013/40

On 3 September 2013, new EU Directive 2013/40 on attacks against information systems (the “Directive”) came into force. It is aimed at large-scale cyber attacks, and directs each member state to enact tougher criminal laws against cyber crimes.

### Saudi Arabia

Saudi Arabia has the Anti-Cyber Crime Law (Royal Decree No. M/17 dated 8 Rabi I 1428). Article 6 of that law provides for up to 5 years in prison and fines equivalent to about 800,000 U.S. dollars for a range of offences including

> “production, preparation, transmission, or storage of material impinging on public order, religious values, public morals, and privacy, through the information network or computers.”

### Jordan Information Systems and Cyber Crime Law

Also known as the Information Systems Crime Law of 2010, the following are a few excerpts from that law:

> “Anyone who intentionally accesses a website or information system in any manner without authorization or in violation or excess of an authorization, shall be punished by imprisonment for a term not less than one week and not exceeding three months, or by a fine of not less than (100) one hundred Dinars and not exceeding (200) two hundred Dinars, or both punishments.”

> “Anyone who installs, publishes or uses intentionally a program through an information network or information system, with the purpose of canceling, deleting, adding, destroying, disclosing, extinguishing, blocking, altering, changing, transferring, copying, capturing, or enabling others to view data or information, or obstructing, interfering, hindering, stopping the operation of an information system or preventing access to it, or altering a website or canceling it, destroying it, or altering its content or operating it, assuming its identity or the identity of the owner without authorization or in violation or excess of the authorization shall be punished by imprisonment for a term not less than three months and not exceeding one year or by a fine of not less than (200) two hundred Dinars and not exceeding (1000) one thousand Dinars, or both punishments.”

### Unauthorized Computer Access Law

This is a Japanese law dating to 1998, but still in force. It is broadly worded and thus can be applied to a wide range of activities. A few interesting excerpts from that law are given here:

> “An act of making available a specific use which is restricted by an access control function by making in operation a specific computer having that access control function through inputting into that specific computer, via telecommunication line, another person’s identification code for that access control function (to exclude such acts conducted by the access administrator who has added the access control function concerned, or conducted with the approval of the access administrator concerned or of the authorized user for that identification code);”
