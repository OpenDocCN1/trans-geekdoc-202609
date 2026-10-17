
`CRYSTALS`（Cryptographic Suite for Algebraic Lattices）包含两种基于格的密码原语：`Kyber`，一种 CCA 安全的 KEM，以及 `Dilithium`，一种强 EUF-CMA 安全的数字签名算法。`CRYSTALS-Kyber` 基于更早的 MLWE 基于加密问题，但使用方形而非矩形矩阵作为公钥，并使用多项式环（`https://en.wikipedia.org/wiki/Polynomial_ring`）而非整数。它性能良好，并且在需要更大密钥大小时可以轻松扩展。

根据其多国开发团队的说法，`Kyber-512` 的安全保护大致相当于 AES-128（NIST 安全等级分类 1），`Kyber-768` 的安全大致相当于 AES-192（NIST 安全等级分类 3），而 `Kyber-1024` 的安全大致相当于 AES-256（NIST 安全等级分类 5）。对于 NIST 所需安全实现第二轮开始阶段，密钥大小范围为 1,632 至 3,168 字节，公钥大小范围为 800 至 1,568 字节，密文大小范围为 736 至 1,568 字节。`CRYSTAL-Kyber` 一直在密钥大小方面排名中等至较小。它是 Open Quantum Safe 项目的一部分。

有关 `CRYSTALS` 的更多信息，请参阅 `https://pq-crystals.org/` 和 `https://pq-crystals.org/kyber/index.shtml`。

### FrodoKEM

`FrodoKEM` 是一种 CCA 安全和 CPA 安全的基于格的密码系统，其保护依赖于求解 LWE 问题。与其他基于格的模型（基于 LWE 环）相比，它具有稍大的密钥大小和较慢的性能。它有三种密钥大小：

* `FrodoKEM-640`，据称具有相当于 AES-128 的安全性
* `FrodoKEM-976`，据称具有相当于 AES-192 的安全性
* `FrodoKEM-1344`，据称具有相当于 AES-256 的安全性

对于 NIST 所需安全实现第二轮开始阶段，密钥大小范围为 19,888 至 43,088 字节，公钥大小范围为 9,616 至 21,520 字节，密文大小范围为 9,720 至 21,632 字节。`FrodoKEM` 属于公钥和密文大小最大的行列之一。

`FrodoKEM` 团队有许多成员来自 Microsoft 和 Google。成员们采用了 `FrodoCCS` 的早期版本，这是一种临时密钥交换方案，并对其进行了改进以制作 IND-CCA-KEM。`FrodoKEM` 是一个更简单的版本，涉及的代码更少。这使其更可能更可靠且对攻击更具弹性。如果发现缺陷，可能也更容易修复。它是 Open Quantum Safe 项目的一部分。

Current FrodoKEM is also “constant-time” as built. It does not need to be reoptimized security-wise to prevent certain types of eavesdropping attacks. `Constant-time` is a cryptographic protection property designed to mitigate many types of side-channel `timing attacks`. In short, due to a variety of reasons, many ciphers and many early implementations of ciphers introduce CPU delays directly related to what the cipher is involved with (say, evaluating a cipher key). Any cipher process that changes processing time in relationship to the length of some examined variable can possibly create a measurable and predictable timing difference and give an attacker knowledgeable insight to otherwise secret information. This information might allow attackers to make assumptions to quicken their attack. In the cryptography world, these types of gained information are called `cribs`. You'll find a great basic discussion on timing side-channel attacks here: `www.chosenplaintext.ca/articles/beginners-guide-constant-time-cryptography.html`.

For more information on FrodoKEM, see `https://frodokem.org/`.

> `NOTE`  Joppe W. Bos, a cryptographic researcher at NXP Semiconductors, Leuven, Belgium, is a submitter of three post-quantum ciphers: FrodoKEM, CRYSTALS-Kyber, and NewHope.

### HQC

QC (Hamming Quasi-Cyclic) is a code-based public key encryption scheme based on the difficulty of decoding random quasi-cyclic codes, which uses Bose–Chaudhuri–Hocquenghem (BCH) codes with a repetition code. BCH codes were invented in 1959 and 1960, and it's considered simple to control what “errors” they correct, thus making it easy to decode when you have the correct keys. BCH codes have been widely used in CDs, DVDs, barcoding, and computer storage devices for decades. Even though HQC uses “easy-to-decode” BCH codes, it is subject to “nonzero” (but still incredibly rare) decryption failures.

HQC has a 2^(–128) chance that any particular decryption round will not result in the original plaintext content. Computers, in general, have many other far more common errors that have a much higher chance of happening, and we accept using those computers just fine. A failure would mean it could take additional decryption rounds to be successful, but those additional rounds would happen very quickly and almost no one would notice. But the probability is nonzero, and so it's noted. Cryptographers are held to exacting reporting standards.

HQC has a secret key size of 40 bytes for all NIST required security implementations (which is tied for second smallest with three other submissions). For the beginning of Round 2 for the NIST required security implementations, HQC's public keys range from 3,125 to 8,897 bytes, with ciphertexts ranging from 6,234 to 17,777 bytes. Like BIKE, HQC has markers that can be used to identify HQC-encrypted traffic, and it uses ephemeral keys to allow perfect forward secrecy. The HQC team is multinational in its makeup, and many of them have submitted other algorithms to the NIST contest (for example, Frenchman Philippe Gaborit also worked on BIKE, HQC, RQC, and ROLLO).

For more information on HQC, see `https://pqc-hqc.org`.

### LAC

The CPA- and CCA-secure LAC (Lattice-based Cryptosystems) cipher includes four different LAC-related primitives based on polynomial learning with errors (poly-LWE) problems over the ring. The LAC cipher primitives are

* `LAC.CPA`: A secure public key encryption scheme, which is the foundation for the other three implementations as well
* `LAC.KE`: A secure key exchange protocol that is directly converted from `LAC.CPA`
* `LAC.CCA`: A secure key encapsulation mechanism, which is related to `LAC.CPA`
* `LAC.AKE`: An authenticated key exchange protocol

LAC can run on both Intel and ARM processors (as do most of the other competitors), uses relatively smaller keys, and has good performance. For the beginning of Round 2 for the NIST required security implementations, secret key sizes range from 512 to 1,204 bytes, public key sizes range from 544 to 1,056 bytes, and ciphertexts range from 712 to 1,424 bytes. This gives LAC the fourth smallest combined key and ciphertext sizes of the NIST competitors.

There does seem to be a higher-than-average number of questions from NIST contest reviewers regarding LAC’s security, including this comment: (`https://csrc.nist.gov/CSRC/media/Projects/Post-Quantum-Cryptography/documents/round-1/official-comments/LAC-official-comment.pdf`), but so far none of them are claiming a significant break.

The LAC team is made up of Chinese cryptographers. Chinese cryptographers are involved in many quantum-resistant algorithms and submissions to NIST. This makes sense, because China is a leader in research on quantum computers, devices, quantum-based cryptography, and defenses.

For more information on LAC, download `https://csrc.nist.gov/CSRC/media/Projects/Post-Quantum-Cryptography/documents/round-1/submissions/LAC.zip`. The LAC team doesn't have a public-facing website, but this zip file has a lot of relevant information.

### LEDAcrypt

LEDAcrypt (Low-dEnsity parity-check coDe-bAsed cryptographic systems) is an asymmetric cipher relying on Quasi-Cyclic Low Density Parity Check (QC-LDPC) codes and ephemeral keys. It was created by a merger of LEDAkem/LEDApkc from the First Round, along with many improvements stemming from NIST suggestions.

LEDAcrypt is a modified version of the Niederreiter cryptosystem. QC-LDPC codes allow high-speed decoding and smaller key pairs. For the beginning of Round 2 for the NIST required security implementations, private key sizes range from 452 to 1,092 bytes, public key sizes range from 1,872 to 8,520 bytes, and ciphertexts range from 1,872 to 4,616 bytes. LEDAcrypt can allow perfect forward secrecy and uses SHA-3 (256 to 512 bits) for its hashing functions but, like many other code-based schemes, is susceptible to decryption failures. The LEDAcrypt team is Italy-based.

For more information on LEDAcrypt, see `www.ledacrypt.org`.

### NewHope

NewHope is a CCA- and CPA-secure lattice-based key-exchange method based on the ring-learning-with-errors (ring-LWE) problem. It has four instantiations:

* `NewHope512-CPA-KEM`
* `NewHope1024-CPA-KEM`
* `NewHope512-CCA-KEM`
* `NewHope1024-CCA-KEM`
