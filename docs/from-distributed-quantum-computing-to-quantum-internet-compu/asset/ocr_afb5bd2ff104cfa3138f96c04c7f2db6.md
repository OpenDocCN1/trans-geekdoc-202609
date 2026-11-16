![](bbox=[0.135, 0.108, 0.865, 0.458])

**Figure 3.3** A solution to the coin flipping protocol without a trusted mediator, but has a problem. Note that before this protocol starts, A and B each has chosen their sides, and then the protocol starts to decide who wins.

compute \( a \oplus b \). Both A and B now has the result. This protocol is illustrated in Figure 3.3.

But what is the problem? Note that A knows the outcome \( b \) before B gets A’s key. Is there a way for A, now knowing B’s outcome, to manipulate its encrypted outcome \( E_{k_a}(a) \)? It seems the answer is “yes”; if A makes use of a colliding triple, where a colliding triple \( (m, k_0, k_1) \) has the property that \( D_{k_0}(m) = 0 \) and \( D_{k_1}(m) = 1 \), that is, the same message m can be decrypted in two different ways, with two different keys, to get either 0 or 1. So, for example, A, knowing b, can force a favorable outcome by giving B either \( k_0 \) or \( k_1 \) so that B decrypts \( E_{k_a}(a) \) to 0 or 1!

An example of such a colliding triple is \( (m, m \oplus 0, m \oplus 1) \), with the decryption function: \( D_k(m) = m \oplus k \). Using such a colliding triple, A sends the encrypted message \( m = E_{k_a}(a) \) to B, and then if A wants m to decrypt to 0, A sends the key \( m \oplus 0 \), so that B decrypts m as follows: \( D_{m \oplus 0}(m) = m \oplus (m \oplus 0) = 0 \), and if A wants m to decrypt to 1, then A sends the key \( m \oplus 1 \), so that B decrypts m as follows: \( D_{m \oplus 1}(m) = m \oplus (m \oplus 1) = 1 \). So, A can choose whatever outcome it wants by sending the corresponding key to B! How can this be resolved?

One way to resolve this issue is for B to also play a role in choosing the key since A would not now be able to choose keys from a colliding triple. So, now instead of