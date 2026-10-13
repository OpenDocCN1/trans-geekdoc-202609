
![Warning](images/warning.png)Don’t confuse confidentiality with privacy: Confidentiality is a subset of the realm of privacy. It deals specifically with protecting data from unauthorized viewers, whereas privacy in general encompasses much more.

Hackers that steal data undermine confidentiality.

*   **Integrity** refers to ensuring that data is both accurate and complete.

    *Accurate* means, for example, that the data is never modified in any way by any unauthorized party or by a technical glitch. *Complete* refers to, for example, data that has had no portion of itself removed by any unauthorized party or technical glitch.

    Integrity also includes ensuring *nonrepudiation,* meaning that data is created and handled in such a fashion that nobody can reasonably argue that the data is not authentic or is inaccurate.

    Cyberattacks that intercept data and modify it before relaying it to its destination — sometimes known as *man-in-the-middle attacks* — undermine integrity.

*   **Availability** refers to ensuring that information, the systems used to store and process it, the communication mechanisms used to access and relay it, and all associated security controls function correctly to meet some specific benchmark (for example, 99.99 percent uptime). People outside of the cybersecurity field sometimes think of availability as a secondary aspect of information security after confidentiality and integrity. In fact, ensuring availability is an integral part of cybersecurity. Doing so, though, is sometimes more difficult than ensuring confidentiality or integrity. One reason that this is true is that maintaining availability often requires involving many more noncybersecurity professionals, leading to a “too many cooks in the kitchen” type challenge, especially in larger organizations. Distributed denial-of-service attacks attempt to undermine availability. Also, consider that attacks often use large numbers of stolen computer power and bandwidth to launch DDoS attacks, but responders who seek to ensure availability can only leverage the relatively small amount of resources that they can afford.

## From a Human Perspective

The risks that cybersecurity addresses can also be thought of in terms better reflecting the human experience:

*   **Privacy risks:** Risks emanating from the potential loss of adequate control over, or misuse of, personal or other confidential information.

*   **Financial risks:** Risks of financial losses due to hacking. Financial losses can include both those that are direct — for example, the theft of money from someone’s bank account by a hacker who hacked into the account — and those that are indirect, such as the loss of customers who no longer trust a small business after the latter suffers a security breach.

*   **Professional risks:** Risks to one’s professional career that stem from breaches. Obviously, cybersecurity professionals are at risk for career damage if a breach occurs under their watch and is determined to have happened due to negligence, but other types of professionals can suffer career harm due to a breach as well. C-level executives can be fired, board members can be sued, and so on. Professional damage can also occur if hackers release private communications or data that shows someone in a bad light — for example, records that a person was disciplined for some inappropriate action, sent an email containing objectionable material, and so on.

*   **Business risks:** Risks to a business similar to the professional risks to an individual. Internal documents leaked after breach of Sony Pictures painted various the firm in a negative light vis-à-vis some of its compensation practices.

*   **Personal risks:** Many people store private information on their electronic devices, from explicit photos to records of participation in activities that may not be deemed respectable by members of their respective social circles. Such data can sometimes cause significant harm to personal relationships if it leaks. Likewise, stolen personal data can help criminals steal people’s identities, which can result in all sorts of personal problems.

*   **Physical danger risks:** Cyberattacks on sewage treatment plants, utilities, and hospitals in recent years have shown clearly that the failure to maintain cybersecurity can lead to the endangering of human lives. For example, in 2020, a woman in Germany died while being transported between hospitals after the hospital at which she had been a patient was struck by ransomware. And in 2021, a lawsuit was filed arguing that a baby died as a result of medical mistakes made as she was born at a hospital in Alabama during system outages caused by a ransomware attack.

# Chapter 2: Getting to Know Common Cyberattacks

## In This Chapter

*   **Exploring attacks that can inflict damage**
*   **Discovering the difference between impersonation, data interception, and data theft**
*   **Looking at the various types of malware, poisoning, and malvertising**
*   **Finding out about advanced forms of cyberattacks**

Many different types of cyberattacks exist — so many that I could write an entire series of books about them and add many new chapters every year. In this book, however, I do not cover all types of threats in detail because the reality is, you’re likely reading this book to learn about how to keep yourself cybersecure, not to learn about matters that have no impact on you, such as forms of attacks that are normally directed at espionage agencies, industrial equipment, or military armaments.

In this chapter, you find out about the different types of problems that cyberattackers can create through the use of attacks that commonly impact individuals and small businesses.

## Attacks That Inflict Damage

Attackers launch some forms of cyberattacks with the intent to inflict damage to victims. The threat posed by such attacks is not that a criminal will directly steal your money or data, but that the attackers will inflict harm to you in some other specific manner — a manner that may ultimately translate into financial, military, political, physical, or other benefit to the attacker and (potentially) damage of some sort to the victim.

Types of attacks that inflict damage include:

*   Denial-of-service (DoS) attacks
*   Distributed denial-of-service (DDoS) attacks
*   Botnets and zombies
*   Data destruction attacks

### Denial-of-service (DoS) attacks

A *denial-of-service (DoS) attack* is one in which an attacker intentionally attempts to either partially cripple or totally paralyze a computer or computer network by flooding it with large amounts of requests or data, which overload the target and make it incapable of responding properly to legitimate requests.

In many cases, the requests sent by the attacker are each, on their own, legitimate — for example, a normal request to load a web page. In other cases, the requests aren’t normal requests. Instead, they leverage knowledge of various protocols to send requests that optimize, or even magnify, the effect of the attack.

In any case, denial-of-service attacks work by overwhelming computer systems’ central processing units (CPUs) and/or memory, utilizing all the available network communications bandwidth, and/or exhausting networking infrastructure resources such as routers.

### Distributed denial-of-service (DDoS) attacks
