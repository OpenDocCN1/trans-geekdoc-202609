# 12.4 Differential and Linear Cryptanalysis

# 285

On the other hand, this report also warned:

... the problem [of the search for structure in the S-boxes] is complicated by the ability of the human mind find apparent structure in random data, which is really not structure at all.

At the second round on DES, the National Security Agency revealed several design criteria behind the S-boxes [229]. This did nothing to quell people's suspicions, and the debate continued [228,422,714,1506,1551].

Various odds about the S-boxes appeared in the literature. The last three bits of the fourth S-box can be derived in the same way as the first by complementing some of the input bits [436,438]. Two different, carefully chosen inputs to S-boxes produce the same output [436]. It is possible to obtain the same output of a single DES round by changing bits in one three neighboring S-boxes [487]. Shamir noticed that the S-boxes entries appear to be somewhat unbalanced, wasn't to turn into an attack [1423]. He mentioned a feature of the fifth S-box, but it took another eight years before linear cryptanalysis exploited that.) Other researchers showed that publicly design principles could be used with S-boxes with the observed characteristics [266].

# Additional Results

There were other attempts to analyze DES. One cryptographer looked at randomness on spectral tests [559]. Others analyzed sequences of linear factors, their attack failed after eight rounds [1297,336,531]. A 1987 unpublished attack by Donald Davies exploited the expansion permutation repeats bits into adjacent S-boxes, this attack is also impractical after eight rounds [172,429].

# 12.4 DIFFERENTIAL AND LINEAR CRYPTANALYSIS

# Differential Cryptanalysis

In 1990, Eli Biham and Adi Shamir introduced differential cryptanalysis [167,168, 171,172]. This is a new method of cryptanalysis, heretofore unknown to the public. Using this method, Biham and Shamir found a chosen-plaintext attack against DES that was more effective than brute force.

Differential cryptanalysis looks specifically at ciphertext pairs: pairs of ciphertexts whose plaintext have particular differences. It analyzes the evolution of these differences as the plaintexts propagate through DES when they are encrypted with the same key.

Simply, choose pairs of plaintexts with a fixed difference. The two plaintexts can be chosen at random, as long as they satisfy particular difference conditions; the cryptanalyst does not even have to know their values.(For DES, the term “difference” is defined using XOR. This can be different for different algorithms.) Then using the differences in the resulting ciphertexts, assign different probabilities to