
This implies that the plaintext space X and cipher-space Y will be equal, that is, Set X = Set Y. In fact, the Plaintext Space and Cipher-text are exactly the same, as illustrated in Figure 6.8.

## Plaintext Space X
## Cipher-text Space Y

```
C = E_K[P]
P = D_K[C]
```

FIGURE 6.8 Plaintext space X and cipher-text space Y are equal.

Now, let us consider the scenario when a given Plaintext P is encrypted using different keys:

- DES Key Size = 56 bits
- Size of DES Key Space = 2^56
- Consider encryption of a given plaintext P using all possible keys in the Key Space. This will result in a set of cipher-text Y_1, which will be a subset of Y.
- The set Y will have a size = |Y_1| <= 2^56, since two different keys may map the plaintext P to the same cipher-text C, as illustrated in Figure 6.9.

## Plaintext Space X
## Cipher-text Space Y

![](img/d3b56042c756fbcc011ff06f1b9f53f0_264_0.png)

FIGURE 6.9 Plaintext P is encrypted using different keys.

## 6.6.1 Strength of DES

Key Size: With a 56-bit Key Size, there would be 2^56 possible keys. In a brute force attack, an adversary will have to try an average of 2^55 keys to meet success.

**Algorithm and S-Boxes:** The Strength of DES lies basically in the design of S-boxes. The design criteria of S-boxes have never been made public, and no fatal weaknesses have so far been reported in their design.

**Resistance to Timing Attacks:** Timing attacks exploit the fact that Encryption or Decryption Algorithms take a slightly different amount of time on different inputs. The algorithm for timing attacks yields the Hamming Weight (i.e., number of bits equal to 1) of the Secret Key. DES is fairly resistant to such attacks.

In 1998, DES encryption was broken in less than three days, using a special “DES Cracker” machine. Thus, a simple DES with a 56-bit key is virtually useless.

## 6.6.2 Possible Attacks on DES

DES is claimed to be prone to the following types of Cryptanalysis attacks:

- Differential Cryptanalysis
- Linear Cryptanalysis

### 6.6.2.1 Differential Cryptanalysis

- A Differential Cryptanalysis Attack is an “Adaptively Chosen Plaintext,” wherein the attacker has access to encryption equipment.
- The attacker analyzes the effect of particular differences in plaintext pairs on the differences in resulting-text.
- The attacker chooses plaintext pairs with a particular XOR difference (say Δm). The chosen plaintext pairs are made to pass through the encryption and their XOR differences are observed at the output of each round.
- It will be observed that certain XOR differences in the plaintext pairs have a high probability of causing certain XOR differences in the corresponding cipher-text. Such pairs are of interest to the analysts.
- The transformation of XOR difference at the output of successive rounds is a function of the sub-keys of those rounds. This information is used to predict the sub-keys. This attack requires chosen plaintexts of the order of $2^{47}$ to break the cipher.

To understand the approach more clearly, we can do the following:

- Consider a plaintext pair $(m, m')$
- XOR difference between $m$ and $m'$ equal to $\Delta m = m \oplus m'$
- Let $\Delta m$ be split into two halves $\Delta m_0$ and $\Delta m_1$, such that $\Delta m = \Delta m_0 \oplus \Delta m_1$
- The plaintexts are passed through various rounds of the encryption algorithm, and their XOR differences are observed at the outputs of various rounds.

![](img/d3b56042c756fbcc011ff06f1b9f53f0_266_0.png)

FIGURE 6.10 Schematic of transformation of XOR differences at the outputs of various rounds.

- XOR difference at the input of round 1 = $\Delta m_0 \oplus \Delta m_1$
- XOR difference at the output of round 1 = $\Delta m_1 \oplus \Delta m_2$
- where $\Delta m_2 = \Delta m_0 \oplus F(\Delta m_0, K_1)$
- Thus, Round 1 transforms the XOR difference from $\Delta m_0 \oplus \Delta m_1$ to $\Delta m_1 \oplus \Delta m_2$
- Only one half of the input gets transformed as function of sub-key $K_1$ and the other half remains unchanged.
- The XOR difference at the output of Round 1 goes as input to Round 2.

For the transformation at round $i$ ($1 \le i \le 16$) we do the following:

- XOR difference at the input of round $i = \Delta m_{i-1} \oplus \Delta m_i$
- XOR difference at the output of round $i = \Delta m_{i} \oplus \Delta m_{i+1}$ where $\Delta m_{i+1} = \Delta m_{i-1} \oplus F(\Delta m_i, K_i)$
- Thus, Round $i$ transforms the XOR difference from $\Delta m_{i-1} \oplus \Delta m_i$ to $\Delta m_i \oplus \Delta m_{i+1}$
- The transformation at Round $i$ is a function of sub-key $K_i$
- The cryptanalyst will study the changes in XOR differences at the outputs of all rounds.
- Since these XOR changes are a function of the sub-keys used in the successive rounds, this information is used to assign probabilities to the sub-key bits.
- As we analyze more and more plaintext-cipher-text pairs, the most probable values of the sub-keys will emerge. Differential Cryptanalysis needs $2^{47}$ chosen plaintexts to break the cipher.

Finally, the Differential Cryptanalysis attack can be summarized as follows:

- The Differential Cryptanalysis Attack is an "Adaptively Chosen Plaintext Attack" wherein the attacker has access to encryption equipment.
- The attacker chooses certain plaintext pairs with a particular XOR difference (say $\Delta m$). The cryptanalyst encrypts those pairs using the same key (which is to be determined) and determines the XOR differences between the resulting cipher-texts. Let the XOR difference between the cipher-texts be $\Delta$.
- There will be certain XOR differences in the plaintext pairs that will result in particular XOR differences in the cipher-text pairs with a high probability. Such XOR differences are of interest to the analysts.
 The plaintext pairs with such XOR differences are made to go through encryption, and transformation of the XOR differences are noted at the outputs of successive rounds.
- This evolution of the XOR differences at the outputs of successive rounds of DES is a function of the sub-keys of those rounds; thus, the information is used to predict the bits of the sub-keys. Analysis of more and more plaintext pairs will enable prediction of the sub-keys completely.

## 6.6.2.2 Linear Cryptanalysis

This cryptanalysis is based on the finding that if we XOR some of the bits of plaintext and XOR some of the bits of corresponding cipher-text and then we have the XOR of the result of the two, then we get a bit that would form the XOR of some of the bits of the key.

- Consider an $n$-bit plaintext and $m$-bit key.
- Let the bits of a plaintext block be labeled as $p[1],p[2],...p[n]$; the bits of a cipher-text block be labeled as $c[1],c[2],...c[n]$; and the key bits be labeled as $k[1],k[2],...k[m]$
- Let us denote

$P[\alpha_1,\alpha_2,...,\alpha_a] = P[\alpha_1] \oplus P[\alpha_2] \oplus ... \oplus P[\alpha_a]$ where $1 \leq a \leq n$
$C[\beta_1,\beta_2,...,\beta_b] = C[\beta_1] \oplus C[\beta_2] \oplus ... \oplus C[\beta_b]$ where $1 \leq b \leq n$
$K[\gamma_1,\gamma_2,...,\gamma_c] = K[\gamma_1] \oplus K[\gamma_2] \oplus ... \oplus K[\gamma_c]$ where $1 \leq c \leq n$

- The goal of linear cryptanalysis is to determine linear equations of the form:

$P[\alpha_1,\alpha_2,...,\alpha_a] \oplus C[\beta_1,\beta_2,...,\beta_b] = K[\gamma_1,\gamma_2,...,\gamma_c]$

- If the result of the equation is 0 most of the time, we assume that $\gamma_1, \gamma_2, \dots, \gamma_e = 0$; if the result is 1 most of the time, then we assume that $\gamma_1, \gamma_2, \dots, \gamma_e = 1$

- By getting many such equations, we can deduce the bits of all sub-keys. For example, the cryptanalyst is able to establish the following: $K[3,17,23]=0$ and $K[3,23]=1$

From these equations, it can be deduced that bit-17 is likely to be 1.

- The number of known plaintexts required to break the cipher is of the order of $2^{43}$

## 6.7 MULTIPLE DES

The simplest form of multiple encryption/decryption has two encryption/decryption stages and two keys. Two blocks of DES with two 56-bit keys are used for encryption/decryption as follows:

### 6.7.1 Double DES

### 6.7.1.1 Encryption

Figure 6.11 illustrates the two blocks of DES with two 56-bit keys that are used for encryption.
