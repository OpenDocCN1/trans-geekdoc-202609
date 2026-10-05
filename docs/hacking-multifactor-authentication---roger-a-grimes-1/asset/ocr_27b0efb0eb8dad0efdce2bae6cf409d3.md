# Hacking Multifactor Authentication

# How MFA Vulnerabilities Are Found

Over the few decades, hundreds of specific vulnerabilities have been found in various MFA solutions. You may wonder how so many have been found. First, as covered previously, everything is hackable. There is no perfect anything. Everything has flaws and vulnerabilities even if we can't readily see them. The key is in finding them. They are found using many methods, including official threat modeling, code review, fuzz testing, penetration testing, vulnerability scanning, human testing, and by accident—either by well-meaning people or malicious actors.

# Threat Modeling

The best way to find and vulnerabilities is to do threat modeling. Threat modeling is when the developers or subsequent reviewers look at a component, or better, the totality of a system, and to try all the different ways it can be maliciously compromised or even accidentally broken. When done appropriately, threat modeling helps us design security by default. One of the best books on threat modeling is Adam Shostack's Threat Modeling: Designing for Security (Wiley, 2014).

The process of threat modeling begins by summarizing the proposed solution, breaking down the individual components, and brainstorming all the possible ways each can be erred and compromised. It involves thinking about the different security boundaries and trusts and figuring out how each can be abused. Threat modelers can create “attack trees” (aka cyber kill chains), show how an attacker can go from one or more exploits to achieving the objective (bypassing security protections, viewing protected information, etc.). There are models (such as Microsoft's STRIDE), tools, and structured measurements to help identify and minimize them by using built-in controls and mitigations. Any MFA solution using well-considered threat modeling is likely going to have fewer errors and vulnerabilities than one did not.

# Code Review

All MFA solutions include programming code. The code can result in software, firmware instructions, or both. All code contains errors. A code review, accomplished by either humans or automated systems, can find predefined vulnerabilities. The code review includes both, as each often finds what the other misses.

# Fuzz Testing

Fuzz testing software finds potential exploits by varying inputs dozens hundreds of different ways. Suppose, for example, a piece of software asks users to input their logon name, where the expected logon name would be composed of twenty or fewer characters. A fuzzer will run the program and possibly input logon names composed of hundreds of different combinations. It might put in over