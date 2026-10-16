
An alternative is to use a custom, complex hash rather than a standard one. While this is normally a horrible idea in security, it's not an unheard-of choice for this application. The goal isn't to provide absolute protection, just to slow down reverse engineering. For anyone in the security space whose toes are curling at the suggestion of making your own hash, just note that this suggestion comes with the caveat that you are able to make a decently good one. As a defender, keep in mind there are lots of tools out there to do common hashing techniques, so those will be all the first things an attacker will try to unroll your key.

Also, find ways to add unique complexity so a key can be used only in a unique setting, and not proliferated. Schemes such as concatenating the product name and version and computer name within the hashed value adds a solid level of complexity. This way, a cracked valid key for one installation doesn't unlock other releases.

### A Better Way

Hashes are better, and, if implemented correctly, they can be decent. But there are even better options. A great example of this is the approach Microsoft uses when generating license keys for its software.

Instead of hash algorithms, Windows uses public key cryptography. With public key cryptography, a digital signature can be generated using a private key and verified using a public one. This means that a digitally signed license key can be verified by an application without exposing sensitive keys.

When generating its license keys, Windows uses a lot of information about the software, including but not limited to:

*   Bitness (32, 64)

*   Type (home, professional, enterprise)

*   Product ID

*   Hardware features

Including all of this information helps to lock a product key to a specific installation of the software. If you're interested in more information on the protocol, there are lots of resources online tearing into Microsoft's key generation.

#### *Digitally Signed Keys*

Digital signatures on license keys, like those used by Windows, make it much more difficult to generate fake, valid keys. A valid signature must be generated using the private key but can be validated with a nonsensitive public key.

Digital signatures prevent the straightforward generation of license keys and present attackers with two options. The first is to leak a legitimate key, which could be traced back to a specific user. Alternatively, an attacker can modify the program to remove the key-checking code, which increases the time and complexity of pirating the software.

### The Best Way

The examples presented so far have focused predominately on offline verification of license keys, meaning the entirety of the code to verify and unlock the software is resident on the system. However, given the prolific connectedness of systems these days, a way to add more strength is to add an online component.

This can take many forms, but one you see today is each piece of software can be distributed with a license key in the form of a large random number distributed alongside the software. When the product is installed and registered, this value is sent to the license server, which verifies that it is valid and has not been used already. For digital software distribution these days, the key you're sent isn't even valid until after you buy the software, meaning that if you had guessed that key 10 minutes before you bought the software, it wouldn't have worked.

Or you can use hybrid approaches where much of the algorithm to verify through hashing or public key cryptography is resident on the system, but then there is also a step where the license server is checked to see if that key has been used before or if the key has been revoked.

### Other Suggestions

The methods introduced align with more of the industry best practices and the most commonly used methods. But there is not a one size fits all to security, and some of the following are techniques you could encounter in a cracking scenario, or you might find them useful in a defensive scenario if you have unique constraints.

#### *Prefer Offline Activation*

While the addition of online key servers sounds powerful from a security perspective, and it is, it's worth acknowledging that technique comes with a huge amount of manageability and infrastructure pain. Managing key servers is no small feat, and they become a beacon for cyberattacks. So, you will still often find that many companies aren't able or willing to bite off that level of chaos, so they will still favor going for stronger offline verification. Supporting offline key verification eliminates the complexities of managing a key server and is inclusive to users without Internet access.

#### *Perform Partial Key Verification*

In an offline mode, you have no method to perform revocation and have no way to make some keys no longer work. To prevent a single leaked key from working on all future versions of your software, check only some of the key. A simplistic example would be to check only the first character of each group in a license key such as the `X`, `9`, `B`, and `B` in `X4Z-951-B41-BR0`.

If someone releases a key generator for your application, release a new version that checks part of the remaining key. For example, switch to checking the second character of each group (`4`, `5`, `4`, and `R`). This limits the potential damage caused by a single key generator.

#### *Encode Useful Data in the Key*

Encoding useful data in the key can help to limit its applicability. For example, a key may specify the maximum version of the application that it applies to, limiting the impact of a compromised key.

## Key Generators

If a piece of software uses a key for activation, crackers will want to build a key generator for it. This is true regardless of which type of key activation you did. Key generators are then distributed for people to generate a “free” key for software.

You'll see later how to patch software to simply remove a key check, so for now focus on making a key generator, and assume you can't just bypass the key check. Key generators typically require a more in-depth analysis of the program and a deeper understanding of the key algorithm.

### Why Build Key Generators?

If key generators are more difficult to create, why bother building them? There are a few different reasons.

Software can have various defenses that can make patching the more difficult route, such as the following:

*   Tamper proofing

*   Dynamic checks

*   Anti-debugging

*   Software guards

Also, patching may require releasing a modified copy of the target software, which may be watermarked. Watermarking is a technique to trace a piece of software back to who originally purchased it. These watermarks can be used to trace a cracked piece of software back to the cracker, which is obviously something they don't want.

The software could implement online checks to look for patched/modified versions of programs. Alternatively, some software may decrypt itself based on the entered key (unpacking, which will be explored in [Chapter 13](#c13.xhtml), “Advanced Defensive Techniques”), and removing the key check entirely means it won't be able to decrypt.

Key generators are also more future-proof than patching. An application developer can't easily revoke valid keys.

Finally, crackers may choose key generators *because* they are harder. Patching in some cases is easy, while building a successful keygen is a challenge that carries a certain amount of prestige.

### The Philosophy of Key Generation

When cracking key checkers, it is useful to think of the key checker in the form of `f(u) == g(k)`, where:

*   *`u`* is the username entered by the user.

*   *`f`* is a transformation function on the username.

*   *`k`* is the key entered by the user.

*   *`g`* is a transformation function on the key.
