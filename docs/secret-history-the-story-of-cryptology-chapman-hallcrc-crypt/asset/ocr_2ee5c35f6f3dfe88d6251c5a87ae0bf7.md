A B C D E F G H I J K L M N O P Q R S T U V W X Y Z plaintext
D E F G H I J K L M N O P Q R S T U V W X Y Z A B C ciphertext
For example,
ET TU BRUTE? message
becomes
HW WX EUXWH? ciphertext

(Note: These were not Caesar’s last words. They are the last words of Caesar in Shakespeare’s play, which is not completely historically accurate.)

We don’t have to shift by three. We could shift by some other integer value K. If we think in terms of the numbers 0 through 25 representing the letters A through Z, the enciphering process may be viewed mathematically as C = M + K (mod 26), where C is the ciphertext letter, M is the plaintext letter, and K is the key. The “mod 26” part (short for “modulo 26”) simply means that if the sum M + K is greater than or equal to 26, we subtract 26 from this number to get our result. The keyspace (defined as the set of possible choices for K) has 25 elements, because the identity, K = 0, leaves the message unchanged, as does K = 26. Only values strictly between 0 and 26 offer distinct encipherments. For those of you who have had a semester of abstract algebra, we are now working with elements from the group Z26. Just as Brutus helped kill Caesar, a brute force attack (trying all possible keys) quickly destroys his cipher. One requirement for a strong cryptosystem is a big keyspace.

Perhaps in an act of rebellion against more modern ciphers, during the U.S. Civil War, General Albert S. Johnston (fighting for the Confederacy), agreed with his second in command, General Pierre Beauregard, to use a Caesar shift cipher!

# 1.6 Other MASC Systems

The substitutions made by a MASC needn’t be obtained by a shift. Examples where the substitutions are random appear in many newspapers alongside the comics and are very easy to break despite having a keyspace of 26! elements. So, although a large keyspace is a necessary condition for security, it is not sufficient.

Note: n! is read as “n factorial” and is used to indicate the product of the integers 1 through n; for example, 4! = 1 · 2 · 3 · 4 = 24. Christian Kramp introduced the! notation in 1808 because n! grows surprisingly fast for small values of n. It was not, as comedian Steven Wright claimed, an attempt to make mathematics look exciting. An arbitrary MASC can make use of any of 26 possible letters to represent A and any of the remaining 25 letters to represent B, and so on, until only 1 choice is left to represent Z, so the size of the keyspace is 26! = 403,291,461,126,605,635,584,000,000. Try double-checking this with your calculator! Alternatively, type 26! into Mathematica or Maple or another computer algebra system. Do you get all of the digits?

Stirling’s formula provides a handy approximation of n! for large n:

n! ~ (√2πn)(nⁿ)(e⁻ⁿ)