# 328 Hacking Multifactor Authentication

Fingerprints have been used by law enforcement for over a century to identify criminal suspects and for decades to register and document applicants for high-security jobs, security clearances, licenses (e.g., concealed carry gun permits), and today, for passports and visas. Fingerprints were among the first used computer security biometric authentication factors and are the most popular biometric used today. One or more fingers may be measured for potential authentication candidates.

Many vendors have included fingerprint readers and applications with various models of computers and laptops for at least two decades. But it really took off in popularity with Apple’s front-located, Touch ID implementation on the iPhone 5s in 2013. Today, many if not smartphones come with a fingerprint sensor that can be used to unlock them. Many USB-style MFA devices include a fingerprint sensor (as shown in Figure 16.1).

![](bbox=[0.095, 0.396, 0.585, 0.643])

**Figure 16.1:** Fingerprint reader sensor incorporated on a relatively inexpensive FIDO (Fast ID) USB device

Fingerprint reader sensors come in four basic technologies: optical, capacitance, ultrasonic, and thermal. An optical scanner records an image of the fingerprint. Capacitance, ultrasonic, and thermal readers all use their underlying technology (i.e., weak electrical current, high-frequency sound waves) to identify and map ridges.

> NOTE Most fingerprint readers require a person to touch or swipe their fingerprint across a physical surface above a sensor. There is a developing class of touchless fingerprint readers. These readers usually work using lasers, light, ultrasonically, but touchless fingerprint reading can also be done using a digital camera on a cell phone. Touchless fingerprint readers have benefits over the