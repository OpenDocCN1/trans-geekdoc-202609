
## INTRODUCTION

> *History teaches that wars begin when governments believe the price of aggression is cheap.*
> —Ronald Reagan

> *You can't say civilization don't advance...in every war they kill you in a new way.*
> —Will Rogers

> *The supreme art of war is to subdue the enemy without fighting.*
> —Sun Tzu

The purpose of this book is to provide individuals the information once held only by governments and a few black hat hackers. In this day and age, individuals stand in the breach of cyberwar, not only against black hat hackers, but sometimes against governments. If you find yourself in this position, either alone or as a defender of your organization, we want you to be equipped with as much knowledge of the attacker as possible. To that end, we submit to you the mindset of the gray hat hacker, an ethical hacker that uses offensive techniques for defensive purposes. The ethical hacker always respects laws and the rights of others, but believes the adversary may be beat to the punch by testing oneself first.

The authors of this book want to provide you, the reader, with something we believe the industry and society in general needs: a holistic review of ethical hacking that is responsible and truly ethical in its intentions and material. This is why we keep releasing new editions of this book with a clear definition of what ethical hacking is and is not—something our society is very confused about.

We have updated the material from the fourth edition and have attempted to deliver the most comprehensive and up-to-date assembly of techniques, procedures, and material with real hands-on labs that can be replicated by the readers. Thirteen new chapters are presented, and the other chapters have been updated.

In Part I, we prepare you for the battle with all the necessary tools and techniques to get the best understanding of the more advanced topics. This section moves quite quickly but is necessary for those just starting out in the field and others looking to move to the next level. This section covers the following:

- White, black, and gray hat definitions and characteristics
- The slippery ethical issues that should be understood before carrying out any type of ethical hacking activities
- Programming survival skills, which is a must-have skill for a gray hat hacker to be able to create exploits or review source code
- Fuzzing, which is a wonderful skill for finding 0-day exploits
- Reverse engineering, which is a mandatory skill when dissecting malware or researching vulnerabilities
- Exploiting with software-defined radios

In Part II, we discuss the business side of hacking. If you are looking to move beyond hacking as a hobby and start paying the bills, this section is for you. If you are a seasoned hacking professional, we hope to offer you a few tips as well. In this section, we cover some of the softer skills required by an ethical hacker to make a living:

- How to get into the penetration testing business
- How to improve the enterprise security posture through red teaming
- A novel approach to developing a purple team
- Bug bounty programs and how to get paid finding vulnerabilities, ethically

In Part III, we discuss the skills required to exploit systems. Each of these topics has been covered before, but the old exploits don’t work anymore; therefore, we have updated the discussions to work past system protections. We cover the following topics in this section:

- How to gain shell access without exploits
- Basic and advanced Linux exploits
- Basic and advanced Windows exploits
- Using PowerShell to exploit systems
- Modern web exploits
- Using patches to develop exploits

In Part IV, we cover advanced malware analysis. In many ways, this is the most advanced topic in the field of cybersecurity. On the front lines of cyberwar is malware, and we aim to equip you with the tools and techniques necessary to perform malware analysis. In this section, we cover the following:

- Mobile malware analysis
- Recent ransomware analysis
- ATM malware analysis
- Using next-generation honeypots to find advanced attackers and malware in the network

Finally, in Part V, we are proud to discuss the topic of Internet of Things (IoT) hacking. The Internet of Things is exploding and, unfortunately, so are the vulnerabilities therein.

In this section, we discuss these latest topics:

- Internet of Things to be hacked
- Dissecting embedded devices
- Exploiting embedded devices
- Malware analysis of IoT devices

We do hope you will see the value of the new content that has been provided and will also enjoy the newly updated chapters. If you are new to the field or ready to take the next step to advance and deepen your understanding of ethical hacking, this is the book for you.

![](img/5f597c6a70133069118d9e804ace3775_30_0.png)

NOTE To ensure your system is properly configured to perform the labs, we have provided the files you will need. The lab materials and errata may be downloaded from either the GitHub repository at https://github.com/GrayHatHacking/GHHv5 or the publisher's site, at www.mhprofessional.com.

## PART I

## Preparation

- Chapter 1 Why Gray Hat Hacking? Ethics and Law
- Chapter 2 Programming Survival Skills
- Chapter 3 Next-Generation Fuzzing
- Chapter 4 Next-Generation Reverse Engineering
- Chapter 5 Software-Defined Radio

## CHAPTER 1

### Why Gray Hat Hacking? Ethics and Law

The purpose of this book is to support individuals who want to refine their ethical hacking skills to better defend against malicious attackers. This book is not written to be used as a tool by those who wish to perform illegal and unethical activities.

In this chapter, we discuss the following topics:

- Know your enemy: understanding your enemy’s tactics
- The gray hat way and the ethical hacking process
- The evolution of cyberlaw

### Know Your Enemy

> “We cannot solve our problems with the same level of thinking that created them.”
> —Albert Einstein

The security challenges we face today will pale in comparison to those we’ll face in the future. We already live in a world so highly integrated with technology that cybersecurity has an impact on our financial markets, our elections, our families, and our healthcare.
Technology is advancing and the threat landscape is increasing. On the one hand, vehicles that are capable of autonomous driving are being mass-produced as smart cities are being developed. On the other hand, hospitals are being held for ransom, power grids are being shut down, intellectual property and secrets are being stolen, and cybercrime is a booming industry. In order to defend and protect our assets and our people, we must understand the enemy and how they operate. Understanding how attacks are performed is one of the most challenging and important aspects of defending the technology on which we rely. After all, how can we possibly defend ourselves against the unknown?

This book was written to provide relevant security information to those who are dedicated to stopping cyberthreats. The only way to address today and tomorrow’s cyberthreats is with a knowledgeable security industry. Learning offensive security allows you to test and refine your defenses. Malicious actors know how to compromise systems and networks. Knowing your enemies’ tactics is paramount to preparing offensive and defensive strategies. Those who have accepted the responsibility of defending our technology must learn how compromises occur in order to defend against them.

### The Current Security Landscape

Technology can be used for good or evil. The same technology that is used to make organizations and countries more productive can be used to steal, surveil, and do harm. This duality means that the technology we create to help us will sometimes hurt us, that technology used to fight for human rights can also be used to violate them, and that tools
