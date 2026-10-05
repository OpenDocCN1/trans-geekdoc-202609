# 1.2 Steganography

+   1. Data complexity. The amount of data needed as input to the attack.
2. Processing complexity. The time needed to perform the attack. This is often called the work factor.
3. Storage requirements. The amount of memory needed to do the attack.

As a rule of thumb, the complexity of an attack is taken to be the minimum of these three factors. Some attacks involve trading off the three complexities: a faster attack might be at the expense of a greater storage requirement.

Complexities are expressed as orders of magnitude. If an algorithm has a complexity of $2^{28}$, $2^{28}$ operations are required to break the algorithm. (These operations may interact with each other time-consuming). Still, if you assume that you have enough computing speed to perform a million operations every second and set a million parallel processors against the task, it will still take over $10^{19}$ years to recover the key.

While the complexity of an attack is constant (until some cryptanalyst finds a better attack, of course), computing power is anything. There have been advances in computing power during the last half-century and there is no reason to think this won't continue. Many cryptanalytic attacks are perfect for parallel machines: The task can be broken down into billions of tiny pieces and none of the processors need to interact with each other. Pronouncing an algorithm secure simply because it is infeasible to break, given current technology, is dice at best. Good cryptystems are designed to be infeasible with the computing power that is expected to evolve many years in the future.

# Historical Terms

Historically, a code refers to a cryptystem that uses linguistic units: words, phrases, sentences, and so on. For example, the word "OCELOT" might be the ciphertext for the entire phrase "TURN LEFT 90 DEGREES," the word "LOLLIPOP" might be the ciphertext for the phrase "TURN RIGHT 90 DEGREES," and the words "BENT ARM" might be the ciphertext for "HOWITZ." Codes of this type are not discussed in this book; see [794,795]. Codes are only useful for specialized circumstances. Codes are useful for any circumstance. If your code has no entry for "ANTEATERS," then you can't say it. You can say anything with a cipher.

# 1.2 STEGANOGRAPHY

Steganography serves to hide secret messages in other messages, such that the secret's very is concealed. Generally the sender writes an innocuous message and then conceals a secret message on the same piece of paper. Historical tricks include invisible inks, tiny pin punctures on selected characters, minute differences between handwritten characters, pencil marks on typewritten characters, grilles which cover most of the message except for a few characters, and so on.