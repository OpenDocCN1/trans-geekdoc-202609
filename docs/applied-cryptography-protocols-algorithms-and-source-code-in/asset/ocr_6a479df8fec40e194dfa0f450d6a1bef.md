# 23.3 Subliminal Channel

information necessary to reconstruct the secret. Only when the two delega- share their equations can be multiplied to reconstruct the secret.

In general, any type of sharing scheme that can be imagined is implemented. All you have to do is envision a system of equations that corresponds to the par- particular scheme. Some excellent papers on generalized secret-sharing schemes are [1462,1463,1464].

# Sharing a Secret with Cheaters

This algorithm modifies the [m, n]-threshold scheme to detect cheaters [1529]. I demonstrate this using the Lagrange scheme, although it works with the others as well.

Choose a prime, $p$, that is both larger than $n$ and larger than

```
$s - 1|m - 1|/e + m$
```

where $s$ is the largest possible secret and $e$ is the probability of successful cheating. You can make $e$ as small as you want, it just makes the computation more complex. Construct your shadows as before, except of using 1, 2, 3, $\dots, n$ for $x_u$, choose random numbers between 1 and $p$ for $x_v$.

Now, when Mallory sneaks into the secret reconstruction meeting with his false secret, share has a high probability of not being possible. An impossible secret is, of course, a fake secret. See [1529] for the math.

Unfortunately, when Mallory is exposed as a cheater, he still learns the secret (assuming that there are $m$ other value shards). Another protocol, from [1529,975], prevents that. The basic idea is to have a series of $k$ secrets, such that none of the participants knows beforehand which is secret. Each secret is larger than the one before, except for the secret. The participants combine their shadows to generate- one after the other, until they create a secret that is less than the previous secret. That's the correct one.

This scheme will expose cheaters early, before the secret is generated. There are complications when the participants deliver their shadows one at a time; refer to the papers for details. Other papers on the detection and prevention of cheaters in threshold schemes are [355,114,270].

# 23.3 SUBLIMINAL CHANNEL

This subliminal channel (see Section 4.2), designed by Gustavus Simmons [1458,1459,1460], uses the Schnorr-Shamir identification scheme (see Section 20.5). In the original scheme, the sender (Alice) chooses a public modulus, $n$, and a private key, $k$, such that $n$ and $k$ are relatively prime. Unlike the original scheme, $k$ is shared between Alice and Bob, the recipient of the subliminal message.

The public key is calculated:

```
$h = -k^2 \mod n$
```