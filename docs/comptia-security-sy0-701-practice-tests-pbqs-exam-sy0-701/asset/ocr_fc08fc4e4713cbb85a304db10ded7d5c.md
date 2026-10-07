**Option A incorrect.** Worm propagation refers to the spread of a standalone malware computer program that replicates itself to spread to other computers. It doesn’t typically rename files or leave readable messages.

**Option B is incorrect.** A Trojan horse is malicious software that deceives users about its true intent. While it can deliver a ransomware payload, the described indicators more directly suggest ransomware activity.

**Option D is incorrect.** A logic bomb is a piece of code that executes a malicious function when certain conditions are met, but it doesn’t necessarily leave the described file traces.

**Question 211.** An organization is choosing a hash function for digital signatures. They want to ensure that it is resistant to scenarios where an attacker might produce two different messages having the same hash. Which type of attack are they trying to defend against?

+   **(A)** Side-channel Attack
**(B)** Replay Attack
**(C)** Birthday Attack
**(D)** Ciphertext-only Attack

**Explanation 211. Correct Answer: C. Birthday Attack.** In a Birthday Attack, attackers exploit the mathematics behind the birthday problem in probability theory, aiming to find two different inputs that produce the same output, or hash. When selecting a hash function for digital signatures, it’s crucial to pick one that is resistant to Birthday Attacks to maintain the integrity of the signatures.