# 140 Hacking Multifactor Authentication

# Accidents

One of the modern medical miracles is the discovery of penicillin. Its founder, a Scottish scientist named Alexander Fleming, discovered it when an accidentally discarded Petri dish containing Staphylococcus bacteria was left uncovered near an open window. A blue-green mold, later identified by Fleming as a strain of penicillin, landed on the Petri dish and started to kill and inhibit the growth of the bacteria. Fleming noticed the mold on the bacteria, and after a lot of serious work, his finding has saved and improved billions of lives. Very substantial accident.

Many found vulnerabilities were welcomed upon. The person or tool that found them was not intentionally looking for them. Sometimes it's an end user types something wrong (like a fuzzer might try) or does something in the wrong order. Sometimes it is from a third-party vendor to use and extend the functionality of an MFA vendor's solution.

MFA solutions that use threat modeling, code review, fuzzers, penetration testing, and vulnerability scanners tend to have fewer bugs after release. The smartest MFA vendors also employ internal resources who focus on finding bugs and encourage friendly environment "bug hunters. Even invite bug hunters and offer rewards to encourage friendly bug hunters in a process known as bug bounties. Some vendors, including MFA vendors, have bug bounties offered at $100,000, although the effort pays out on the severity of the bug found.

Even if an MFA vendor is not utilizing all, or even a single, of these vulnerability-hunting methods, you can always assume that malicious hackers and adversaries are. It's always best if the MFA vendor tries to find as many bugs as they can in their products first.

# Summary

The security of an MFA solution depends on far more than the inherent properties and technologies of the solution itself. Most also rely on potentially dozens of other, not-in-the-control, components and infrastructure issues. Each component can be hacked to compromise or get around the involved MFA component. In general, MFA hacks can be accomplished with technical methods, human elements, physical attacks, or two or more of these. MFA vulnerabilities are found in a variety of ways, including human review, automated scans, and even accidents. An MFA solution and designer must be aware of all the involved factors and potential attack vectors. The remaining chapters of Part II will give specific examples of MFA attacks. Chapter 6, "Access Control Token Tricks" will begin with one of the most common and hard-to-stop attack methods: hacking the access control token.