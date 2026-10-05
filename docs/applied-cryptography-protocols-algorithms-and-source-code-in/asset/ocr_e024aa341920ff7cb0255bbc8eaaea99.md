CA-1.1 is patented [678], but is available free for non-commercial use. Anyone interested in either licensing the algorithm or in the cryptanalysis prize should consider Howard Gutowitz, ESPCI, Laboratoire d'Electronique, 10 rue Vauquelin, 75005 Paris, France.

# 13.12 SKIPJACK

Skipjack is the NSA-developed encryption algorithm for the Clipper and Capstone chips [Sections 24.16 and 24.17]. Since the algorithm is classified Secret, its details have never been published. It will only be implemented in tamperproof hardware.

The algorithm is classified Secret, not because that enhances its security, but because the NSA doesn't want Skipjack being used without the Clipper key-escrow mechanism. They don't want the algorithm implemented in software and spread around the world.

Is Skipjack secure? If the NSA wants to produce a secure algorithm, they presumably can. On the other hand, if the NSA wants to design an algorithm with a trapdoor, they can do that well.

Here's what has been published [115462].

+   - It's an iterative cipher.
- The block size is 64 bits.
- It has an 80-bit key.
- It can be used in ECB, CBC, OFB, or 1-, 8-, 16-, 32- or 64-bit CFB modes.
- There are 32 rounds of processing per single entry or decrypt operation.
- NSA started the design in 1985 and completed the evaluation in 1990.

The documentation for the Mykotron Clipper chips shows that the latency for the Skipjack algorithm is 64 clock cycles. This means each round consists of two clock cycles: presumably one for the S-box substitution and another for the XOR at the end. [Remember, permutations take no time in hardware.] The Mykotron documentation calls this two-clock-cycle operation a "G-box," and the whole thing a "shift." [Some part of the G-box is called an "F-table," probably a table of constants by many functions.]

I heard a rumor that Skipjack uses 16 S-boxes, and that the total memory requirement for the S-boxes is 128 bytes. It is unlikely that both of these rumors are true.

Another rumor implies that Skipjack's, unlike DES's, do not operate on half of the block size. This, combined with the notion of "shifts," an inadvertent statement made at Crypto '94 that Skipjack has a "48-bit internal structure," implies that it is similar in design to SHA (see Section 18.7) but with four sub-bit blocks: three sub-blocks go through a key-dependent one-way function to produce