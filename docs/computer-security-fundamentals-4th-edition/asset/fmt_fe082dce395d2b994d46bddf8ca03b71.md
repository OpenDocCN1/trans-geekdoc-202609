
After viruses, the most common attack is unauthorized usage of computer systems. Unauthorized usage includes everything from DoS attacks to outright intrusion of your system. It also includes internal employees misusing system resources. The first edition of this book referenced a survey by the Computer Security Institute of 223 computer professionals showing over $445 million in losses due to computer security breaches. In 75% of the cases, an Internet connection was the point of attack, while 33% of the professionals cited the location as their internal systems. A rather astonishing 78% of those surveyed detected employee abuse of systems/Internet. This statistic means that in any organization, one of the chief dangers might be its own employees. In 2019 similar threats still exist, with only slight changes in the percentages.

The 2014 Data Breach Investigation Report from Verizon surveyed 63,437 security incidents with 1367 confirmed breaches in 95 countries. This survey showed significant employee abuse of the network as well as many of the familiar attacks we have already discussed in this chapter. The 2015 Data Breach Investigation Report did not show significant improvement. In 2019, the situation was not improved. In fact, as mentioned earlier in the chapter, it is expected that cybercrime will cost more than $1 trillion per year.

### Basic Security Terminology

Before you embark on the rest of this chapter and this book, it is important to know some basic terminology. The security and hacking terms in this section provide a basic introduction to computer security terminology, but they are an excellent starting point to help you prepare for learning more about computer security. Additional terms will be introduced throughout the text and listed in the Glossary at the end of this book.

The world of computer security takes its vocabulary from both the professional security community and the hacker community.

#### Hacker Slang

You probably have heard the term *[hacker](#glossary.xhtml#gloss43)* used in movies and in news broadcasts. Most people use it to describe any person who breaks into a computer system. In the hacking community, however, a *hacker* is an expert on a particular system or systems, a person who simply wants to learn more about the system. Hackers feel that looking at a system’s flaws is the best way to learn about that system. For example, someone well versed in the Linux operating system who works to understand that system by learning its weaknesses and flaws would be a hacker.

This process does often mean seeing if a flaw can be exploited to gain access to a system. This “exploiting” part of the process is where hackers differentiate themselves into three groups:

*   A *[white hat hacker](#glossary.xhtml#gloss92)*, upon finding some flaw in a system, will report the flaw to the vendor of that system. For example, if a white hat hacker were to discover some flaw in Red Hat Linux, he would email the Red Hat company (probably anonymously) and explain exactly what the flaw is and how it was exploited. White hat hackers are often hired specifically by companies to do penetration tests. The EC Council even has a certification test for white hat hackers: the Certified Ethical Hacker test.

*   A *[black hat hacker](#glossary.xhtml#gloss10)* is the person normally depicted in the media. Once she gains access to a system, her goal is to cause some type of harm. She might steal data, erase files, or deface websites. Black hat hackers are sometimes referred to as *crackers*.

*   A *[gray hat hacker](#glossary.xhtml#gloss42)* is normally a law-abiding citizen but in some cases will venture into illegal activities.

Regardless of how hackers view themselves, intruding on any system is illegal. This means that technically speaking all hackers, regardless of the color of the metaphorical hat they may wear, are in violation of the law. However, many people feel that white hat hackers actually perform a service by finding flaws and informing vendors before those flaws are exploited by less ethically inclined individuals.

##### Script Kiddies

A hacker is an expert in a given system. As with any profession, it includes its share of frauds. So, what is the term for someone who calls himself a hacker but lacks the expertise? The most common term for this sort of person is *[script kiddy](#glossary.xhtml#gloss71)*). Yes, that is an older resource, but the term still means the same thing. The name comes from the fact that the Internet is full of utilities and scripts that one can download to perform some hacking tasks. Many of these tools have easy-to-use graphical user interfaces that allow those with very little or no skill to operate them. A classic example is the Low Orbit Ion Cannon tool for executing a DoS attack. Someone who downloads such a tool without really understanding the target system is considered a script kiddy. A significant number of the people you are likely to encounter who call themselves hackers are, in reality, mere script kiddies.

##### Ethical Hacking: Penetration Testers

When and why would someone give permission to another party to hack his system? The most common answer is in order to assess system vulnerabilities. Such a person used to be called a *[sneaker](#glossary.xhtml#gloss74)*, but now the term *penetration tester* is far more widely used. Whatever the term, the person legally breaks into a system in order to assess security deficiencies, as portrayed in the 1992 film *Sneakers*, starring Robert Redford, Dan Aykroyd, and Sidney Poitier. More and more companies are soliciting the services of such individuals or firms to assess their vulnerabilities.

Anyone hired to assess the vulnerabilities of a system should be both technically proficient and ethical. Run a criminal background check and avoid those people with problematic pasts. There are plenty of legitimate security professionals available who know and understand hacker skills but have never committed security crimes. If you take to its logical conclusion the argument that hiring convicted hackers means hiring talented people, you could surmise that obviously those in question are not as good at hacking as they would like to think because they were caught.

Most importantly, giving a person with a criminal background access to your systems is on par with hiring a person with multiple DWI convictions to be your driver. In both cases, you are inviting problems and perhaps assuming significant civil liabilities.

Also, some review of their qualifications is clearly in order. Just as there are people who claim to be highly skilled hackers yet are not, there are those who will claim to be skilled penetration testers yet lack the skills truly needed. You would not want to inadvertently hire a script kiddy who thinks she is a penetration tester. Such a person might then pronounce your system quite sound when, in fact, it was simply a lack of skills that prevented the script kiddy from successfully breaching your security. Later in this book, in [Chapter 11](#ch11.xhtml#ch11), “[Network Scanning and Vulnerability Scanning](#ch11.xhtml#ch11),” we discuss the basics of assessing a target system. In [Chapter 11](#ch11.xhtml#ch11) we also discuss the qualifications you should seek in any consultant you might hire for this purpose.

##### Phreaking
