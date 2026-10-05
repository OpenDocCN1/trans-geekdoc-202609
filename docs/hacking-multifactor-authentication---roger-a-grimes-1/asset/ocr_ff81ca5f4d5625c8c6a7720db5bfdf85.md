# Developer Defenses Against Physical Attacks

First, we'll look at developer defenses against physical attacks.

# Threat Model

Physical attacks are easy to overlook. MFA developers need to ensure that physical attacks are included in their threat model and mitigated. Encryption keys and other critical secrets should be securely protected as possible. Developers need to make sure the secrets don't accidentally “bleed” out into less protected areas.

# Educate

Programming team managers need to be sure that all involved developers are educated about the possible physical attacks discovered during threat modeling so that they can be mitigated. Vendors should share potential physical attack scenarios with customers so that they can do their part in preventing physical attacks.

# Allow/Require Split Secrets

Many physical attacks can be viewed stored, supplied protected, authentication secrets. If possible, store the secret across two locations so that a compromise of one location does not reveal the entire secret. For example, with BitLocker, Microsoft recommends users use at least two different locations for the secrets needed to unlock a BitLocker volume. As an example, BitLocker can part of the key in a local TPM chip and require a PIN entered by an end. An electron microscope may be to discover the master key over a TPM chip, but it won't be able to see the PIN stored in someone's memory. It's the whole reason MFA can be more secure than 1FA.

# Implement Anti-Tampering

Any MFA-related software or firmware starts up it should check for unauthorized modification. But it's better to allow an external component, which has already been checked and verified for legitimacy, to do the check. For example, in Microsoft Windows, the TPM chip has self-checks and “roots of trust” to verify itself. The TPM chip has secrets that other unlock, including the roots of trust of UEFI Secure Boot, which then unlocks BitLocker, which in turn unlocks the disk volume and loads Windows. Critical drivers go through another integrity check load. One big integrity-checking chain, from beginning to end, before the end can ever log on. Each verified component checks the next component's integrity in the chain. Only authorized updates should be allowed

Any MFA physical device should be designed to prevent physical tampering. You can do Internet searches on anti-tampering and TEMPE to get plenty of recommendations and guidance. Design and engineering should make it hard for an attacker to logically or physically tamper. MFA device cases should be resistant to easy opening. If a case is opened by an unknowledgeable