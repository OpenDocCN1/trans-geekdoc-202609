
What the creators of Stuxnet apparently did not intend or expect was that the worm would escape from Natanz. Stuxnet spread to an engineer's computer when it was connected to the centrifuges due to an error in the code; when that computer was then connected to the internet, the worm began self-replicating around the world.^([12](#20_chapter10.xhtml#ch10_en12)) Stuxnet was the first cyber weapon and illustrated that cyber weapons are not (yet) like kinetic weapons. With traditional, kinetic warfare, weaponry has become more precise and targeted, resulting in less collateral damage. In cyber warfare, it is much more difficult to make weaponry that is precise, targeted and contained, with no risk of collateral damage.

### WannaCry

We have been reminded of this reality many times since Stuxnet, not least with WannaCry. In [Chapter 3](#11_chapter03.xhtml#ch03_sec_002), we covered what happened when WannaCry hit and how the attack was thwarted; now we will explore the nation-state dimensions. WannaCry propagated through EternalBlue, an exploit that takes advantage of a vulnerability in Microsoft's Server Message Block (SMB; a method that allows for shared access to files, printers and ports on a network). The exploit was discovered, or perhaps even created, by the US National Security Agency (NSA) and kept secret by the Agency, not informing Microsoft of it for five years until a hacking group named the Shadow Brokers revealed they had possession of it. If an intelligence agency creates or discovers an exploit, they may be motivated to keep it secret so they can use it in operations against other nation states. Many people criticize this practice, especially in the wake of WannaCry and other attacks that utilize EternalBlue, but it seems a fact of life that intelligence agencies will conduct themselves this way. Spies are going to spy!

From 2016 to 2017, the Shadow Brokers released highly classified NSA data that dated no later than 2013. The data included the EternalBlue exploit, along with details of major vulnerabilities in Cisco routers, Linux mail servers and more, and came from the NSA's hacking group, Tailored Access Operations (TAO, also known as the Equation Group).

The timeline of events was as follows:

> August 2016: The Shadow Brokers announce possession of TAO/NSA classified data and attempt to auction it.
>
> January 2017: The Shadow Brokers publish screenshots that show a list of exploit tools, including EternalBlue.
>
> March 2017: Microsoft patch the vulnerability that can be exploited by EternalBlue.
>
> April 2017: The Shadow Brokers release all of the tools shown in the screenshot they shared in January, including EternalBlue.
>
> May 2017: WannaCry hits.

It is largely a matter of speculation as to who the Shadow Brokers are, but many agree that the group operate at the nation-state level and that the most likely state is Russia.

The NSA faced criticism for withholding information regarding the vulnerability that was leveraged by the EternalBlue exploit. Since then, the NSA has – for the first time – been attributed with publicly disclosing a vulnerability that they discovered: on 14 January 2020, Microsoft released a patch for vulnerability CVE-2020-0601, which they attributed to the NSA.^([13](#20_chapter10.xhtml#ch10_en13))

## [Companies and nation-state level attacks](#04_toc01.xhtml#fm_toc_113)

It is not simply governments who are targeted at the nation-state level. In an effort to cause destabilization, state-owned and private companies that are linked to nation states can become the target of nation-state level activity.

### Saudi Aramco

On 15 August 2012, one of the most destructive computer viruses ever seen sabotaged Saudi Aramco, the state-owned oil company of Saudi Arabia. The data on three-quarters of Saudi Aramco's computers (35,000 in total) was completely destroyed, and replaced with an image of a burning American flag. Aramco shut down the internal corporate network, disabling email and internet access, in an attempt to contain the virus, called Shamoon. Oil production was segregated on the network, and so unaffected, but the business side of Aramco was completely disconnected with a return to pen and paper, typewriters and fax machines. Recovery took months.

The attack was claimed by a hacking group calling themselves 'Cutting Sword of Justice', who said they were motivated by Saudi policies in the Middle East, although many believe this is a ruse and the true culprits are Iran, potentially in retaliation for Stuxnet, using lessons learned from the attack. Much like Stuxnet, it is suspected that an insider was fundamental to the Shamoon infection of Aramco, initiating it by plugging in a USB stick containing the virus.

As the state-owned national oil company of Saudi Arabia, it is not surprising that Saudi Aramco would be targeted by nation-state actors. However, we also see private companies that are not state-owned being caught up in nation-state level activity.

### NotPetya

The shipping giant Maersk is responsible for approximately one-fifth of the world's shipping capacity, carrying tens of millions of tons of cargo around the world. On 27 June 2017, computers across Maersk were infected by NotPetya. Computers shut down, phones stopped working, access gates locked and the vast majority of employees were told to go home until further notice.

Maersk was caught up in a huge attack using the malware NotPetya, which has been identified as a tool in the Russian war with Ukraine. NotPetya is linked to, but not the same as, the ransomware Petya, which spread via email attachments; NotPetya masqueraded as ransomware but was irreversible, intended to destroy not extort. It was built on EternalBlue and Mimikatz (a penetration testing tool that can pull passwords out of computer memory and use them to hack into other machines using the same username and passwords). The combination of these two tools was powerful, meaning that computers that were not patched against ExternalBlue could be hacked and then, via use of Mimikatz, those that were patched could be accessed and infected.^([14](#20_chapter10.xhtml#ch10_en14))

Ukraine was the first to be hit with NotPetya, and was hit with the majority of infections, with victims including banks, energy firms and Borispol airport in Kiev. This is not the first time Ukraine has been subject to cyber attacks at the nation-state level: it has been a target of cyber attacks in parallel to Russian military intervention in the country since 2014. During this time, companies running Ukraine's power grid have been targeted, resulting in blackouts that affected hundreds of thousands of citizens for up to six hours.

Although the NotPetya malware is understood to have been specifically targeting Ukraine, the malware did not stop at the country's borders, but soon spread around the world. NotPetya indiscriminately and permanently encrypted the hard drives of tens of thousands of computers – not only in Maersk, but also the pharmaceutical company Merck and the courier delivery service FedEx – costing each company hundreds of millions of dollars. The United States White House has identified the Russian military as the source of NotPetya, whilst describing it as the most destructive and costly cyber attack so far experienced.^([15](#20_chapter10.xhtml#ch10_en15))

## [Misinformation and disinformation](#04_toc01.xhtml#fm_toc_114)

It is common for nation-state cyber activity to be covert and challenging to attribute. However, when that activity is not only about code, but also about misinformation and influencing hearts and minds, it becomes an even greater challenge to identify and confront.
