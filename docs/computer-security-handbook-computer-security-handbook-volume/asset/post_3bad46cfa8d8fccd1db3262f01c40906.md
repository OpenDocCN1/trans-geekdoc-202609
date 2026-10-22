
- 15. “The Ghost in the Browser: Analysis of Web-based Malware,” www.usenix.org/events/hotbots07/tech/full_papers/provos/provos.pdf
- 16. Cobb, Stephen Cobb Guide.
- 17. C. Wilson, “Botnets, Cybercrime, and Cyberterrorism: Vulnerabilities and Policy Issues for Congress,” Congressional Research Service Report for Congress, RL32114, 2007, at http://tinyurl.com/2y995r
- 18. A. Rubin, “All Your Devices Can Be Hacked,” TED, October 2011, www.ted.com/talks/avi_rubin_all_your_devices_can_be_hacked.html

## 16.2 MALICIOUS CODE

Common types of malicious code include viruses, worms, Trojan horses, spyware, rootkits, and bots. Emerging malicious code threats include kleptographic code, cryptoviruses, and hardware-based rootkits. Present-day malicious code threats do not always fit into neat categories, resulting in confusion when discussing the topic. It is not possible to classify all code as being good code or malicious code. Absent the mens rea, or criminal intent of the author or user, code is neither good nor bad. Authors develop code to achieve some goal or fulfill some purpose just as users run code to achieve some goal or purpose. It is therefore the context of use and the intent of the wielder that determines whether code is malicious.

### 16.2 MALICIOUS CODE THREAT MODEL.

In a threat model or profile, an actor uses access to target an asset, with an action, to yield an outcome.³ To understand the scope of the problem (and possible prevention), it is useful to study malicious code threats in this model. Actors may be structured or unstructured threats posed by individuals, organizations, or nation-states. Access is some allowed physical or logical path to the targeted asset. The execution of malicious code or logic is an action used to yield the desired outcome. This outcome could be intelligence (such as theft of trade secrets), surveillance, reconnaissance, disruption of operations, destruction of assets, publicity for some cause, or negative publicity for the victim.

### 16.2.1 Self-Replicating Code.

Self-replicating code is not inherently malicious. A good deal of artificial intelligence research focuses on iterative self-replication. Hewlett-Packard and others⁴ have researched how techniques of self-replication could yield beneficial software such as code-patching worms. John Von Neumann proposed the basic concept of self-replicating code in his 1949 paper, “Theory of Self-Reproducing Automata.”⁵ In 1961 at Bell Labs, Douglas McIlroy, Victor Vyssotsky, and Robert H. Morris played a game called Darwin in which two opposing programs (memory worms) would enter a system and only one would leave. In an interview with one of the authors, Robert H. Morris the former Chief Scientist of the National Security Agency (NSA), stated:

> We had this notion of putting two programs in a machine that would fight with each other and one would win and the other would die. Basically, the notion and the program were written by McIlroy and Vyssotsky and I was just on the side. But then, a few days later, I had a good idea and simply won the game and everyone else gave up… just because I happened to hit upon a very good idea for writing it.⁶

Although it would be desirable to live in a world free of war, the ever-increasing integration of technology and warfare necessitates the development of offensive information warfare capabilities. Malicious code implants can serve useful intelligence, surveillance, and reconnaissance capabilities in national security and law enforcement operations. In addition, by researching and developing malicious code techniques, practitioners can better prepare for defense against developing threats.

### 16.2.2 Actors: Origin of Malicious Code Threats.

Prior to discussing the specific types of malicious code, it is worth understanding the origin and source of malicious code attacks. Malicious code may originate from structured or unstructured threats. Structured threats include nation-states, corporate criminals, and organized crime. Unstructured threats include rogue actors such as individual intruders and so-called script kiddies.

#### 16.3.1.5 Cross-Site Scripting Viruses (or Worms).

Cross-site scripting (XSS) viruses (or worms) replicate via flawed Web application servers and client code. A cross-site scripting exploit involving the social networking site MySpace and flaws in Microsoft Internet Explorer occurred in 2005 whereby a user named Samy amassed over 1 million friends overnight using a JavaScript insertion bug.^22 The Los Angeles Superior Court sentenced the author, Samy Kamkar, to three years’ probation and 90 days of community service for his actions.

In an excellent review of XSS, Sherif Koussa wrote,

> > Cross-site scripting is an attack that targets the application users. The simplicity of cross-site scripting is also why it is so powerful. If the application is vulnerable to cross-site scripting, the developer is not in charge of what runs on the user’s browser anymore . . . the attacker is. Cross-site scripting could be used in attacks like authentication hijacking and session hijacking. The power of cross-site scripting manifests itself even more when combined with cross-site request forgery.^23

He then cites the case of the Twitter attack below:

> > In 2009, Mikey Mooney, then 17 years old, claimed responsibility for attacking Twitter using XSS techniques: “... at least four separate variants of the original StalkDaily.com XSS worm hit the popular micro-blogging site Twitter, automatically hijacking accounts and advertising the author’s web site by posting tweets on behalf of the account holders, by exploiting cross site scripting flaws at the site.” Writer Dancho Danchev provided more details about the attack in his ZDNet article.^24

#### 16.3.1.6 Polymorphic Viruses.

Polymorphic code modifies itself to evade detection. The virus code may accomplish this by dynamically reassembling itself to modify the underlying structure while retaining overall functionality. In other methods, the virus is encrypted, encoded, or packed, and a stub loader decrypts, decodes, or unpacks the virus at run time. UPX, the Ultimate Packer for eXecutables, is currently the most widely used packer format.

In the SOPHOS Security Threat Report 2013, the authors write:

> > Polymorphism is not a new idea—malware authors have been using it for 20 years. Simply stated, polymorphic code changes its appearance in an attempt to avoid detection, without changing its behavior or goals. If a program looks different enough, attackers hope, antivirus software might miss it. Or the antivirus software might be forced to generate too many false positives, leading users to disable it.

> > In a polymorphic attack, code is typically encrypted to appear meaningless and paired with a decryptor that translates it back into a form that can be executed. Each time it’s decrypted, a mutation engine changes its syntax, semantics, or both.

> > For instance, Windows malware authors have often used structured exception handling to obfuscate control flow and make it tougher to perform static analysis of programs before they run.

> > Traditional polymorphic viruses are self-contained and must contain the mutation engine in order to replicate. Sophos and other security companies have become adept at detecting these forms of malware. With access to the mutation engine, it’s easier to analyze its behavior.

> > Today attackers are rapidly moving to web-distributed malware relying on server-side polymorphism (SSP). Now, the mutation engine and associated tools are hosted entirely on the server. Criminals can use these tools to create diverse file content on the fly. Recipients of this content (whether it is a Windows .exe, Adobe PDF, JavaScript, or anything else) see only one example of what the engine can create. They don’t get to see the engine itself.^25
