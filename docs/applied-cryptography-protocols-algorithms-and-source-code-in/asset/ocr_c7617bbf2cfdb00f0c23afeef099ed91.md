# 22.7 Conference Key Distribution and Secret Broadcasting

cube roots modulo $n$. A lot of the details are left out of the following protocol, and you get the idea.

+   (1) Alice chooses a random number, $r_A$, and sends Trent
$r_A^8 mod n$

+   (2) Trent tells Bob that someone wants to exchange a key with him.

+   (3) Bob chooses a random number, $r_B$, and sends Trent
$r_B^8 mod n$

+   (4) Trent uses his private key to recover $r_A$ and $r_B$. He sends Alice
$r_A \oplus r_B$

+   (5) Alice calculates
$[r_A \oplus r_B] \oplus r_A = r_B$

She uses $r_B$ to communicate securely with Bob.

This protocol looks good, but it has a horrible flaw. Carol can listen on step [3] and use that information, with the help of an unsuspecting Trent and another malicious user [Dave], to recover $r_B$ [1472].

+   (1) Carol chooses a random number, $r_C$, and sends Trent
$r_B \oplus r_C^3 mod n$

+   (2) Trent tells Dave that someone wants to exchange a key with him.

+   (3) Dave chooses a random number, $r_D$, and sends Trent
$r_D^3 mod n$

+   (4) Trent uses his private key to recover $r_C$ and $r_D$. He sends Carol
$[r_B \oplus r_C] mod n \oplus r_D$

+   (5) Dave sends $r_D$ to Carol.

+   (6) Carol uses $r_C$ and $r_D$ to recover $r_B$. She uses $r_B$ to eavesdrop on Alice and Bob.

This is not good.