
## 118 Hacking Multifactor Authentication

more time to train help desk and support staff on how to support and troubleshoot. It takes more time for people to input and use multiple factors as compared to single-factor solutions. It is the very MFA solution that actually speeds up everything. If you do that, it's a win-win for everyone.

There are even claims (krebsonsecurity.com/2019/11/study-ransomware-data-breaches-at-hospitals-to-tick-in-fatal-attacks/) that requiring MFA has caused an increase in deaths at a hospital due to lockdown outages. On first, it seems a strong conclusion to reach on just one story, and perhaps it's just an anecdotal anomaly, or maybe MFA was a causative reason for the increase in deaths—but it might be. We haven't studied a computer security problem with these types of potential severe consequences before. Until we know more with findings and more data that rules out other possible cases or out, we might not know for sure.

## MFA Will Cause Downtime

Years ago, when I was a child my mother bought the first car we owned had electric windows. Prior to that, in any car we had to manually roll up or down the windows using a knob of some type. We loved our new car and its fancy, high-tech windows. Until we broke down on the side of a Florida highway during a torrential storm weekend and we could not roll up our windows. It rained so much that not only did we get wet, but it ruined the inside of the car. We had to buy a new car. It was a lot of rain. Ever since, I haven't bought things with too many fancy gadgets.

MFA is like electric car windows. The reason password authentication has survived so long in the face of growing adversity is it works—from a usability perspective. MFA costs more to implement and operate. It takes longer to enroll users in MFA authentication; it is far more likely to cause problems, far more likely to have false positives and false negatives, and far more likely to cause downtime. Here's an example: bleepingcomputer.com/news/microsoft-365-authentication-outage-unable-to-login. It was barely any downtime, two hours, but it has happened before, multiple times (including another 14 hours: securityweek.com/microsoft-details-cause-recent-multi-factor-authentication-outage). It's not much downtime, but it's downtime would not have been incurred if MFA did not exist.

## No MFA Solution Works Everywhere

Perhaps the biggest usability argument, at least right now, is that no MFA solution works everywhere. None. You can take the most popular and widespread MFA options, which are supported by millions of sites and services, and they don't account for 1 percent of sites and people need to log on. In every case, administrators to pick incomplete solutions and have to use the MFA solution for some things and a non-MFA (or other MFA solution) for others. The lack of global support for any MFA option is absolutely slowing its proliferation.

## Chapter 4 Usability vs. Security 119

The best admin looking for a new MFA solution can do is inventory which MFA applications must be covered and which are optional. And then they need to find MFA solutions cover their “must-haves” and which critical applications needed be covered. I've yet to see an organization where a single MFA solution covered everything, unless it was a very specialized, high-security environment where MFA coverage was the primary requirement above all. Or perhaps they had an MFA-enabled SSO solution that allowed a single MFA sign-on to then open other (really non-MFA-protected) applications.

## Summary

Security has always been a struggle between usability and safety, and that struggle is definitely challenged by any MFA solution. This chapter explored many of the main points of usability versus security, including the fact that users actually don't care about security as much as we do and they don't want the best security possible. Instead, the solutions that win in the long run provide us with the right balance of security and ease of use.

Chapter 5, “Hacking MFA in General” investigates the general methods for hacking any MFA solution.

## Hacking MFA

- Chapter 5: Hacking MFA in General
- Chapter 6: Access Control Token Tricks
- Chapter 7: Endpoint Attacks
- Chapter 8: SMS Attacks
- Chapter 9: One-Time Password Attacks
- Chapter 10: Subject Hijack Attacks
- Chapter 11: Fake Authentication Attacks
- Chapter 12: Social Engineering Attacks
- Chapter 13: Downgrade/Recovery Attacks
- Chapter 14: Brute-Force Attacks
- Chapter 15: Buggy Software
- Chapter 16: Attacks Against Biometrics
- Chapter 17: Physical Attacks
- Chapter 18: DNS Hijacking
- Chapter 19: API Abuses
- Chapter 20: Miscellaneous MFA Hacks
- Chapter 21: Test: Can You Spot the Vulnerabilities?

## Hacking MFA in General

Chapter 5 will cover hacking MFA generally, without showing any specific techniques. Anything can be hacked. Anyone telling you that they have something that can't be hacked is lying or naive. Either way, they shouldn't be trusted. Multifactor authentication (MFA) has many components and supporting infrastructures may which the MFA solution vendor has no control, and each can be hacked by various means. This book is dedicated to showing dozens of ways that all, or specific implementations, can be hacked, although this particular chapter addresses the topic in a generalized way.

This book will not be to show all the ways MFA can be hacked, although I'll fill as many as I can within these pages. There are ways that I don't know about; I haven't thought of or encountered them, or I've simply forgotten them. Many MFA vulnerabilities are only known to the potential attacker who is keeping them secret until they are otherwise needed. They are used sparingly and rarely in a way that the exploited victim isn't even aware of. The biggest nation-states have thousands of nonpublic vulnerabilities cataloged, awaiting a specific need. Others are known by their vendors and kept secret because the vendor doesn't know a good way to mitigate the risk.

Many MFA vulnerabilities have not been discovered yet. The world is full of hacked things that have vulnerabilities that went undetected for decades, until they were finally discovered by a single, curious soul. Vulnerabilities often sit in plain sight for years, until someone reviewing the code or trying a specific action shows a weakness and explored it. Many vulnerabilities are found by accident. Someone is trying to do something new, extend or accidentally causing an error that reveals a previously unknown vulnerability.

Many, if not most, vulnerabilities will go undiscovered, without anyone recognizing the vulnerability that could be exploited. Humans are imperfect. Just as we can't stop all programming mistakes, we don't find every mistake or vulnerability. We will always create more vulnerabilities than we will find. It's the nature of programming. Even the software that we design to specifically find vulnerabilities doesn't find every one; it only find the vulnerabilities that we already understand and know how to find.

## 124 Hacking Multifactor Authentication

Chapter 5 is not only a generalized look at how MFA vulnerabilities are found, but also summarizes all the different components. This chapter should be used by nonmalicious hackers looking to ensure that an MFA solution they are considering is as secure as possible as well as MFA developers to ensure that the solution they are delivering is as secure as from the start they offer to. Nothing is vulnerability free, but by learning and using the lessons of past exploits, the number of future bugs can be minimized. Many of the discussions in this chapter apply to most digital solutions and not just authentication or MFA. The rest of Part II will cover specific examples of MFA vulnerabilities that illustrate the generalized vulnerabilities covered here.

## MFA Dependency Components

No MFA solution is an island. Every MFA solution is just one part of multiple components, relationships, and dependencies, as visually depicted in Figure 5.1, and each of these components is an additional area where an exploitable vulnerability can occur.

![](img/c78b0f79db62998ee317a35df5629d85_148_0.png)

Figure 5.1: MFA dependent components

Essentially any component in the entirety of the MFA's life cycle, from provisioning to deprovisioning and everything in between, is subject to having exploitable vulnerabilities and hacking.
