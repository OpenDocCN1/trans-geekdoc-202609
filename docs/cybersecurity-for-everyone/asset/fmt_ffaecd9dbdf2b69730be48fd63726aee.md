
# Net neutrality

Net neutrality is the principle that organizations that carry data, that is, those who provide the pipes, do not provide preferential service to particular other organizations. This principle has been under fire recently as, for example, streaming entertainment services would like stronger guarantees of how much of their data can be moved and how fast.

# Internet structure and national boundaries

The global and slightly anarchic structure of the Internet does not fit well with Westphalian international legal principles. This has resulted in attempts by governments to carve the Internet into national sub-internets that they can control.

The best known of these is the so-called Great Firewall of China. The Chinese government controls traffic into and out of China (and within China as well) using a combination of rules embodied in filtering devices and a very large group of human supervisors. However, even this well-resourced and draconian approach leaks because of the need to provide tourists, and especially international business people, with access to their home nodes while they are in China. As a result, many international hotels in China are connected to the Internet in the ordinary way. Leaks like this have enabled various workarounds to evade the Great Firewall.

Other countries, notably Russia, have experimented with cutting their national section of the Internet off from the rest of the world. This would require turning on the same kind of filtering used by the Chinese at short notice, or perhaps even cutting connections completely. The difficulty with ideas like this is that it is hard to make sure that all the doors have been closed without actually trying it. Short tests have been carried out, but the economic impact makes it difficult to mount a thorough test.

The fundamental problem is that the structure of the Internet cuts across national boundaries, so that a web site used in one country need not necessarily be in the country, or even on the same continent.

## Data storage and privacy

Another area where Internet structure and national boundaries cause an issue is the question of where data is stored. The rules for the protection of data and data privacy vary from country to country so whether data can be accessed by, say, law enforcement or intelligence organizations will depend on where it is stored. Concerns about privacy means that, increasingly, countries are legislating where data about its citizens can be held.

# 2.13 Security issues

As we discussed in [Chapter 1](#01chap_01.xhtml), most of the security issues in cyberspace arise because security was almost never considered in the design of the systems on which it is built. However, even if security had been part of the design, there are a number of difficult issues in the design of a complex, distributed, incremental, world-spanning system.

The typical starting point for thinking about security in cyberspace comes from the design of medieval castles. Castles are defined by walls, intended to keep attackers out, and often arranged in rings so that penetrating one ring did not mean that the whole castle has been conquered. The problem with using this as a model for security is that castles necessarily have gates. Historically more castles by far were conquered via their gates, often opened by someone on the inside, than by battering down the walls. The same is true in cyberspace: security mechanisms often resemble building thicker and higher walls, without paying enough attention to the fact that data has to move in and out of regions and systems, and the places where this happens are often poorly defended. Of course, the walls are more obvious and more impressive than the gates, in cyberspace as they are in the real world.

Security wasn't considered in most parts of cyberspace when it was designed and built. Unfortunately, retrofitting security is extremely difficult. A major part of the difficulty comes because of the need for backward compatibility—all of the systems must continue to operate even when some part of it is upgraded to be more secure, and there's no overarching authority that can mandate installing the new improved part everywhere. There are many parts of cyberspace that are using computers and software whose flaws are widely known but which have not been updated or replaced because of cost, ignorance, or lethargy. Sometimes this heterogeneous nature, mixing new and old security regimes, introduces new vulnerabilities, so that security often seems like two steps forward, one (or two) steps back.

Some of the major players are taking responsibility for forcing updates to systems that increase their security. For example, `Microsoft` makes it much harder not to install updates to `Windows` automatically; `Google` and `Mozilla` both update their browsers behind the scenes; phone manufacturers force system updates; and `Amazon` updates `Kindles`, all without (much) user action.

Forcing updates seems like an inherently good idea, but it is actually a two-edged sword. Updates to address security issues often break other parts of running systems, and this can be disastrous for businesses that rely on constant availability. As a result, organizations tend to try and block automatic updating; and so security vulnerabilities for which a fix is available are often still present in important systems, providing targets of opportunity.

A more fundamental problem is the asymmetry between attack and defence. Any part of cyberspace must successfully defend against *all* possible attacks. An attacker only has to find one attack that works. This forces defenders to spend resources on defence, most of which is motivated by hypotheticals and so a hard sell to those providing the resources. Attackers may also have higher levels of motivation. The security staff of an organization is working for a salary; an attacker often has a more-personal or direct purpose.

Another significant problem is the pull on cyberspace stakeholders to indulge in *security theater*. This is when an organization imposes security processes that appear to be increasing security but actually do little or nothing to actually improve it. Often this means pushing processes that address low-risk but visible vulnerabilities while ignoring less visible but more substantial risks. A common example is a requirement to change passwords regularly, despite considerable evidence that this causes more problems then it solves (people change passwords back to what they were by cycling through the required number of possibilities, or write passwords down).

# 2.14 Non-benign use of cyberspace

Cybersecurity aims to prevent exploitation of cyberspace for purposes other than normal use. This range from vandalism by the bored, to money-making criminality, to use by states as levers of international policy. Some uses are not technically criminal but are social destructive.

For criminals, security vulnerabilities create new ways for them to commit crimes, primarily crimes that make money (rather than violence). Some of these are online version of traditional crimes, for example, stealing money from people's bank accounts rather than mugging them. The difference between online and offline crimes of this kind is scale—it takes the same effort to steal ⁢100 as ⁢100,000—and timing—transfers can happen in a few milliseconds.

Online crimes also tend to be more invisible. The victim of a mugging knows that it has happened, but the victim of a pickpocket does not, at least for a while. Online crimes are more like pickpocketing, but we are not used to keeping track of online resources in the same way that we keep track of wallets. Because online information and knowledge are digital, stealing them means taking a copy, so there need be no obvious sign that anything has happened.
