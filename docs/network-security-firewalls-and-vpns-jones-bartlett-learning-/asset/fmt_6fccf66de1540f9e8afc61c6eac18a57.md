
## 24. What feature or function in tunnel mode encryption is not supported in transport mode encryption?

A. The header is encrypted.

B. The payload is encrypted.

C. The source address is encrypted, but not the destination address.

D. A footer is added to contain the hash value.

E. It provides encryption protection from the source of a conversation to the destination.

## 25. All of the following statements are true *except*:

A. Encryption ensures VPN traffic remains confidential.

B. It is possible to have a private VPN without encryption.

C. VPN authentication ensures only valid entities can access the secured connection.

D. Authorization over a VPN consists exclusively of granting or denying access to file resources.

E. VPN authentication can include multifactor options.

# CHAPTER 4 Network Security Threats and Issues

**NETWORK SECURITY IS UNDER CONSTANT ATTACK** by threats both internal and external, ranging from disgruntled employees to worldwide hackers. There’s no perfect defense because hackers are able to bypass, compromise, or evade almost every safeguard, countermeasure, and security control. Hackers are constantly developing new techniques of attack, writing new exploits, and discovering new vulnerabilities. Network security is a task of constant vigilance, not a project to complete. It’s a job that’s never done.

Why is understanding hacking, exploitation, vulnerabilities, and attacks critically important? As the sixth century B.C. Chinese military strategist and philosopher Sun Tzu stated in his famous military text *The Art of War*: “If you know the enemy and know yourself you need not fear the results of a hundred battles.” Once you understand how hackers think, the tools they use, their exploits, and their attack techniques, you can then create effective defenses to protect against them. Understanding hacking not only improves network security; it also maintains security at a high level of readiness.

## Chapter 4 Topics

This chapter covers the following topics and concepts:

- What motivates hackers to attack computer networks
- Which assets attackers frequently target
- Which internal or external threats networks are vulnerable to
- What common IT infrastructure threats are
- What the various types of malicious code (malware) are and what the security concerns about them are
- What fast growth and overuse are
- What wireless and wired connections are
- What the risk of eavesdropping is
- What a replay attack is and how it is performed
- What an insertion attack is
- What fragmentation attacks, buffer overflows, and XSS attacks are
- What man-in-the-middle, session hijacking, and spoofing attacks are
- What covert channels are and how a hacker uses them
- What threats to network and resource availability are
- How a denial of service (DoS) functions
- What a distributed denial of service (DDoS) is
- What some common hacker tools are
- Who is at risk from social engineering

## Chapter 4 Goals

When you complete this chapter, you will be able to:

- Describe the motivations of hackers and other malicious computer network intruders
- Compare and contrast threats from internal and external sources
- Describe how accidents, natural disasters, and ignorance affect network security
- Explain the risk posed by malicious code
- Express the effects of wired and wireless connectivity on network security
- Describe common network security exploits and attacks, including replay attacks, insertion attacks, fragmentation attacks, buffer overflow attacks, XSS attacks, man-in-the-middle attacks, hijacking attacks, spoofing attacks, covert channels, DoS, DDoS, botnet attacks, and social engineering attacks
- Demonstrate how hacker tools exploit vulnerable targets

## Hacker Motivation

What motivates hackers to attack computer networks? Why does anyone get involved in illicit activity outside the mainstream? The motives are as numerous as there are ways of conducting the computer attacks: Many do it for the sheer thrill of hacking, for the sport of it. Some hackers consider hacking their hobby. Some love a challenge. Some are victims of peer pressure or are seeking social validation. To still others, hacking is a status trip. And finally, many hackers pursue their exploits for power and financial gain. Take a look at some of these motives in more detail to see if you can begin to understand the hacker mentality.

Many criminal hackers are in it simply for the money. There are many ways of gaining financially from attacking computer networks. These range from theft of credit cards and financial statements to blackmail and black markets. Some monetary gain is immediate. Hackers might be able to transfer funds out of a target account, for example. Other methods are more involved, such as stealing corporate documents and selling them to competitors or hijacking data using encryption and holding it for ransom. Hackers can become involved in selling their services, including distributing `spam`, eavesdropping, cracking passwords, and generating DoS events.

Demonstrating the ability to compromise a target, especially if the target is reasonably secure, is a way for hackers to prove they are more powerful than the defenders. If you can control something, you have power over it. If a hacker can control your computer remotely, then the hacker has power over your computer, and in some ways has power over you as well. Hackers sometimes hack as an ego boost. If they can wage a successful attack, then they are showing dominance over their target.

For many hackers, it’s an exciting challenge to find new vulnerabilities, develop new attack code, or discover new security breaches. Some hackers attack targets for the same reasons some people climb mountains—because it’s there, because they can, and because they want to beat it. Some hackers continually seek out new, more difficult targets to improve their skills and increase the level of the challenge.

Some hackers enjoy the sheer risk of attacking a network. As with any crime, the risk of being caught is always a possibility. A target network might have `honeypots`, IDSs, IPSs, firewalls, and other technical defenses that the hacker will need to detect and evade. Security professionals are always looking to discover new attack techniques and learn the identity of hackers. With every attack, therefore, the hacker is at risk of getting caught and prosecuted.

Hacking can be thrilling. Think of the way a treasure hunter on private property feels. The combination of power, challenge, risk, and potential pursuit along with discovering potentially valuable assets is a thrill for some hackers. The thrill of getting away with it motivates many hackers to continue their attacks once they figure out how to successfully hack into a network.

Some hackers have few exciting or engaging aspects of their life and they resort to hacking as an attempt to be entertained or distracted from their boredom. A successful system breach will usually initiate a response, often a cat-and-mouse game that is more entertaining for hackers than anything else they can think of at the moment.
