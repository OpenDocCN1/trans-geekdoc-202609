# CHAPTER 16 Pseudo-Random-Sequence Generators

This algorithm looks pretty impressive, but I doubt it is. The NSA allows export, so there must be some attack on the order of $2^{40}$ or less. What is it?

# 16.7 Nanoteq

Nanoteq is a South African electronics company. This is their algorithm that has been fielded by the South African police to encrypt their fax transmissions, and presumably sumably for others uses.

The algorithm is designed, more or less, in [902,903]. It uses a 127-bit LFSR with a fixed feedback polynomial, the key is the initial state of the feedback register. The 127 bits of register are reduced to a single keystream by 25 primitive cells. Each cell has five inputs and one output:

```
$f(X_1,X_2,X_3,X_4,X_5) = X_1 + X_3 \oplus [X_2 + X_4] \oplus [X_2 + X_5] \oplus [X_1 + X_4 \oplus X_5]$
```

Each input is XORed with some bit of the key. There is also a secret permutation that depends on the particular implementation, and is detailed in the papers. This algorithm is only available in hardware.

Is this algorithm secure? I doubt it. During the transition to majority rule, harassing faxes from one police station to another would sometimes turn up in liberal newspapers. U.S., U.K., or Soviet intelligence efforts. Ross Anderson took some initial steps towards cryptanalizing this algorithm in [46]; I expect more to come soon.

# 16.8 Rambutan

Rambutan is a British algorithm, designed by the Communications Electronics Security Group (one of the aliases used by GCHQ). It is only sold as a hardware module and is approved for the protection of classified material up to "Confidential." The algorithm itself, and the chip are not generally commercially available.

Rambutan has a 112-bit key [parity bits] and can operate in three modes: ECB, CBC, and 8-bit CFB. This strongly indicates that it is a block algorithm, but rumors place elsewhere. So, it is a LFSR shift register. Each one of different length around 80 bits. The feedback polynomials are fairly sparse, with only about 10 taps each. Each shift register provides four inputs to a large and complex nonlinear function that eventually spits out a bit.

Why call Rambutan? Perhaps, like the fruit, it's spiny and forbidding on the outset soft and yielding inside. On the other hand, maybe that's not the reason.

# 16.9 Additive Generators

Additive generators (sometimes called Fibonacci generators) are extremely efficient because they produce random words instead of random bits [863]. They are not secure on their own, but can be used as building blocks for secure generators.