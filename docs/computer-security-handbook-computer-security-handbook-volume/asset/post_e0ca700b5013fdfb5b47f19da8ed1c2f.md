
Most often RAR is used to package the data for exfiltration. RAR is particularly useful for attackers because of its unique characteristic among compression formats: Data in an RAR file can be recovered even if the RAR is incomplete. If exfiltration is interrupted mid-transmission, the attackers will still be able to extract whatever portion of the data made it out. Encryption is used to make it more difficult for a compromised company to figure out what data was stolen. Most groups also prefer to use a media file extension for their RAR files as a further means of obfuscation. The renamed files may have a .mpg or .avi extension but they are simply normal encrypted RAR files.

For transmission of the data the attackers typically use Secure Sockets Layer (SSL). This tool, combined with the compressed and encrypted contents, makes it very difficult for companies to detect that anything malicious is occurring. The sophisticated attackers are so successful overall because the majority of their activities are done by hiding in the large volume and noise of legitimate activity. Consequently, they’ve all been observed using services like dropbox, box.net, and other cloud providers for exfiltration as well, given the significant adoption rate of these types of services legitimately by our users. Detecting malicious activity to a cloud provider from legitimate activity is very difficult indeed.

## 15.4 POLITICAL AND LEGAL ISSUES.

Thanks to the World Wide Web, the Internet has become a self-documenting phenomenon. One can use the Internet to find out everything one wants to know about the Internet, including how to penetrate information systems that employ Internet technology. However, the penetration information available on the Internet is not restricted to Internet systems, and the Internet is not the only source of penetration information. Furthermore, the very availability of penetration information is fraught with political and legal issues. These are discussed briefly in this final section of the chapter.

### 15.4.1 Exchange of System Penetration Information.

The sharing of system penetration information—that is, information that could facilitate illegal penetration of an information system—is the subject of a long, heated, and ongoing debate. This debate encompasses both practical and ethical aspects of the issue. Although complete coverage is not possible within the confines of this chapter, we do review the question of full disclosure, along with some of the sources for penetration information.

### 15.4.2 Full Disclosure.

How should we handle known vulnerabilities and potentially damaging computer viruses? Should we publish full details, conceal some details, or suppress any publication that would allow exploitation until patches or updates are available from manufacturers? Is there a case for handling some viruses and exploits differently from others?

Over the last two decades, formal venues for full disclosure of system or network vulnerabilities and exploits have evolved (e.g., BugTraq). Support for full disclosure of such details, down to the source code or script level, from professional, honest security experts (the Good Guys) is based on subsets of several key beliefs:

- The Bad Guys know about the vulnerabilities anyway.
- If they do not know about it already, they will soon with or without the posted details.
- Knowing the details helps the Good Guys more than the Bad Guys.

In the wild,” most viruses were written in assembly language or machine code. This limited the number of people who could read them or understand them to persons familiar with assembly language and machine code. However, anyone who receives a macro virus has the text editor tools needed to read its code. The tools required to develop and test macro viruses are provided in mainstream applications such as Microsoft Word, which has tens of millions of users worldwide, a significant percentage of whom have, or can easily acquire, the rudimentary programming skills required to develop their own viruses. The rapid spread of the original Word Concept virus in the summer of 1995 pretty much ensured that anyone who wanted a copy of it could get one (and many of those who did not want a copy got one anyway). The idea of keeping the content of the virus secret was a nonstarter.

Faced with vendor inability or unwillingness to fix security vulnerabilities in a timely manner, some users and experts can be expected to turn to full disclosure of security information, even though many of them may deplore using such tactics. However, they will always run the risk of making the wrong call when it comes to the effect of such disclosures, which are inherently unpredictable. Indeed, the release of the Word Concept virus may have been motivated by a desire to make Microsoft change the way its office applications handle macros. Other office applications, such as WordPerfect and Lotus 1-2-3, were designed to keep macro code separate from document content, making a malicious document much harder to create.

### 15.4.3 Sources.

There are many sources for information about how to penetrate systems. The motives behind these sources range from highly ethical to downright criminal. Chapter 74 in this Handbook discusses training and certification in penetration testing for legitimate, authorized purposes.

### 15.4.3.1 Online Sources.

There is no small irony in the fact that much of what a person needs to know about how to penetrate information systems is made available by information systems. Fortunately, the inverse is also true, as one of this chapter’s authors has observed: “The best weapon with which to protect information is information.”16 For this reason, security professionals need to know what sources of penetration information are available.

Today there are thousands of Websites that

- Document security holes in different versions of operating systems
- Distribute hacking tools and discuss how to use them
- Catalog default credentials for network hardware
- Teach malicious code writing, including how to make viruses and worms
- List license codes to enable activation of pirated software
- Buy, sell, and trade system access codes, stolen credit cards, stolen identity data, and networks of compromised hosts (botnets)
- Provide a forum and meeting place for those seeking to penetrate systems

These sites have assumed the mantle of earlier online communication channels, such as bulletin boards and Usenet groups, where legitimate sharing of information occurred alongside the exchange of illegal information, pirated code, and so on. Some Websites are moderated and so maintain certain ethical standards. Others follow the Internet tradition of “anything goes.” System administrators and employees should never participate in discussions on these Websites with company email addresses. In a popular strategy, hackers wait for platform-specific vulnerabilities to be announced, then search the Internet for messages from people using that platform, look at their email addresses to see where they work, and attack systems at those companies in the hope that patches are not yet installed.

### 15.4.3.2 Publications.

Over the years many publications have specialized in hacking. Often these provided information on how to penetrate systems. Some publications were primarily electronic, such as Phrack, while others have been print based, such as 2600, which is now widely distributed through conventional magazine channels as well as through paid subscriptions.

### 15.4.3.3 Hacker Support Groups.

Numerous groups of people exist to share hacking information, ranging from relatively stable entities with their own publications (e.g., 2600 and cDc) to annual conventions with thousands of participants (e.g., DefCon). Although some members of these groups may have committed criminal acts, and some participants at hacker conventions actually have been convicted of such and served time, there is usually a diverse mix of elements with different motivations in these groups and meetings. DefCon, for example, draws not only people who openly advocate unauthorized security testing of other people’s systems and networks, but also law enforcement personnel and legitimate security experts. Some participants go to DefCon specifically to convince young people not to break laws while trying to learn about security.

Many security professionals would prefer that the line between white-hat hacking and black-hat hacking be clearer and more sharply enforced; however, some companies overlook past transgressions in order to gain the perceived value of the hackers’ technical security expertise. Indeed, in recent years, investors have even cooperated with groups of hackers in founding security consulting companies, complete with some employees who continue to use hacker handles. The fact remains that some of the best technical training in the field is provided by people who gained their expertise in criminal (or quasi-criminal) hacking, but who now help defend against such activity.

### 15.4.4 Future of Penetration.

Trends over the last 15 years strongly suggest that attempts to penetrate information systems will not decrease any time soon. These factors have been in play for some time:

- The declining cost of, and increased access to, penetration technology—from software and hardware used to crack passwords and encryption to eavesdropping and interception devices
- The continuing practice of fielding inadequately tested systems, built with immature technology and with insufficient attention to security
- The increased availability of automated hacking tools with easy-to-use interfaces
- The continuing allure, and portrayal in popular culture, of hacking as a “cool” activity, without adequate reflection on its legality or consideration of its morality

Additionally, these factors have emerged strongly in recent years:

- The very real opportunity to make money from penetrating systems, given a thriving market in purloined personal data, compromised hosts (bots), and exploits
