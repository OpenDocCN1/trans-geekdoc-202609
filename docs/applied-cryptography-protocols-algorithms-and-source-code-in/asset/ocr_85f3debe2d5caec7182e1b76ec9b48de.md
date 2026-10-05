# 10.1 Choosing an Algorithm

the myriad military security organizations in the world [which are probably better than the academic institutions—they've been doing longer and are better funded]; so it is possible that these algorithms are easier to break than it appears. Even so, it is far more likely that they are more secure than an algorithm designed and implemented in secret some corporate basement.

The hole in all this reasoning is that we don't know the abilities of the various military cryptanalysis organizations.

What algorithms can the NSA break? For the majority of us, there's really no way of knowing. If you are arrested with a DES-encrypted computer hard drive, the FBI is unlikely to introduce the decrypted plaintext at your trial; the fact that they break an algorithm is often a better secret than any information that is recovered. During WWII, the Allies were forbidden from using decrypted German Ultra traffic unless they could plausibly gotten the information elsewhere. The only way to get the NSA to admit the ability to break an algorithm is to encrypt something so valuable that its publication warrants the admission. Or, better yet, create a funny joke and send it via e-mail to shady characters in shadowy countries. NSA employees are people, too; I don't think they can keep a good secret.

A good working assumption is that the NSA can read any message that it chooses, the NSA is limited by resources, and has to pick and choose among its targets. Another good assumption is that they prefer breaking knuckles to breaking codes; this preference is so strong that they will only resort to breaking codes when they wish to preserve the secret that they have read the message.

In case, the best of us can do is to choose among public algorithms that have withstood a reasonable amount of public scrutiny and cryptanalysis.

# Algorithms for Export

Algorithms for export out of the U.S. government must be approved by the U.S. government (see Section 25.1). It is widely believed that these export-approved algorithms can be broken by the NSA. Although no one has admitted this on the record, these are some of the things the NSA is rumored to privately suggest to companies wishing to export their cryptographic products:

+   - Leak a key bit once in a while, embedded in the ciphertext.
- "Dumb down" to something in the 30-bit range. For example, while the algorithm might accept a 100-bit key, most of those keys might be equivalent.
- Use a fixed IV, or a fixed header at the beginning of each encrypted message. This facilitates a known-plaintext attack.
- Generate a few random bytes, encrypt them with the key, and then put the plaintext and the ciphertext of these random bytes at the beginning of the encrypted message. This also facilitates a known-plaintext attack.