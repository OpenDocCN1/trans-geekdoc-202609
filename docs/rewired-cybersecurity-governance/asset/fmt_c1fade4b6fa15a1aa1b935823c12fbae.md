
# Cybersecurity Standards and Cyber Insurance

There was a time when cybersecurity standards were more akin to environmental regulations: self‐governance enabled companies to keep costs low and maintain a delightful ignorance of IT mechanics or the types of threats that might be arrayed against them. Attacks, especially when they affected customers, could be treated as an externality.

Cybersecurity is a prominent issue now, not just because of newfound awareness of the sorts of consequences that can be imposed by an incident but also because of increasing sensitivity to the connection between events affecting customer's data, firm's proprietary information, and the material value of these companies.

The cyber insurance industry has developed into a form of private governance over the security standards used to control risk. This emergence is best explained as private advance, the activity of insurance firms looking to reap benefits from new markets and lock in their dominant market position.

The ability to recognize these benefits was critically enabled by state action in the form of the NIST security controls and 2011 SEC guidance, undermining the logic of a state retreat.

The centrality of risk to the emergence of cyber insurance as a mechanism of private governance rests on an extended history of fundamentally insecure computing architectures and the adaptability of threat groups. Security standards establish practices and policies to help control this risk.

Growing uncertainty around the consequences of attacks provides an incentive for the private sector to find new means to manage risk and has motivated substantial growth in the use of insurance. Like credit rating agencies, insurers provide risk assessments to structure uncertainty and identify controls to reduce it.

Leaning on participants in this market to legitimate and enforce these standards, insurers occupy an unusual position within the panoply of public‐ and private‐sector groups dealing with cybersecurity.

The policy implications for governments center on the state's willingness to craft neutral standards. Government standards bodies retain a high degree of legitimacy in the private sector, as their codification efforts have provided robust starting points for the design and implementation of security controls.

This codification effort have continued with discussions at the FDA around cybersecurity‐responsive development, production, and operating practices for medical device manufacturers.

Continuing engagement with companies and nonprofit groups, as well as additional work to improve risk assessment practices, would be a boon to this effort and help reinforce best practices in both private‐ and public‐sector organizations.

Cyber insurance is a rapidly expanding market; insurer's ability to recognize trends across customers and spread best practices could serve to not only enforce but also identify new security standards.

At present, the market acts as a form of private governance over existing security standards, a novel form of this governance in cybersecurity.

This governance, which works to break down information asymmetries in the private sector and helps enforce security standards, could well serve as model for policymakers.

The keys appear to be emphasizing lateral pressure from companies against their business partners and vendors (rather than direct regulation), and emphasizing the role of certain specialized companies, like insurance firms, to monetize standards enforcement.

Policymakers may find cyber insurance a helpful model for private sector‐led security governance as they seek to rewire cybersecurity.

## Notes

### 9 Containing Conficker: A Public Health Approach

*Michael Thornton*

*History and Philosophy of Science, University of Cambridge, Cambridge, UK*

#### 9.1 Introduction

In late 2008, Microsoft discovered a vulnerability in Windows which could be exploited by computer worms, a highly contagious type of self‐replicating malware. While Microsoft promptly released an emergency patch, within months a sophisticated worm called Conficker spread rapidly around the world, drafting between 5 and 13 million machines into the “holy grail” of botnets.[¹](#c09.xhtml#c9-note-0001) While estimates of the danger vary, a botnet of that size could have credibly threatened critical infrastructure[²](#c09.xhtml#c9-note-0002) (water treatment plants, emergency response systems, power plants, etc.) and possibly even the backbone of the internet itself. Despite this danger, world governments essentially did nothing to contain the worm. Luckily, a small group of security experts calling themselves The Cabal[³](#c09.xhtml#c9-note-0003) (later renamed the less sinister Conficker Working Group, CWG) understood the risk. They were largely able to prevent the creators of the worm from gaining control of the botnet, by working with the companies and organizations which manage over 100 Top Level Domains (TLDs) to preregister domains that Conficker's creators might use for command and control communications.

In this chapter, I will briefly describe the spread of Conficker and assess whether the CWG is a good model for future large‐scale malware mitigation efforts. Finding that model insufficient, I will explore an alternative framework for containing malware based on the philosophy and policy of public health. In this section, I will explore fundamental philosophical questions about what constitutes a matter of public concern and the proper role of government. While others have compared public health efforts to cybersecurity, this work has often focused on specific low‐level applications (e.g. nomenclature[⁴](#c09.xhtml#c9-note-0004) and network effects[⁵](#c09.xhtml#c9-note-0005)). I will argue, however, that the philosophy and policy of public health is most useful as a way of might have looked like.

#### 9.2 The Conficker Infection

On 23 October 2008, during the eighth annual meeting of the International Botnet Task Force, Microsoft released an out‐of‐band emergency security patch. The patch fixed a Windows vulnerability that could allow malware to spread between unprotected machines without any user interaction.[⁶](#c09.xhtml#c9-note-0006) While releasing an emergency patch cast a spotlight on the vulnerability, Microsoft had already seen the flaw exploited in the wild. On 22 November a month after the patch's release, a new piece of highly contagious malware – the Conficker worm – was first detected. In response, Microsoft issued a security alert recommending that people immediately patch their systems.

For the most part, Conficker A (as it would come to be called) simply hid in a computer's background activity. When it was time to call home for instructions, however, the worm would contact 250 pseudorandomly generated domains spread out across 5 TLDs. Behind any of those domains, the creators of the worm could be waiting to issue commands. A few weeks later, a more sophisticated variant called Conficker B appeared; this variant could propagate via thumb drives, disable Windows Automatic Update, block certain DNS look‐ups, and call domains from eight TLDs.[⁷](#c09.xhtml#c9-note-0007) While these strategies were not new, it was unusual for so many features to be packed into a single piece of malware. More than one researcher described it as “elegant.”[⁸](#c09.xhtml#c9-note-0008) By the end of 2008, SRI International estimated that between 1 and 1.5 million computers were infected.[⁹](#c09.xhtml#c9-note-0009) Over the next five months, three additional versions of the worm would be introduced. At its peak in 2009, the Conficker botnet grew to between 5 and 13 million machines.[^(10)](#c09.xhtml#c9-note-0010)
