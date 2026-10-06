286

Blockchain

![](bbox=[0.5574, 0.1175, 0.8905, 0.2635])

FIGURE 15.8
Illustration of a hash function.

12 cycles/bytes needed for the stream generation. Its simplicity makes it vulnerable to several attacks. A large volume of flip-flop utilization in hardware is the weakness of this cipher.

# 15.6 Lightweight Hash Function

In a cryptographic environment, a hash function generates a fixed-size output from a random length input. Figure 15.8 shows that technique. A cryptographic hash function is used to check the integrity and authenticity of information by creating a message digest.
There are two main parts in a hash function. One is construction and another one is compression functions. The compression function is iterated by the construction function. To make a hash function ideal, it should follow the random oracle property. Although this property does not exist, a security criterion must be followed by a hash function technique.
The three main security properties of cryptographic hash function (h) with fixed output are:

+   - Collision-resistance: It is hard to find any two messages x1 and x2 for a hash function h, such that h(x1)=h(x2).
- Pre-image resistance: Reversing a hash function is computationally hard. It means it is difficult to find x from a hash value h(x).
- Second pre-image resistance: If a hash h produces hash value h hx1) as an output for input message x1, then it should be tough to find hash value h(x2) for any other input value x2 that h(x2)=h(x1).

# 15.6.1 PHOTON

A small hardware-based lightweight hash function PHOTON was designed by Guo et al. [7]. For internal key permutation, PHOTON includes an AES primitive and the sponge-like construction. Sponge construction framework uses for very small internal memory utilization. But the squeezing process of functions is very slow. Figure 15.9 displays the extended sponge framework. There it's this framework in such a way that it gives interesting trade-off. This compact hash function requires 1120 GE. It