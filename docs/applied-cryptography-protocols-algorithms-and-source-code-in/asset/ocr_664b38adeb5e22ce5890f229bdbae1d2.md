# 14.10 Theory of Block Cipher Design

tiels seek to apply only to rulers with a small number of rounds, but partial differentials combine nicely with differentials.

Linear cryptanalysis is newer, and is still being improved. Notions of key ranking [1019] and multiple approximations [811,812] have been defined. Other work that extends the scale of linear cryptanalysis can be found in [1270]; [938] tries to combine linear and differential cryptanalysis into one attack. It is unclear what design techniques will protect against these sorts of attacks.

Knudsen has some progress, considering some necessary [but perhaps not sufficient] criteria for what he calls secure Feistel networks: ciphers that resist both linear and differential cryptanalysis [857]. Nyberg introduced linear cryptanalysis an analogy to the concept of differentials from differential cryptanalysis [1180].

Interestingly, there seems to be a duality between differential and linear cryptanalysis. This duality appears both in the design of techniques to construct good differential characteristics and linear approximations [164,1018], and also in the criteria for making algorithms that are secure against attacks [307]. Exactly where this line of research will lead is still unknown. As a start, Daemen has developed an algorithm-design strategy based on linear and differential cryptanalysis [402].

# S-Box Design

The strength of various Feistel networks—and specifically their resistance to differential and linear cryptanalysis—is tied directly to their S-boxes. This prompted a spate of research on what constitutes a good S-box.

An S-box is a mapping of $m$-bit inputs to $n$-bit outputs. Previously I talked about one large lookup table of 64-bit inputs to 64-bit outputs, which would be a $64\times64$ S-box. An S-box with $m$-bit input and $n$-bit output is called a $m\times n$ bit-box. S-boxes are generally the only nonlinear step in an algorithm; they are what give block cipher its security. In the general, they are the better,

DES has eight $6\times4$ S-boxes. Khufre and Khafre have a single $8\times32$ S-box, LOKI has a $12\times8$ S-box, and Blowfish and CAST have $8\times32$ S-boxes. In IDEA the modular multiplication strategy is effectively the S-box; it is a $16\times16$ S-box. The larger the S-box, the harder is it to find useful statistics to attack using using either differential or linear cryptanalysis [653,729,1626]. While random S-boxes are generally not optimal to protect against differential and linear attacks, it is easier to find strong S-boxes that are larger. Most S-boxes are nonlinear, nondegenerate, and have strong resistance to linear cryptanalysis—the fraction that does not go as rapidly as the number of bits decreases [1185,118,187].

The size of $m$ is more important than the size of $n$. Increasing the $n$ reduces the effectiveness of differential cryptanalysis, but greatly increases the effectiveness of linear cryptanalysis. In fact, if $n \geq 2^m - m$, then there is definitely a linear relation of the input and output bits of the S-box. If $n \geq 2^m$, then there is a linear relation of only the output bits [164].