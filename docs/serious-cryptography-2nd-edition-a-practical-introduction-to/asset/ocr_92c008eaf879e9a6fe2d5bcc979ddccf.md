E(K, P) = C. But in practice, even with testing 100 billion keys per second, it would take more than 100,000,000,000,000,000,000 years. In other words, reasonably speaking, this cipher is computationally secure because it's practically impossible to break.

We can express computational security in terms of two values:

+   - t, which is a limit on the number of operations that an attacker will carry out
+   - ε (epsilon), which is a limit on the probability of success of an attack

We then say that a cryptographic scheme is (t, ε)-secure if an attacker performing at most t operations—whatever those operations are—has a probability of success that is no higher than ε, where ε is at least 0 and at most 1. Computational security gives a limit on how hard it is to break a cryptographic algorithm.

Recognize that t and ε are just limits: if a cipher is (t, ε)-secure, then no attacker performing fewer than t operations will succeed (with probability ε). However, this doesn't imply that an attacker doing exactly t operations will succeed, and it doesn't provide the necessary number of operations, which may be much larger than t. We say that t is a lower bound on the necessary computation effort because you'd need at least t operations to compromise security.

If we do know precisely how much effort it takes to break a cipher, we say that (t, ε)-security gives us a tight bound when an attack exists that breaks the cipher with probability ε and exactly t operations.

For example, consider a symmetric cipher with a 128-bit key. Ideally, this cipher should be (t, t/2^128)-secure for any value of t between 1 and 2^128. The best attack should be brute force (trying all keys until you find the correct one). Any better attack would have to exploit some imperfection in the cipher, so we strive to create ciphers where brute force is the best possible attack.

Given the statement (t, t/2^128)-secure, let's examine the probability of success of three possible attacks:

+   - In the first case, t = 1, an attacker tries one key and succeeds with a probability of ε = 1/2^128.
+   - In the second case, t = 2^128, an attacker tries all 2^128 keys, and one succeeds. Thus, the probability ε = 1. (If the attacker tries all keys, the right one must be among them.)
+   - In the third case, an attacker tries only t = 2^64 keys and succeeds with a probability of ε = 2^64 / 2^128 = 2^-64. When an attacker tries only a fraction of all keys, the success probability is proportional to the number of keys tried.

We can conclude that a cipher with a key of n bits is at best (t, t/2^n)-secure, for any t between 1 and 2^n, because no matter how strong the cipher, a brute-force attack against it will always succeed. The key thus needs to be long enough to blunt brute-force attacks in practice.