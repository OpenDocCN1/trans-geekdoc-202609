# 124 Hacking Multifactor Authentication

Chapter 5 is not only a generalized look at how MFA vulnerabilities are found, but also summarizes all the different components. This chapter should be used by nonmalicious hackers looking to ensure that an MFA solution they are considering is as secure as possible as well as MFA developers to ensure that the solution they are delivering is as secure as from the start they offer to. Nothing is vulnerability, but by learning and using the lessons of past exploits, the number of future bugs can be minimized. Many of the discussions in this chapter apply to most digital solutions and not just authentication or MFA. The rest of Part II will cover specific examples of MFA vulnerabilities that illustrate the generalized vulnerabilities covered here.

# MFA Dependency Components

No MFA solution is an island. Every MFA solution is just one part of multiple components, relationships, and dependencies, as visually depicted in Figure 5.1, and each of these components is an additional area where an exploitable vulnerability can occur.

![](bbox=[0.095, 0.465, 0.905, 0.803])

Figure 5.1: MFA dependent components

Essentially any component in the entirety of the MFA's life cycle, from provisioning to deprovisioning and everything in between, is subject to having exploitable vulnerabilities and hacking.