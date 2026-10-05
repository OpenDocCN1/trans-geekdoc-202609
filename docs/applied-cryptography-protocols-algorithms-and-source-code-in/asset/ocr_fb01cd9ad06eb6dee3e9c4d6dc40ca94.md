# CHAPTER 12 Data Encryption Standard (DES)

# Table 12.15
Differential Cryptanalysis Attacks against DES Variants

| Modified Operation | Chosen Plaintexts |
| --- | --- |
| Full DES [no modification] | $2^{47}$ |
| P permutation | Cannot strengthen $2^{19}$ |
| Identity permutation | $2^{38}$ |
| Order of S-boxes | $2^{30}, 2^{31}$ |
| Replace XORs by additions | $2^{18}, 2^{20}$ |
| S-boxes: | $2^{33}$ |
| Random | $2^{26}$ |
| Random permutations | $2^{26}$ |
| One entry | $2^{44}$ |
| Uniform tables | |
| Elimination of the E Expansion | |
| Order of E and subkey XOR | 6, 16 |
| GDES (width q=8): | $2^{49}$ (independent key)

RDES-1, there is a data-dependent swap of the 16-bit words at the beginning of each round. In RDES-2, there is a data-dependent swap of the bytes at the beginning of each round after the 16-bit swapping as in RDES-1. And so on through RDES-4. RDES-1 is secure against both differential cryptanalysis [815] and linear cryptanalysis [1163]. Preschool RDES-2 and greater are as well.

# **s**DES**

A group of researchers led by Kwang Kim, has attempted to find a way to secure against both linear and differential cryptanalysis. Their first attempt, known as $s$DES, was presented in [834] and shown to be better than DES against differential cryptanalysis [855, 858]. Their next attempt, $s$DES, was presented in [839] and shown to be better than DES against linear cryptanalysis [856, 1491, 1527, 858, 838]. Biham suggested a minor change to make $s$s$DES secure against both linear and differential cryptanalysis [165]. The group went back to their computers and developed better techniques for S-box design [835, 837]. They proposed $s$DES [836] and then $s$DES [838, 944].

Table 12.16 uses $s$S-Boxes with S-box 1 and S-box 2 reversed, which are secure against both differential and linear cryptanalysis. Sticking this variant in a triple-DES mix is used to isolate cryptanalysis.

# **DES with Key-Dependent S-Boxes**

Linear and differential cryptanalysis work only if the analyst knows the composition of the S-boxes. If they are key-dependent and chosen by aographically strong method, then linear and differential cryptanalysis are much more difficult. However, randomly generated S-boxes have very poor differential and linear characteristics, even if they are secret.