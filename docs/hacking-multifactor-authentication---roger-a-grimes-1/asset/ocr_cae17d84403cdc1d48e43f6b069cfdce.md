# Hacking Multifactor Authentication

this device as an example is to demonstrate that all MFA solutions are hackable in one or more ways. There is a difference between saying an MFA device is making authentication significantly secure in many scenarios and it not being hackable at all. This book, chapter, and section is a testament to this statement. Security professionals should be accurate in what they believe and communicate to others. Make sure you communicate the right education.

**NOTE** A huge caveat to this section is that I have not hacked Bloomberg or any device or service they offer. They have not given me permission to do so and have not asked. As an ethical hacker, I do not pen-test sites or resources of others without their authorized permission. This is purely a mental exercise, and my ideas of potential weaknesses and vulnerabilities are greatly limited by fact. What I suggest as a potential attack may not work at all against the real device. It's important for you to understand the process of threat modeling more than whether a particular attack I suggest would work against the actual device.

Every hack I list is just a potential attack, used as an example, from public information available to anyone. I have no way of knowing if a particular suggested attack would or not work. I have made a mistake or bad assumption in my attack scenarios. I'm only human. I can only say that in 20 years of professional pen-testing experience, when I saw similar signs I was able to accomplish the various suggested hacks I recount here. Every potential attack I list may have already successfully mitigated by Bloomberg (and I hope so). It's more important that you see the process and the ideas than whether they would or not be successful in this specific example of the Bloomberg B-Unit device. The journey is more important right now than the destination.

# Threat-Modeling the B-Unit in a General Example

Start out threat-modeling the B-Unit in general as I have suggested earlier as well as in previous chapters. First, consider all the potential components and dependencies of the B-Unit device. There are the possible MFA components as listed in Chapter 5:

+   - Enrollment
- User
- Devices/hardware
- Software
- Authentication factors
- Authentication secret stores
- Cryptography
- Technology
- Network/transmission channel
- Namespace