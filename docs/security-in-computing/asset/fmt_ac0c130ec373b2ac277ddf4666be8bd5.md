
## 9. Privacy

***

In this chapter:

*   Privacy as an aspect of security; confidentiality
*   Authentication effects on privacy
*   Privacy and the Internet

***

Computers did not invent or even cause privacy issues; we had those long before computers and probably even before written language. But computers’ high-speed processing and data storage and transmission capabilities made possible both the data collection and correlation that affect privacy. Because privacy is part of confidentiality, it is an aspect of computer security.

Privacy is a human right, although people can legitimately disagree over when or to what extent privacy is deserved; this disagreement may have cultural, historical, or personal roots. Laws and ethics, which we study in [Chapter 12](#ch12.html#ch12), can set the baseline for and enforce expectations of privacy. And economics, which we address in [Chapter 13](#ch13.html#ch13), can determine how much privacy we are able or willing to provide. But at its root, the right to privacy depends on the situation in which privacy is desired, the ownership and persistence of data, and the legal rights and responsibilities of the affected parties. Moreover, just as confidentiality, integrity, and availability can conflict, so too can privacy and other aspects of security. We don’t take a position on when a right to privacy should be enforceable, because that is outside the scope of this book. You might characterize the presentation of this chapter this way: “Assuming a particular right to privacy exists, what are its implications in computing and information technology?” As citizens, we help our policy-makers decide the contours of privacy rights; as computer security experts, we design and implement those decisions in computer systems.

Because privacy as a topic is broader than its implications for security, we restrict ourselves in this chapter only to those privacy issues inextricably linked to computer security. Thus, in this chapter we look at the meaning of information privacy. We revisit identification and authentication, two familiar aspects of computing that have significant privacy implications. We study how privacy relates to the Internet, specifically in email and web access. Finally, we investigate some emerging computer-based technologies for which privacy is important.

### 9.1 Privacy Concepts

In this section we examine privacy, first from its general or common usage and then as it applies in technological situations.

#### Aspects of Information Privacy

Information privacy has three aspects: sensitive data, affected parties, and controlled disclosure. In fact, these aspects are similar to the three elements of access control from [Chapter 2](#ch02.html#ch02): subject, object, and access rights. We examine these three in turn.

##### Controlled Disclosure

What is privacy? A good working definition is that privacy is the right to control who knows certain aspects about you, your communications, and your activities. In other words, you voluntarily choose who can know which things about you. People may ask you for your telephone number: your auto mechanic, a shop clerk, your tax authority, a new business contact, or a new friend. In each case, you consider why the person wants the number and then decide whether to give it out. But the key point is that *you* decide. So privacy is something over which you can have considerable influence.

***

**Privacy is the right to control who knows certain things about you.**

***

You do not have complete control, however. Once you give your number to a person or a system, your control is diminished because it depends in part on what the person or system does with that information. In giving out your number, you are transferring or ceding authority and control to someone or something else. You may say “don’t give my number to anyone else,” “use discretion,” or “I am sensitive about my privacy,” but you do not control the other person or system. You have to trust the person or system to comply with your wishes, whether you state those wishes explicitly or not. This problem is similar to the propagation problem of computer security: Anyone who has access to an object can copy, transfer, or propagate that object or its content to others without restriction. And even if you specify that the object should be deleted or destroyed after a certain period of time, you have no way to verify that the system or person really does destroy the content.

##### Sensitive Data

Someone asks you for your shoe size. You might answer, “I’m a very private person and cannot imagine why you would want to know such an intimate detail” or you could say “10C”; some people find that data item more sensitive than others. Some information is usually considered sensitive, such as financial status, certain health data, unsavory events in someone’s past, and the like. So if you learn something you consider sensitive about someone, you are likely to keep it quiet, unless there is a compelling argument for revealing it. For example, in many places, healthcare professionals (interested in disease identification, containment, and prevention) are required to report instances of highly communicable or deadly diseases, even if the stricken person does not want that information to be made public. But most of us are not too sensitive about our shoe size, so we don’t normally protect that information if asked, or if we learn it about someone else. In most cases, we respect requests to protect someone’s sensitive information.

Here are examples (in no particular order) of types of data many people consider private.

*   **Identity**: name, identifying information, the ownership of private data and ability to control its disclosure
*   **Finances**: credit rating and status, bank details, outstanding loans, payment records, tax information
*   **Legal**: criminal records, marriage history, civil suits
*   **Health**: medical conditions, drug use, DNA, genetic predisposition to illnesses
*   **Opinions, preferences, and membership**: voting records, expressed opinions, membership in advocacy organizations, religion, political party, sexual preference, reading habits, web browsing, favorite pastimes, close friends
*   **Biometrics**: physical characteristics, polygraph results, fingerprints
*   **Documentary evidence**: surface mail, diaries, poems, correspondence, recorded thoughts
*   **Privileged communications**: with professionals such as lawyers, accountants, doctors, counselors, and clergy
*   **Academic and employment information**: school records, employment ratings
*   **Location data**: general travel plans, current location, travel patterns
